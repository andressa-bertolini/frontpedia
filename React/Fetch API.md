You will need the URL that contains a key as a parameter from the API
```
const API_URL = 'https://apiurl.api?apikey=12345';
```

Create the function to fetch the API
```
const fetchAPI = () => {
  fetch(API_URL)
      .then(res => res.json())
      .then(data => {
          console.log(data);
      })
}
```

Import the useEffect hook to load the API
```
import { useEffect } from 'react';
```

Call the funtion in useEffect
```
useEffect(() => {
  fetchAPI();
},[])
```

---

Variations:

Storing the API parts in an object:
```
const api = {
  key: "abcde12345",
  base: "https://apiurl.api/"
}

fetch(`${api.base}?q=${string}&id=12345&appid=${api.key}`)
    .then(res => res.json())
    .then(result => {
        console.log(result);
    }
)
```

Fetch alternative:
```
const fetchAPI = async () => {
  const response = await fetch(`${API_URL}`);
  const data = await response.json();

  console.log(data);
}
```

---

Errors

Network error
```
import { useState } from "react";
const [error, setError] = useState();

.catch(err => {
  console.log(err.message);
  setError(err.message);
})
```

Data error
```
.then(res => {
  if(!res.ok){
    throw Error('Could not fetch the data for that resource');
  }
})
```
---

Clean the error for the next request
```
.then(data => {
  setError(null);
})
```

POST
```
const [title, setTitle] = useState('');
const [body, setBody] = useState('');
const [author, setAuthor] = useState('Author 1');

const data = { title, body, author }

fetch('http://api.url',{
  method: 'POST',
  headers: {"Content-Type": "application/json"},
  body: JSON.stringfy(data)
})
```

DELETE
```
fetch('http://api.url/' + id, {
  method: 'DELETE'
})
```