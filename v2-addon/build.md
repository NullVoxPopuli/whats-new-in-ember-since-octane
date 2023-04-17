# Builds time behaviors with V2 Addons

V2 addons will typically be browser code, but can ship separate entrypoints which provide build-time plugins.

For example, consider this package.json#exports definition:
```
"exports": {
  ".": "./dist/browser/index.js",
  "./components/*": "./dist/browser/components/*.js",
  "./build": "./dist/build/index.cjs",
  "./build/webpack": "./dist/build/webpack.cjs"
}
```

The first two entries of `exports` are meant for browser usage, and allow a consuming app to use the index.js module as well as the components via their verbose import paths (which is good for tree shaking).

The next two imports are for providing build-time plugins to a build system. [Unplugin](https://github.com/unjs/unplugin/) is an effort to provide cross-ecosystem build plugins to a variaty of tools, rollup, vite, webpack, etc. 
However, webpack has a good number of quirks, so you may want to provide a separate webpack plugin entirely, depending on the functionalities of your plugin.
