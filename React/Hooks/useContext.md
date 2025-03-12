## useContext

Context is a way to store data and have it be accessible to components no matter where they are without having to pass it through props

Step by Step
- Create a context to store user data.
- Create a Provider that makes the context available to child components.
- Use useContext to access data within a component.

UserContext.js
```
import { createContext } from "react";
export const UserContext = createContext();
```

The Provider supplies user data to the entire application.

UserProvider.js
```
import { useState } from "react";
import { UserContext } from "./UserContext";

const UserProvider = ({ children }) => {
  const [user, setUser] = useState("Peter");

  return (
    <UserContext.Provider value={{ user, setUser }}>
      {children}
    </UserContext.Provider>
  );
};

export default UserProvider;

```

Now, we wrap the entire application with the UserProvider so that the components have access to the context.

App.js
```
import "./App.css";
import UserProvider from "./UserProvider";
import UserProfile from "./UserProfile";

function App() {
  return (
    <UserProvider>
      <div className="App">
        <h1>Context API em ação! 🚀</h1>
        <UserProfile />
      </div>
    </UserProvider>
  );
}

export default App;
```

Now, let's access the context without having to pass props!

UserProfile.js
```
import { useContext } from "react";
import { UserContext } from "./UserContext";

const UserProfile = () => {
  const { user } = useContext(UserContext); // Pegando o usuário do contexto

  return <h2>Usuário logado: {user}</h2>;
};

export default UserProfile;
```