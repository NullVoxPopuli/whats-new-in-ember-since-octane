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
