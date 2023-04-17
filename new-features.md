## Ergonomics

### New file format

Per [RFC#779](https://github.com/emberjs/rfcs/pull/779), the prior exploration, and additional exploration, post-submission, we have a new file format, gjs and gts, (Glimmer JavaScript, and Glimmer TypeScript, respectively).

The goals of this new format and and problems it solves are explained in the RFC, so please read that if you have questions.

It looks like this:

```gjs
function someFunction () {
  return 'Hello there';
}

<template>
  {{ (someFunction) }}
</template>
```

For apps and 1v addons: [the addon that enables this](https://github.com/ember-template-imports/ember-template-imports/)
For v2 addons: [the rollup plugin](https://github.com/NullVoxPopuli/rollup-plugin-glimmer-template-tag/)

For ease of bridging between old Octane and the new, all code samples throughout this "what's new in ember since octane" guide will include both js/hbs + gjs ways of whatever the topic is.

### Normal functions are helpers

```js
class Demo extends Component {
  someFunction = () => 'some content';
}
```
```hbs
{{this.someFunction}}
```

[Announcement](https://blog.emberjs.com/plain-old-functions-as-helpers/)

### Everything can be used everywhere

```js
import { SomeModifier, SomeComponent, SomeHelper } from 'some-library';

class Demo extends Component {
  someModifier = SomeModifier;
  someComponent = SomeComponent;
  someHelper = SomeHelper;
}
```
```hbs
<this.someComponent {{this.someModifier (this.someHelper) }} />

<@componentFromArgs {{@modifierFromArgs (@helperFromArgs) }} />
```

[Guides docs](https://guides.emberjs.com/release/in-depth-topics/rendering-values/)

## Modifiers

[ember-modifier](https://github.com/ember-modifier/ember-modifier) has been added to the default blueprint

## Dynamically tracked Objects, Arrays, Maps, Sets

[tracked-built-ins](https://github.com/tracked-tools/tracked-built-ins) has been added to the default blueprint.

Generally, wrapping complex data structures in a custom class that manages tracking lifecycles is good.
