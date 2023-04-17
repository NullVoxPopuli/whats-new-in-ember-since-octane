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

## Managing the document `title`

[ember-page-title](https://ember-cli.github.io/ember-page-title/) is now a default addon.


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

## ember-source 

### Router service refresh

[RFC#631](https://github.com/emberjs/rfcs/pull/631) proposed and implemented a `.refresh()` method on the router service. 

[Docs here](https://api.emberjs.com/ember/4.12/classes/RouterService/methods/refresh?anchor=refresh)

### `{{in-element}}`

Allows portalling content to other locations in the DOM.

[Demo here](https://tutorial.glimdown.com/4-logic/9-portalling)

[Docs here](https://api.emberjs.com/ember/release/classes/Ember.Templates.helpers/methods/each?anchor=in-element)

### `@ember/destroyable`

Introduced via [RFC#0580](https://emberjs.github.io/rfcs/0580-destroyables.html), which allows you to create and manage your own destroyables.

[Docs](https://api.emberjs.com/ember/release/functions/@ember%2Fdestroyable/registerDestructor)

### Cache API

```js
import { cached } from '@glimmer/tracking';
```

Decorator that caches values of getters, useful for retaining referential integrity.

[Docs](https://api.emberjs.com/ember/release/functions/@glimmer%2Ftracking/cached)

### `invokeHelper` and Helper Managers

These two features, combined with destroyables, are what enabled Resources to exist.

`invokeHelper` allows invoking helpers from JS, without knowing _how_ to invoke them.
Helper managers tell the framework _how_ to invoke helpers.

[`invokeHelper` Docs](https://api.emberjs.com/ember/release/functions/@ember%2Fhelper/invokeHelper)
[Helper Manager RFC](https://github.com/emberjs/rfcs/blob/master/text/0625-helper-managers.md)

### Named Blocks

Introduced in [RFC#460](https://rfcs.emberjs.com/id/0460-yieldable-named-blocks/), which at the time of writing is the best documentation for the feature.

This feature is good for design systems, and in general when the component author wants to control _layout_ of a component's parts, but wants to allow for the consumer to pass complex content, where the author's component can, in multiple locations, yield back to the consumer.

### `helper` Helper

Just like `component`, we can now use `helper` to curry helpers and yield helpers back to consumers.

[Docs](https://api.emberjs.com/ember/4.12/classes/Ember.Templates.helpers/methods/helper?anchor=helper)

### `modifier` Helper

Just like `component`, we can now use `modifier` to curry modifiers and yield modifiers back to consumers.

[Docs](https://api.emberjs.com/ember/4.12/classes/Ember.Templates.helpers/methods/modifier?anchor=modifier)
