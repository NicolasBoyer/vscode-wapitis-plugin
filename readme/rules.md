## Rules

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
| Rule                                                             | Description                                                                                                                             | Severity normal | Severity strict |
| :--------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | --------------- | --------------- |
| [no-incompatible-property-type](#-no-incompatible-property-type) | When using the @property decorator in Typescript, the property option `type` is checked against the declared property Typescript type   | error           | error           |
| [no-unknown-property-converter](#-no-unknown-property-converter) | LitElement provides default converters. For example 'Function' is not a valid default converter type for a LitElement-managed property. | error           | error           |
| [no-invalid-attribute-name](#-no-invalid-attribute-name)         | When using the property option `attribute`, the value is checked to make sure it's a valid attribute name.                              | error           | error           |
| [no-invalid-tag-name](#-no-invalid-tag-name)                     | When defining a custom element the tag name is checked to make sure it's valid.                                                         | error           | error           |

**Validating CSS**

<!-- prettier-ignore -->
| Rule                               | Description                                                     | Severity normal | Severity strict |
| :--------------------------------- | --------------------------------------------------------------- | --------------- | --------------- |
| [no-invalid-css](#-no-invalid-css) | CSS within the tagged template literal `css` will be validated. | warning         | error           |