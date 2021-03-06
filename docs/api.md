# Node.js API

To use `bili` programmatically:

```js
import bili from 'bili'

bili(options).catch(err => {
  if (err.snippet) {
    // display the actual error snippet
    console.error(err.snippet)
  }
  console.error(err.stack)
})
```

### name

Type: `string`

The filename of bundled files, the default value is package name in `package.json`. If no package.json was found, fallback to `index`.

### format

Type: `string` or `array`<br>
Default: `['cjs']`

Specific the bundle format, it could be a string like `'umd'` or multiple targets `['umd', 'cjs']`, it's useful if you want to support multiple standards. Default value is `['cjs']`.

You should specfic a `moduleName` if you target `umd`, otherwise fallback to `name`.

### compress

Type: `boolean`<br>
Default: `false`

Enable this option to generate an extra compressed file for the UMD bundle, and sourcemap.

### alias

Type: `object`

This is some feature which is similar to Webpack's `resolve.alias`.

### js

Type: `string`

And string that can be load via `require('rollup-plugin-'+js)`, used for transpiling ESnext code.

### replace

Type: `object`

Add options to [rollup-plugin-replace](https://github.com/rollup/rollup-plugin-replace).

### paths

Type: `object`

This helps you import some file from the CDN (as using AMD), or set an alias to an external file, see [more details in Rollup's WIKI](https://github.com/rollup/rollup/wiki/JavaScript-API#paths).

### map

Type: `boolean`<br>
Default: `false`

Generate soucemaps for `cjs` and `umd` builds, note that when option `compress` is set to `true` it will always generate sourcemaps for compressed file:

### flow

Type: `boolean`<br>
Default: `undefined`

Remove flow type annotations.

### exports

Type: `string`<br>
Default: `default`

[Specific what export mode to use](https://github.com/rollup/rollup/wiki/JavaScript-API#exports).

### watch

Type: `boolean`<br>
Default: `false`

Run Rollup in watch mode, which means you will have faster incremental builds.

### buble

Options for `rollup-plugin-buble`.

#### buble.transforms

Type: `object`<br>
Default:

```js
{
  generator: false,
  dangerousForOf: true
}
```

Apply custom transform rules to `buble` options.

#### buble.jsx

Type: `string`

Buble supports JSX, and you can specific a custom JSX pragma, eg: `h`.


#### buble.async

Type: `boolean`<br>
Default: `true`

Transform `async/await` to generator function, defaults to `true`. This is independently using `async-to-gen`.

#### buble.target

Type: `object`

Set compile targets for buble, eg: `{"chrome": 48, "firefox": 44, "node": 4}`.
