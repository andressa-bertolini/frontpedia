## Router

Install the router package
```
npm install react-router-dom
```

> [!NOTE]
> react-router is a library for managing routes in React applications. It allows you to define and navigate between different pages or sections of your app, and react-router-dom is a browser-specific version of this library. DOM stands for 'Document Object Model' (the HTML elements of a web application in simple words).

First, let's create the navigation component. Inside the "src" folder, create a folder called "layouts"

Inside the layouts folder, create a file called **Navigation.js**

The structure of this component is as follows:

```
import { NavLink } from "react-router-dom";

const Navigation = () => {
    return <div>
        <NavLink exact to="/">Home</NavLink>
        <NavLink exact to="/about">About</NavLink>
        <NavLink exact to="/contact">Contact</NavLink>
    </div>;
};

export default Navigation;
```

> [!NOTE]
> NavLink is imported in {} because it's a named export

> [!NOTE]
> Exact ensures that the "Home" link will only be activated when the URL is exactly "https://yoursite.com/", and not on URLs that contain the path / followed by other subroutes (such as /about or /contact). Without exact, the NavLink to "Home" would be activated on any URL that starts with /, which would cause the link to not activate correctly on internal pages.

The other components will be the pages, create the “pages” folder inside the “src” folder. Create the file “Home.js” inside this folder

Home.js
```
const Home = () => {
    return <div>
        <h1>Home</h1>
    </div>;
};

export default Home;
```

Now that we've created everything we need, it's time to put it all together. In the "src" folder, open the App.js file and import the react-router-dom components:

```
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
```

> [!NOTE]
> Here, we are importing three main components from react-router-dom: BrowserRouter, Routes, and Route. In the part, "BrowserRouter as Router", we are simply creating an alias (Router) for the BrowserRouter.

We will need to import all the components we created, we can add comments /* layout */ and /* pages */ to better organize the project:

```
/* Layout */
import Navigation from './layouts/Navigation';
/* Pages */
import Home from './pages/Home';
```

Finally, we will create the routes for our menu with the <Navigation /> component inside the App() function. (You can delete the default content)
```
<Router>
  <Navigation />

  <Routes>
      <Route path="/" element={<Home />} />
      /* Other examples */
      <Route path="/about" element={<About />} />
      <Route path="/contact" element={<Contact />} />
  </Routes>
</Router>
```

And our App.js file will look like this:
```
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
/* Layout */
import Navigation from './layouts/Navigation';
/* Pages */
import Home from './pages/Home';

function App() {
  return (
    <div>
      <Router>
        <Navigation />

        <Routes>
            <Route path="/" element={<Home />} />
            /* Other examples */
            <Route path="/about" element={<About />} />
            <Route path="/contact" element={<Contact />} />
        </Routes>
      </Router>
    </div>
  );
}

export default App;
```