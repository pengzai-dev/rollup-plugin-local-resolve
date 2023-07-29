# rollup-plugin-resolve-index
Resolves Node-style directories with `index.js` files in Rollup



Rollup by default doesn't handle resolving `./folder` to `./folder/index.js` internally. While there is the `rollup-plugin-node-resolve` plugin which also resolves directories as well as all dependencies from the `node_modules` directory, these may sometimes be too much for the use case at hand.

## Installation
```
npm install --save-dev rollup-plugin-resolve-index
```

## Usage
```javascript
import { rollup } from 'rollup';
import localResolve from 'rollup-plugin-resolve-index';

// This will resolve `./files` to `./files/index.js` if the file exists
rollup({
  entry: './files',
  plugins: [localResolve()],
});
```
if you want to resolve a different file than `index.js` you can pass a `extensions` option to the plugin:
```javascript
// This will resolve `./files` to `./files/index.js` or `./files/index.jsx` if the file exists
rollup({
  entry: './files',
  plugins: [localResolve({
    extensions: ['.js', '.jsx'],
  })],
});
```

## Things to improve on
- Check for `index.js` file asynchronously
- Use absolute paths instead of relative ones to be consistent with how Rollup handles modules

## License
MIT, see `LICENSE` for more information
