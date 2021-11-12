# CommonJS / require

Without any further configuration, node.js will import modules as CommonJS modules, meaning that they are declared by

```javascript
// import.js
const world = () => 'world';
module.exports = {world}
```

and imported by

```javascript
// index.js
const {world} = require("./import");
```