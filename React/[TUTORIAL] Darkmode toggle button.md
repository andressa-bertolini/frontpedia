Create a folder in src and name it 'context'. In this folder, create the fila 'GlobalContext.js'

```
import { createContext } from 'react';

export const GlobalContext = createContext();
```

Create the variables for the modes
```
export const themes = {
    light: {
        background: "white",
        text: "black"
    },
    dark: {
        background: "black",
        text: "white"
    }
}
```

Your file should look like this:
GlobalContext.js
```
import { createContext } from 'react';

export const themes = {
    light: {
        background: "white",
        text: "black"
    },
    dark: {
        background: "black",
        text: "white"
    }
}

export const GlobalContext = createContext(themes.light);
```

In 'App.js', supposing you have two components <Navbar /> and <Button /> you want to have access to the theme props, we should import context/themes and wrap them in a provider

```
import { GlobalContext, themes } from './context/GlobalContext';
<GlobalProvider.Provider>
    <Navbar />
    <Button />
</GlobalProvider.Provider>
```

We now need to create a state variable to store the mode
```
import { useState } from 'react';
const [theme, setTheme] = useState(themes.light);
```

Let's pass it to GlobalContext
```
<GlobalContext.Provider value={theme}>
```

App.js should look like this:
```
import Navbar from './components/Navbar';
import Button from './components/Button';

import { GlobalContext, themes } from './context/GlobalContext';

import { useState } from 'react';

function App() {
  const [theme, setTheme] = useState(themes.light);
  
  return (
    <div className="App">
      <GlobalContext.Provider value={theme}>
        <Navbar />
        <Button />
      </GlobalContext.Provider>
    </div>
  );
}

export default App;
```

Now we need to get the prop in the components. In 'Navbar.js' and 'Button.js', import useContext and GlobalContext
```
import { useContext } from 'react';
import { GlobalContext } from '../context/GlobalContext';
```

Create a const
```
const theme = useContext(GlobalContext);
```

We can apply it as inline CSS in the HTML
```
<ul style={{backgroundColor: theme.background}}>
    <li style={{ color: theme.text }}>Home</li>
    <li style={{ color: theme.text }}>About</li>
</ul>
```

Navbar.js
```
import { useContext } from 'react';
import { GlobalContext } from '../context/GlobalContext';

const Navbar = () => {
    const theme = useContext(GlobalContext);

    return(
        <ul style={{backgroundColor: theme.background}}>
            <li style={{ color: theme.text }}>Home</li>
            <li style={{ color: theme.text }}>About</li>
        </ul>
    )
}

export default Navbar;
```

Button.js 
```
import { useContext } from 'react';
import { GlobalContext } from '../context/GlobalContext';

const Button = () => {
    const theme = useContext(GlobalContext);
    return(
        <button
            style={{
                backgroundColor: theme.background,
                color: theme.text
            }}
        >
            Toggle Theme
        </button>
    )
}

export default Button;
```

To attach the toggle function to the button, we need to create the function in App.js
```
  const toggleTheme = () => {
    setTheme(state => (state === themes.light ? themes.dark : themes.light));
  }
```

Pass it to the Button
```
<Button changeTheme={toggleTheme} />
```

In 'Button.js', set the function
```
const Button = ({changeTheme}) => {
    const theme = useContext(GlobalContext);
    return(
        <button
            style={{
                backgroundColor: theme.background,
                color: theme.text
            }}
            onClick={changeTheme}
        >
            Toggle Theme
        </button>
    )
}
```

And we're done!