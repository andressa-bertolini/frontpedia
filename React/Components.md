## Components

- [Function Component](https://github.com/andressabertolini/frontpedia/blob/main/React/Components.md/#Function%Component)

- [Class Component](https://github.com/andressabertolini/frontpedia/blob/main/React/Components.md/#Class%Component)

## Function Component

A component is a piece of the UI (user interface) that has its own logic and appearance

React components are JavaScript functions that return markup

Example 1
```
const Hello = () => {
    return(
        <div>Hello!</div>
    );
}

export default Home;
```

Example 2
```
function Hello() {
  return (
    <div>Hello</div>
  );
}
```

> [!NOTE]
> React component names must always start with a capital letter, while HTML tags must be lowercase

## Class Component

```
import React, { Component } from 'react';

class MyComponent extends Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  increment = () => {
    this.setState({ count: this.state.count + 1 });
  }

  render() {
    return (
      <div>
        <p>Contador: {this.state.count}</p>
        <button onClick={this.increment}>Incrementar</button>
      </div>
    );
  }
}

export default MyComponent;
```

Lifecycle
- Mounting
componentWillMount()
render() - first time
componentDidMount()

- Updating
getDerivedStateFromProps()
getSnapshotBeforeUpdate()
componentDidUpdate() - side effects
render() - updates the component

- Unmounting
componentWillUnmount() - cleanup