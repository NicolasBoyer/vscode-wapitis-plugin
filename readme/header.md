
<div align="center" markdown="1">

  {{ template:logo }}

  {{ template:description }}

<!-- [![](https://vsmarketplacebadge.apphb.com/version-short/runem.lit-plugin.svg)](https://marketplace.visualstudio.com/items?itemName=runem.lit-plugin)
[![](https://vsmarketplacebadge.apphb.com/downloads-short/runem.lit-plugin.svg)](https://marketplace.visualstudio.com/items?itemName=runem.lit-plugin)
[![](https://vsmarketplacebadge.apphb.com/rating-short/runem.lit-plugin.svg)](https://marketplace.visualstudio.com/items?itemName=runem.lit-plugin) -->
<a href="https://opensource.org/licenses/MIT"><img alt="MIT License" src="https://img.shields.io/badge/License-MIT-green.svg" height="20"></img></a>


  <img src="https://github.com/NicolasBoyer/vscode-wapitis-plugin/blob/master/docs/assets/wapitis-plugin.gif?raw=true" alt="Lit plugin GIF"/>

</div>

## Disclaimer

This plugin is an adaptation of [lit-plugin](https://marketplace.visualstudio.com/items?itemName=runem.lit-plugin). It was created to work with [wapitis](https://nicolasboyer.github.io/wapitis) and add wapitis specifics configurations.

**Prefer lit-plugin to work with any other configuration than wapitis.**

All features are provided by these three libraries:

-   **[ts-wapitis-plugin](https://github.com/NicolasBoyer/lit-analyzer)** a fork of **[ts-lit-plugin](https://github.com/runem/lit-analyzer)**: The typescript plugin that powers the logic through the typescript language service (code completion, type checking, eg.).
-   **[vscode-lit-html](https://github.com/mjbvz/vscode-lit-html)**: Provides highlighting for the html template tag.
-   **[vscode-styled-components](https://github.com/styled-components/vscode-styled-components)**: Provides highlighting for the css template tag.

This library couples it all together and synchronizes relevant settings between vscode and `ts-wapitis-plugin`.