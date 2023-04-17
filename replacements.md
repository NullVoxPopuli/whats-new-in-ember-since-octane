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

`@ember/string` will be phased out and put in maintenance mode, because better solutions exist on npm.

The best alternative is [change-case](https://www.npmjs.com/package/change-case) which is cross-platform and ships ESM.

### `rsvp`

RSVP was largely a polyfill for Promises before Promises were standardized.
Nearly all of the features of RSVP have landed in native `Promise`, and at the time of writing, there is even a proposal for `RSVP.hash`: [Await dictionary](https://github.com/tc39/proposal-await-dictionary).
