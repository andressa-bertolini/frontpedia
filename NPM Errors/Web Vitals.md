## Error

> [!NOTE]
> This error happens when trying to create a new react project with "npx create-react-app"

rror: ENOENT: no such file or directory, open '/Users/andressabertolini/Desktop/node_modules/web-vitals/dist/web-vitals.js'
ERROR in ../node_modules/web-vitals/dist/web-vitals.js
Module build failed (from ./node_modules/source-map-loader/dist/cjs.js):
Error: ENOENT: no such file or directory, open '/Users/andressabertolini/Desktop/node_modules/web-vitals/dist/web-vitals.js'

webpack compiled with 1 error

## Solution
```
npm i web-vitals
```