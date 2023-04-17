## Ergonomics

### New file format

Per [RFC#779](https://github.com/emberjs/rfcs/pull/779), the prior exploration, and additional exploration, post-submission, we have a new file format, gjs and gts, (Glimmer JavaScript, and Glimmer TypeScript, respectively).

Tutorial: https://tutorial.glimdown.com/

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

<details><summary>js + hbs</summary>

```js
class Demo extends Component {
  someFunction = () => 'some content';
}
```
```hbs
{{this.someFunction}}
```
  
</details>
<details><summary>gjs</summary>
  
```gjs
function someFunction () {
  return 'Hello there';
}

<template>
  {{ (someFunction) }}
</template>  
```  
  
</details>  

[Announcement](https://blog.emberjs.com/plain-old-functions-as-helpers/)

### Everything can be used everywhere

<details><summary>js + hbs</summary>

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
  
</details>
<details><summary>gjs</summary>
  
```gjs
import { SomeModifier, SomeComponent, SomeHelper } from 'some-library';

<template>
  <SomeComponent {{SomeModifier (SomeHelper) }} />

  <@componentFromArgs {{@modifierFromArgs (@helperFromArgs) }} />
</template>  
```  
  
</details>  

[Guides docs](https://guides.emberjs.com/release/in-depth-topics/rendering-values/)

## Modifiers

[ember-modifier](https://github.com/ember-modifier/ember-modifier) has been added to the default blueprint.

More information about modifiers can be found on [the tutorial](https://tutorial.glimdown.com/).

## Dynamically tracked Objects, Arrays, Maps, Sets

[tracked-built-ins](https://github.com/tracked-tools/tracked-built-ins) has been added to the default blueprint.

Generally, wrapping complex data structures in a custom class that manages tracking lifecycles is good.

## Resources

Resources provide a way to encapsulate long lived state, cleanup, etc.

More information about them can be found in [ember-resources](https://github.com/NullVoxPopuli/ember-resources/), as well as [the tutorial](https://tutorial.glimdown.com/).
[Starbeam](https://www.starbeamjs.com/guides/fundamentals/resources.html) is another library implementing resources, and the [concepts](https://www.starbeamjs.com/guides/fundamentals/resources.html) are directly transferrable to ember.
