# v2 Addons

[RFC#507](https://rfcs.emberjs.com/id/0507-embroider-v2-package-format/) describes the motivation and purpose of V2 addons.

The tl;dr: 
 - move builds of addons from the consuming app to publish-time of the addon (makes apps faster)
 - support tree-shaking
 - align with broader community standards by _being normal npm packages_ (v1 addons are node programs that apps ask to emit browser code)

## New blueprint

New blueprint is [available here](https://github.com/embroider-build/addon-blueprint)

And can be used via `ember addon -b @embroider/addon-blueprint`

**NOTE**: This blueprint covers a lot of of the common things that need to be wired up for npm packages. V2 addons _are just npm packages_, however configuring npm packages to work correctly requires some nuance to package.json config. 
Best to read up on [package.json#exports](https://nodejs.org/api/packages.html#exports)

For migrating a v1 addon to a v2 addon, you may follow _[Porting Addons to V2](https://github.com/embroider-build/embroider/blob/main/PORTING-ADDONS-TO-V2.md)_ and
this blog post [Migrating an Ember addon to the next-gen v2 format
](https://www.kaliber5.de/de/blog/v2-addon_en).

## Migrating v1 addons

There are two utilities to aid in migration

 - [ember-addon-migrator](https://github.com/NullVoxPopuli/ember-addon-migrator)
 - [v1-to-v2-codemod](https://github.com/ijlee2/ember-codemod-v1-to-v2)