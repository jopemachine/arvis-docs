---
layout: default
title: Plugin development
parent: Extension development
has_children: true
nav_order: 9998
---

# How to write arvis plugin

## Use [generator-arvis](https://github.com/jopemachine/generator-arvis) to create plugin skeleton

Just install `generator-arvis` and type `yo arvis` on your terminal.

## Use [arvish](https://github.com/jopemachine/arvish) to build your plugin

1. Write proper `arvis-plugin.json`.

2. Write some scripts to use in your `plugin`.

3. Type `arvish build` on your project root.

## Manual (not recommend)

<details><summary>Manual (not recommend)</summary>
<p>

1. Write proper `arvis-plugin.json`.
2. Write some scripts to use in your `plugin`.
3. Compress the scripts used in the `plugin` into a `.zip` file with the `arvis-plugin.json`.
4. Change the `.zip` file's extension to `.arvisplugin`
</p>
</details>

# `arvis-plugin.json` format

`arvis-plugin.json` format is very similar with `arvis-workflow.json` format.

[Click me to check arvis-plugin.json format]({{ site.baseurl }}{% link documents/extension-development/plugin/plugin-config-format.md %})

## Action

[Click me to check Action]({{ site.baseurl }}{% link documents/extension-development/action-description.md %})

## Entry point of plugin (`main`)

The js file specified in `main` is entry point of the `plugin`, which means this is imported by `Arvis` in runtime.

This file should export below form's function to be properly imported.

You can also use `async-await` syntax to this to handle some async operation.

```js
module.exports = ({ inputStr }) => {
  ...
 
  return {
    items: []
  }
};
```

You can check minimal working [plugin example](https://github.com/jopemachine/arvis-calculator-plugin-example) here.

### Arguments

#### inputStr

type: `string`

String entered by user

### Return value

#### items

type: `array`

required: `true`

[Click me to check Environment variables]({{ site.baseurl }}{% link documents/extension-development/plugin/plugin-items-format-description.md %})

#### noSort

type: `boolean`

required: `false`

defalult value: `false`

If you want to not sort your plugin item, use `noSort` option.

Note that `noSort` is true, your plugin items will be positioned most below position.

# JSON Schema

Recommend to use the [JSON schema](https://github.com/jopemachine/arvis-extension-validator/blob/master/plugin-schema.json) below when creating `plugin`.

You can simply create arvis-plugin skeleton file using the schema by [arvish](https://github.com/jopemachine/arvish).

# Available Environment variable

Both `workflows` and `plugin` set useful environment variables when running scripts.

You can use the variables you want in your script.

[Click me to check Environment variables]({{ site.baseurl }}{% link documents/extension-development/advanced/extension-env-description.md %})

# Debugging workflow, plugin

[How to debug workflow, plugin]({{ site.baseurl }}{% link documents/extension-development/debugging/debugging-description.md %})

# Arvish

If you are familiar with `Alfy`, you can try to use [arvish](https://github.com/jopemachine/arvish) in your js scripts.