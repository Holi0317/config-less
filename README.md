# @easy-webpack/config-less
This config allows you to bundle [Less] in your webpack bundle using [less-loader].

This use [config-css](https://github.com/easy-webpack/config-css) to achieve loading of CSS module. It is highly recommended to read the documentation of config-css before using this module.

# Installation
```
npm install --save-dev @easy-webpack/config-less
```
[easy-webpack](https://github.com/easy-webpack/core) is also required.

# Usage
```js
// webpack.config.js
const generateConfig = require('@easy-webpack/core').generateConfig;

const baseConfig = { ... }; // project-specific config like the entry file

module.exports = generateConfig(
  baseConfig,

  require('@easy-webpack/config-less')
    ({/* Options object */ filename: 'styles.css', allChunks: true, sourceMap: false })
);

// This config will compile less file imported and generate a CSS file named 'style.css' on output path 
```

# Options
All options (except the below one) are identical to that of config-css. Please refer to their [documentation](https://github/com/easy-webpack/config-css#options).

### additionalLoaders
Type: `string[]` Default: `[]`

This option need special notice as it may cause confusion.

All loaders string in this config option array will be append __before__ less-loader.

For example,

```js
const generateConfig = require('@easy-webpack/core').generateConfig;

generateConfig(
  require('@easy-webpack/config-less')
    ({ additionalLoaders: ['postcss-loader'], extractText: false })
)

// Final loader string will be 'style-loader!css-loader!postcss-loader!less-loader'
```

[Less]: http://lesscss.org/
[less-loader]: https://github.com/webpack/less-loader