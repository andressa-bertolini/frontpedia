https://redux-toolkit.js.org/
In the terminal, install redux toolkit and react-redux

```
npm install @reduxjs/toolkit
npm install react-redux
//or 
npm install @reduxjs/toolkit react-redux
```


In the src folder, create the "app" folder

We need to do is create a store file

store.js
```
import { configureStore } from '@reduxjs/toolkit';
import counterReducer from '../features/counter/counterSlice';

export const store = configureStore({
    reducer: {
        counter: counterReducer,
    },
})
```

index.js

---

Slice

counterSlice.js
```
import { createSlice } from '@reduxjs/toolkit';

const initialState = {
    count: 0
}

export const counterSlice = createSlice({
    name: 'counter',
    initialState,
    reducers: {
        increment: (state) => {
            state.count += 1;
        },
        decrement: (state) => {
            state.count -= 1;
        }
    }
})

export const { increment, decerement } = counterSlice.actions;

export default counterSlice.reducer;
```

---

Using the state

The useSelector hook is used to access the global state of the Redux store inside a React component. It allows you to "select" a specific piece of global state that your component needs.

```
import { useSelector } from 'react-redux';

function MyComponent() {
  const user = useSelector((state) => state.user); // Select the "user" state of the store

  return <div>Hi, {user.name}!</div>;
}
```

The useDispatch hook is used to dispatch actions to the Redux store. It returns the dispatch function, which you can use to dispatch actions.

```
import { useDispatch } from 'react-redux';

function MyComponent() {
  const dispatch = useDispatch();

  const handleClick = () => {
    dispatch({ type: 'UPDATE_USER', payload: { name: 'Amber' } });
  };

  return <button onClick={handleClick}>Update Name</button>;
}
```

Summary:
useSelector: Gets data from the Redux store for use in the component.
useDispatch: Dispatches actions to the Redux store, changing the state.

---

Counter.js
```
import { useSelector, useDistpatch } from 'react-redux';
import { increment, decrement } from './counterSlice';

const Counter = () => {
    const count = useSelector((state) => state.counter.count);
    const dispatch = useDispatch();

    return(
        <div>
            {count}
            <button onClick={() => dispatch(increment())}>+</button>
            <button onClick={() => dispatch(decrement())}>-</button>
        </div>
    )
}
```