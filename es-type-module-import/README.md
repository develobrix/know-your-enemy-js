# ES / type module / import

* `npm run start` - execute code that uses the ES syntax with `export const` and `import <file>.js`.
* `npm run start:esmsr` - execute code that uses simplified import `import <file>` without extension.

## Explanation

By setting

```json
"type": "module"
```

in the `package.json`, node.js will import modules as ES modules, meaning that they are declared by

```js
// import.js
export const world = () => 'world';
```

and imported by

```js
// index.js
import {world} from "./import.js";
```

The `.js` extension needs to be included in the import statement, unless we run the script with the `--es-module-specifier-resolution=node` option:

```json
"start:esmsr": "node --es-module-specifier-resolution=node index-esmsr.js"
```

In that case, the import statement simplifies to

```js
// index-esmsr.js
import {world} from "./import";
```