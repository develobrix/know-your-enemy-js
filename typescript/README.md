# TypeScript

* `npm install` to install TypeScript

After that there are three ways to transpile and execute the code:

* `npm run start:es5:commonjs` transpiles the code to ES5 syntax with CommonJS modules and executes it
* `npm run start:es6:commonjs` transpiles the code to ES6 syntax with CommonJS modules and executes it
* `npm run start:es6:es6` transpiles the code to ES6 syntax with ES modules and executes it

The JS code can be viewed in the corresponding `dist` directory.

## Explanation

### Modules and imports in TypeScript

TypeScript uses the same module/import syntax as ES-style Javascript, meaning that modules are defined by

```ts
// src/import.ts
export const world = () => 'world';
```

and imported by

```ts
// src/index.ts
import {world} from "./import";
```

### TypeScript compiler options

The style of the generated JS code is determined by two options in the [tsconfig.json](./tsconfig-es5-commonjs.json):

```json
"target": "ES5"
...
"module": "commonjs"
```

* `target` defines to what ES syntax the code is transpiled to (supported language features etc.)
* `module` defines the module/import style of the generated code

#### ES5 syntax with CommonJS modules

```js
// dist-es5-commonjs/import.js
"use strict";
Object.defineProperty(exports, "__esModule", { value: true });
exports.world = void 0;
var world = function () { return 'world'; };
exports.world = world;
```

#### ES6 syntax with CommonJS modules

ES6 supports arrow functions, while ES5 doesn't. So when the code is transpiled to ES6, the arrow function is preserved:

```js
// dist-es6-commonjs/import.js
"use strict";
Object.defineProperty(exports, "__esModule", { value: true });
exports.world = void 0;
const world = () => 'world';
exports.world = world;
```

#### ES6 syntax with ES modules

When using ES modules, it is crucial that either `"type": "module"` is set in the package.json, or (like in this case) the JS files have the `.mjs` extension.

```js
// dist-es6-es6/import.mjs
export const world = () => 'world';
```

The node command needs to be executed with the `--es-module-specifier-resolution=node` option.