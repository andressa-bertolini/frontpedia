## useContext

Context: a way to store data and have it be accessible to components no matter where they are without having to pass it through props

```
import React, { createContext, useState } from "react";

export const GlobalContext = createContext();

export const GlobalProvider = ({ children }) => {
    const [state, setState] = useState("Initial Value");

    return (
        <GlobalContext.Provider value={{ state, setState }}>
            {children}
        </GlobalContext.Provider>
    );
};
```