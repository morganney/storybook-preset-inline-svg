# Storybook Preset Inline SVG

A [Storybook preset](https://storybook.js.org/docs/react/addons/writing-presets) to load SVG files inline using `svg-inline-loader`.

## Basic Usage
First `npm install storybook-preset-inline-svg`

Then update one of the following files based on your Storybook setup:

* `.storybook/main.js`

    ```js
    module.exports = {
        addons: ['storybook-preset-inline-svg']
    }
    ```

* `.storybook/presets.js`

    ```js
    module.exports = ['storybook-preset-inline-svg']
    ```

## Advanced Usage

By default this preset will inline **all** SVG files. You can use these options to filter which SVG files are inlined or to pass options along to `svg-inline-loader`.

None of the options are required. Only use one of `include` or `exclude`, not both.

* `svgInlineLoaderOptions` options supported by [svg-inline-loader](https://www.npmjs.com/package/svg-inline-loader)
* `include` sets which files will be inlined. Only RegExp and Function are supported. See Webpack's [include](https://webpack.js.org/configuration/module/#ruleinclude).
* `exclude` sets which files will not be inlined. Only RegExp and Function are supported. See Webpack's [exclude](https://webpack.js.org/configuration/module/#ruleexclude).

For example,

```js
module.exports = {
  addons: [
    {
      name: 'storybook-preset-inline-svg',
      options: {
        include: /source\/.+\.svg$/,
        svgInlineLoaderOptions: {
          removeTags: true,
          removingTags: ['circle']
        }
      }
    }
  ]
}
```
