## Updating a counter when clicking a button

```

In the 'src' folder, create the 'components' folder and the "Count.js" component inside it

Count.js
```
const Count = () => {
    return(
        <div>
        </div>
    );
}

export default Count;
```

Import useState in the component:
```
import { useState } from 'react';
```

Create the useState variable
```
const [count, setCount] = useState(0);
```

Create the buttons
```
<button onClick={() => setCount(count + 1)}>Increment</button>
<button onClick={() => setCount(count - 1)}>Decrement</button>
```

This is the full Count.js file
```
import { useState } from 'react';

const Count = () => {
    const [count, setCount] = useState(0);

    return(
        <div>
            count: { count }

            <button onClick={() => setCount(count + 1)}>Increment</button>
            <button onClick={() => setCount(count - 1)}>Decrement</button>
        </div>
    );
}

export default Count;
```

Don't forget to import the Count component to App.js
```
import Count from './components/Count';

function App() {
  return (
    <div className="App">
      <Count />
    </div>
  );
}

export default App;

``` 
