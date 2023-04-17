### `Ember.onerror`

```js
function errorHandler(...) {

}

window.addEventListener('error', errorHandler);
```
[Docs](https://developer.mozilla.org/en-US/docs/Web/API/Window/error_event)

### `Ember.testing` 

```js
import { macroCondition, isTesting } from '@embroider/macros';

// ...

if (macroCondition(isTesting()) {

}
```

Unlike `Ember.testing`, anything in the testing block will be removed from production builds, whereas code with `Ember.testing` is left in production builds.

[Docs](https://github.com/embroider-build/embroider/blob/main/packages/macros/README.md) (does not require embroider)

### `@ember/string`

The core team is uninterested in updating `@ember/string` to be compatible with Polaris features, so it's best to move off.

Some alternatives:
 - [inflection](https://www.npmjs.com/package/inflection) (not ESM)
 - [change-case](https://www.npmjs.com/package/change-case) (cross-platform, ships ESM)
