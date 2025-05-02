## Conditional rendering 

You can use an if statement to conditionally include JSX
```
let content;
if (isLoggedIn) {
  content = <AdminPanel />;
} else {
  content = <LoginForm />;
}
return (
  <div>
    {content}
  </div>
);
```

If you prefer more compact code, you can use the conditional ? operator. Unlike if, it works inside JSX:
```
<div>
  {isLoggedIn ? (
    <AdminPanel />
  ) : (
    <LoginForm />
  )}
</div>
``` 

When you don’t need the else branch, you can also use a shorter logical && syntax:
```
<div>
  {isLoggedIn && <AdminPanel />}
</div>
```