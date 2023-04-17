# Tooling

## Glint

Glint is a layer on top of typescript that provides type checking for gjs, gts, and hbs.

Docs, setup, usage are all documented here: https://typed-ember.gitbook.io/glint

## `--typescript`

ember-cli can now generate typescript projects, and TypeScript is officially supported.
More information can be found in [the RFC](https://github.com/emberjs/rfcs/pull/724).

To generate an app or addon with TypeScript out of the box, run one of the following:
```bash
# App
ember new my-app --typescript
# v1 Addon
ember addon my-addon --typescript
# v2 Addon
ember addon my-addon -b @embroider/addon-blueprint --typescript
```

## Embroider

Old apps can't "just" switch to Vite. Embroider provides the stepping stones and intermediary / incremental migration path towards pure Vite usage.

Getting to standalone vite usage will require all your consumed addons to be in the [v2 format](./v2-addon/README.md).

### CSS-Modules

The implementation of ember-css-modules (at the time of writing) has some issues, but there is [an alternative, embroider-css-modules](https://github.com/ijlee2/embroider-css-modules).
There is also a more manual way of using CSS-modules described here [in this discuss post](https://discuss.emberjs.com/t/ember-modern-css/19614)

## `ember-cli-typescript`

This addon is on its way out, and will soon:tm: deprecated by the typed-ember team.

At the moment, the way to use TypeScript without `ember-cli-typescript` is to, `ember install ember-cli-typescript`, and then remove the two addons it installs (`ember-cli-typescript`, and `ember-cli-typescript-blueprints`).
Following the README from [`ember-cli-babel`](https://github.com/babel/ember-cli-babel#enabling-typescript-transpilation), typescript transpilation can be added by setting this setting in your `ember-cli-build.js`:
```js
// ember-cli-build.js
module.exports = function(defaults) {
  let app = new EmberApp(defaults, {
    'ember-cli-babel': {
      enableTypeScriptTransform: true
    }
  });

  return app.toTree();
}
```
