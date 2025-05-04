# Props

Props are arguments passed into React components. Props are passed to components via HTML attributes.

```
<Avatar
    size={50}
    person={{ 
        name: 'Lisa',
        age: '22'
    }}
/>
```

Read props inside the child component 
```
function Avatar({ person, size }) {
  // ...
}
```