## UseMemo Hook

In react, to update the state means you have to trigger and rerun the entire component

The state doesn't run again, just when it's initialized

UseMemo is a hook that memorizes a value and returns the same value untils any of the depedencies changes

```
import { useMemo } from 'react';

const selectedItem = useMemo(
    () => function, //should return something
    [variable]
);
```