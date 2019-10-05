# rollup-plugin-yaml

Convert .yaml and .yml files to ES6 modules:

```js
// import a single property from a YAML file
import { foo } from './config.yaml';

// import the whole file as an object
import config from './config.yaml';
```


## Installation

```bash
npm install --save-dev rollup-plugin-yaml
```


## Usage

```js
import { rollup } from 'rollup';
import yaml from 'rollup-plugin-yaml';

rollup({
  entry: 'main.js',
  plugins: [
    yaml({
      // All YAML files will be parsed by default,
      // but you can also specifically include/exclude files
      include: 'node_modules/**',  // Default: undefined
      exclude: [ 'node_modules/foo/**', 'node_modules/bar/**' ],  // Default: undefined
      // optionally transform yaml content
      transform(data) {
        if (Array.isArray(data))
          return data.filter((element) => element.private !== true);
        return data;
      }
    })
  ]
});
```


## License

MIT
