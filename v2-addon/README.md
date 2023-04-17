# v2 Addons

## New blueprint

New blueprint is [available here](https://github.com/embroider-build/addon-blueprint)

And can be used via `ember addon -b @embroider/addon-blueprint`

**NOTE**: This blueprint covers a lot of of the common things that need to be wired up for npm packages. V2 addons _are just npm packages_, however configuring npm packages to work correctly requires some nuance to package.json config. 
Best to read up on [package.json#exports](https://nodejs.org/api/packages.html#exports)

For migrating a v1 addon to a v2 addon, you may follow _[Porting Addons to V2](https://github.com/embroider-build/embroider/blob/main/PORTING-ADDONS-TO-V2.md)_ and
this blog post [Migrating an Ember addon to the next-gen v2 format
](https://www.kaliber5.de/de/blog/v2-addon_en).
