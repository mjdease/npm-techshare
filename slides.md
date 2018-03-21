---
controls: false
transition: none
theme: night
---

<style type="text/css">
  .reveal p {
    text-align: left;
  }
  .reveal ul {
    display: block;
  }
  .reveal ol {
    display: block;
  }
</style>

## NPM Package Development

---

### Overview

* Current state of JS module formats
* Package configuration & tooling
* Development workflows

---

#### Module Formats

### CommonJS

* Module format for NodeJS
* Build tools (browserify etc.) enable these modules to be used in the browser
* Example module:

```js
// index.js
module.exports = myLib;
```

* Entry point is specified by the `main` field in `package.json`:

```json
{
  "main": "index.js"
}
```

---

#### Module Formats

### ES Modules (ESM)

* Language-level module support
* Supports multiple named exports and a default export
* Experimental Node support (requires `.mjs` extension)
* Example Module:

```js
// index.esm.js
export const anything = true;
export default myLib;
```


---

#### Module Formats

### ESM Recommendations

* ESM module should only use `import`/`export`, other ES2015+ features should be transpiled.
* Use the proposed `module` field in `package.json` for main ESM entry file (webpack will use it over `main` if available).
* Example `package.json`:

```json
{
  "main": "index.js",
  "module": "index.esm.js"
}
```

---

### Packaging

Configure Distributed Files
* `.npmignore` - File blacklist
* `files` property - File whitelist

Useful Commands

* `npm pack` - Create a tarball of a package
* `npm version` - Bump package version

---

### Local Development Workflow

Use case: Locally developing a lib and an app that uses the lib

In `my-great-lib/`:

```js
// package.json
{ "name": "my-lib" }
```

* Run *`npm link`*. (registers `my-lib` globally)

In `my-ok-app/`:

* Run *`npm link my-lib`*. Symlinks `my-lib` into `node_modules` for use in the app, `my-lib` updates as files in `my-great-lib/` change.

---

### Resources

* https://docs.npmjs.com/
* https://github.com/rollup/rollup/wiki/pkg.module
* https://nodejs.org/api/esm.html
* http://2ality.com/2017/09/native-esm-node.html


