When we organize a reusable logic on a custom file, we are creating a custom hook

For example, a custom hook to fetch data:

Create a file in the "src" folder and name it "useFetch.js". Custom hooks need to start with "use" or this will not work

useFetch.js
```
import { useState, useEffect } from 'react';

const useFetch = (url) => {
  const [data, setData] = useState(null);
  const [isPending, setIsPending] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    setTimeout(() => {
      fetch(url)
      .then(res => {
        if (!res.ok) { // error coming back from server
          throw Error('could not fetch the data for that resource');
        } 
        return res.json();
      })
      .then(data => {
        setIsPending(false);
        setData(data);
        setError(null);
      })
      .catch(err => {
        // auto catches network / connection error
        setIsPending(false);
        setError(err.message);
      })
    }, 1000);
  }, [url])

  return { data, isPending, error };
}
 
export default useFetch;
```


Using it
```
import useFetch from './useFetch';
const { data, isPending, Error } = useFetch('http://api.url');
```