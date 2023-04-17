## Ergonomics

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
