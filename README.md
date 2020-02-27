
<div align="center" markdown="1">

  <p align="center">
  <img src="https://github.com/NicolasBoyer/vscode-wapitis-plugin/blob/master/docs/assets/wapitis-plugin@256w.png?raw=true" alt="Logo" width="200" height="auto" />
</p>

  <p align="center">
  <b>Syntax highlighting, type checking and code completion for Wapitis</b></br>
  <sub><sub>
</p>

<br />


<!-- [![](https://vsmarketplacebadge.apphb.com/version-short/runem.lit-plugin.svg)](https://marketplace.visualstudio.com/items?itemName=runem.lit-plugin)
[![](https://vsmarketplacebadge.apphb.com/downloads-short/runem.lit-plugin.svg)](https://marketplace.visualstudio.com/items?itemName=runem.lit-plugin)
[![](https://vsmarketplacebadge.apphb.com/rating-short/runem.lit-plugin.svg)](https://marketplace.visualstudio.com/items?itemName=runem.lit-plugin) -->
<a href="https://opensource.org/licenses/MIT"><img alt="MIT License" src="https://img.shields.io/badge/License-MIT-green.svg" height="20"></img></a>


  <img src="https://github.com/NicolasBoyer/vscode-wapitis-plugin/blob/master/docs/assets/wapitis-plugin.gif?raw=true" alt="Lit plugin GIF"/>

</div>


[![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/dark.png)](#disclaimer)

## ➤ Disclaimer

This plugin is an adaptation of [lit-plugin](https://marketplace.visualstudio.com/items?itemName=runem.lit-plugin). It was created to work with [wapitis](https://nicolasboyer.github.io/wapitis) and add wapitis specifics configurations.

**Prefer lit-plugin to work with any other configuration than wapitis.**

All features are provided by these three libraries:

-   **[ts-wapitis-plugin](https://github.com/NicolasBoyer/lit-analyzer)** a fork of **[ts-lit-plugin](https://github.com/runem/lit-analyzer)**: The typescript plugin that powers the logic through the typescript language service (code completion, type checking, eg.).
-   **[vscode-lit-html](https://github.com/mjbvz/vscode-lit-html)**: Provides highlighting for the html template tag.
-   **[vscode-styled-components](https://github.com/styled-components/vscode-styled-components)**: Provides highlighting for the css template tag.

This library couples it all together and synchronizes relevant settings between vscode and `ts-wapitis-plugin`.


[![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/dark.png)](#rules)

## ➤ Rules

All the rules are the same as [lit-plugin](https://marketplace.visualstudio.com/items?itemName=runem.lit-plugin), but the default severity are changed as described below.

The default severity of each rule depend on the `strict` [configuration option](#-configuration). Strict mode is enabled as default.

Each rule can have severity of `off`, `warning` or `error`. You can toggle rules as you like.

**Validating custom elements**

<!-- prettier-ignore -->
| Rule                                         | Description                                                                                                                | Severity normal | Severity strict |
| :------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | --------------- | --------------- |
| [no-unknown-tag-name](#-no-unknown-tag-name) | The existence of tag names are checked. Be aware that not all custom elements from libraries will be found out of the box. | off             | error           |
| [no-missing-import](#-no-missing-import)     | When using custom elements in HTML it is checked if the element has been imported and is available in the current context. | off             | error           |
| [no-unclosed-tag](#-no-unclosed-tag)         | Unclosed tags, and invalid self closing tags like custom elements tags, are checked.                                       | warning         | error           |


**Validating binding names**

<!-- prettier-ignore -->
| Rule                                                                                                                                     | Description                                                                                                               | Severity normal | Severity strict |
| :--------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | --------------- | --------------- |
| [no-unknown-attribute](#-no-unknown-attribute-no-unknown-property)<br> [no-unknown-property](#-no-unknown-attribute-no-unknown-property) | You will get a warning whenever you use an unknown attribute or property within your `lit-html` template.                 | off             | error           |
| [no-unknown-event](#-no-unknown-event)                                                                                                   | When using event bindings it's checked that the event names are fired.                                                    | off             | error           |
| [no-unknown-slot](#-no-unknown-slot)                                                                                                     | Using the "@slot" jsdoc tag on your custom element class, you can tell which slots are accepted for a particular element. | off             | warning         |


**Validating binding types**

<!-- prettier-ignore -->
| Rule                                                                       | Description                                                                                                      | Severity normal | Severity strict |
| :------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | --------------- | --------------- |
| [no-invalid-boolean-binding](#-no-invalid-boolean-binding)                 | Disallow boolean attribute bindings on non-boolean types.                                                        | error           | error           |
| [no-expressionless-property-binding](#-no-expressionless-property-binding) | Disallow property bindings without an expression.                                                                | error           | error           |
| [no-noncallable-event-binding](#-no-noncallable-event-binding)             | Disallow event listener bindings with a noncallable type.                                                        | error           | error           |
| [no-boolean-in-attribute-binding](#-no-boolean-in-attribute-binding)       | Disallow attribute bindings with a boolean type.                                                                 | error           | error           |
| [no-complex-attribute-binding](#-no-complex-attribute-binding)             | Disallow attribute bindings with a complex type.                                                                 | error           | error           |
| [no-nullable-attribute-binding](#-no-nullable-attribute-binding)           | Disallow attribute bindings with nullable types such as "null" or "undefined".                                   | error           | error           |
| [no-incompatible-type-binding](#-no-incompatible-type-binding)             | Disallow incompatible type in bindings.                                                                          | error           | error           |
| [no-invalid-directive-binding](#-no-invalid-directive-binding)             | Disallow using built-in directives in unsupported bindings.                                                      | error           | error           |
| [no-unintended-mixed-binding](#-no-unintended-mixed-binding)               | Disallow mixed value bindings where a character `'`, `"`, `}` or `/` is unintentionally included in the binding. | warn            | warn            |

**Validating LitElement / Wapitis Element**

<!-- prettier-ignore -->
| Rule                                                             | Description                                                                                                                           | Severity normal | Severity strict |
| :--------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | --------------- | --------------- |
| [no-incompatible-property-type](#-no-incompatible-property-type) | When using the @property decorator in Typescript, the property option `type` is checked against the declared property Typescript type | error           | error           |
| [no-invalid-attribute-name](#-no-invalid-attribute-name)         | When using the property option `attribute`, the value is checked to make sure it's a valid attribute name.                            | error           | error           |
| [no-invalid-tag-name](#-no-invalid-tag-name)                     | When defining a custom element the tag name is checked to make sure it's valid.                                                       | error           | error           |

**Validating CSS**

<!-- prettier-ignore -->
| Rule                               | Description                                                     | Severity normal | Severity strict |
| :--------------------------------- | --------------------------------------------------------------- | --------------- | --------------- |
| [no-invalid-css](#-no-invalid-css) | CSS within the tagged template literal `css` will be validated. | warning         | error           |

[![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/dark.png)](#configuration)

## ➤ Configuration

With the exception of the section and the strict default which is ``true``, all the configuration is the same as the section ``Configuration`` of [lit-plugin](https://marketplace.visualstudio.com/items?itemName=runem.lit-plugin).

You can configure this plugin by going to `VS Code Settings` > `Extension` > `wapitis-plugin`.

**Note:** You can also configure the plugin using a `tsconfig.json` file (see [ts-lit-plugin](https://github.com/runem/lit-analyzer/blob/master/packages/ts-lit-plugin)).

### Available options

<!-- prettier-ignore -->
| Option                | Description                                                                                                                                                       | Type                                                                                                                                                                        | Default                                                 |
| :-------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| `strict`              | Enabling strict mode will change which rules are applied as default (see list of [rules](https://github.com/runem/lit-analyzer/blob/master/docs/readme/rules.md)) | `boolean`                                                                                                                                                                   | true                                                    |
| `rules`               | Enable/disable individual rules or set their severity. Example: `{"no-unknown-tag-name": "off"}`                                                                  | `{"rule-name": "off" \| "warn" \| "error"}`                                                                                                                                 | The default rules enabled depend on the `strict` option |
| `disable`             | Completely disable this plugin.                                                                                                                                   | `boolean`                                                                                                                                                                   | false                                                   |
| `dontShowSuggestions` | This option sets strict as                                                                                                                                        | `boolean`                                                                                                                                                                   | false                                                   |
| `htmlTemplateTags`    | List of template tags to enable html support in.                                                                                                                  | `string[]`                                                                                                                                                                  | ["html", "raw"]                                         |  |
| `cssTemplateTags`     | This option sets strict as                                                                                                                                        | `string[]`                                                                                                                                                                  | ["css"]                                                 |
| `globalTags`          | List of html tag names that you expect to be present at all times.                                                                                                | `string[]`                                                                                                                                                                  |                                                         |
| `globalAttributes`    | List of html attributes names that you expect to be present at all times.                                                                                         | `string[]`                                                                                                                                                                  |                                                         |
| `globalEvents`        | List of event names that you expect to be present at all times                                                                                                    | `string[]`                                                                                                                                                                  |                                                         |
| `customHtmlData`      | This plugin supports the [custom vscode html data format](https://code.visualstudio.com/updates/v1_31#_html-and-css-custom-data-support) through this setting.    | [Vscode Custom HTML Data Format](https://github.com/Microsoft/vscode-html-languageservice/blob/master/docs/customData.md). Supports arrays, objects and relative file paths |                                                         |




[![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/dark.png)](#other-features)

## ➤ Other features

You can find all the other features in the section ``other features`` of [lit-plugin](https://marketplace.visualstudio.com/items?itemName=runem.lit-plugin).


[![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/dark.png)](#contributors)

## ➤ Contributors
	

| [<img alt="Nicolas Boyer" src="https://joeschmoe.io/api/v1/random" width="100">](https://github.com/NicolasBoyer) | [<img alt="Rune Mehlsen" src="https://avatars2.githubusercontent.com/u/5372940?s=460&v=4" width="100">](https://twitter.com/runemehlsen) | [<img alt="Andreas Mehlsen" src="https://avatars1.githubusercontent.com/u/6267397?s=460&v=4" width="100">](https://twitter.com/andreasmehlsen) |
|:--------------------------------------------------:|:--------------------------------------------------:|:--------------------------------------------------:|
| [Nicolas Boyer](https://github.com/NicolasBoyer) | [Rune Mehlsen](https://twitter.com/runemehlsen)  | [Andreas Mehlsen](https://twitter.com/andreasmehlsen) |


[![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/dark.png)](#license)

## ➤ License
	
Licensed under [MIT](https://opensource.org/licenses/MIT).
