## useContext

Context is a way to store data and have it be accessible to components no matter where they are without having to pass it through props

Step by Step
- Create a context to store data.
- Create a Provider that makes the context available to child components.
- Use useContext to access data within a component.


### Creating the context

Import createContext and assign it to a const. We need to create it in a separate file because we will need to import it in all the files we use the **Provider** or the **useContext** hook

context/GlobalContext.jsx
```
import { createContext } from 'react';
export const GlobalContext = createContext();
```

The Provider supplies data to the entire application. Now, we wrap the entire application with the provider so that the components have access to the context. Add the state you want to access in the value attribute
```
import { useState } from 'react';
import { GlobalContext } from './context/GlobalContext';
import ShowLanguage from './components/ShowLanguage';

function App() {
  const [language, setLanguage] = useState('en');

  return (
    <div className="App">
      <GlobalContext.Provider value={{language}}>
        <ShowLanguage />
      </GlobalContext.Provider>
    </div>
  );
}

export default App;
```

Now, let's access the context without having to pass props!

components/ShowLanguage.jsx
```
import { useContext } from 'react';
import { GlobalContext } from "../context/GlobalContext";

const ShowLanguage = () => {

  const { language } = useContext(GlobalContext);
  return (
    <div>
        Language: {language}
    </div>
  )
}

export default ShowLanguage
```