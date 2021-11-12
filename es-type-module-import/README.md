# ES / type module / import

By setting

```
"type": "module"
```

in the package.json, node.js will import modules as ES modules, meaning that they are declared by

```javascript
// import.js
export const world = () => 'world';
```

and imported by

```javascript
// index.js
import {world} from "./import.js";
```

The `.js` extension needs to be included in the import statement!