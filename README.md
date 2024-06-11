# Quasar App (quasar-project-with-vitest)

A Quasar project with vitest that fails due to

  > The requested module 'vite' does not provide an export named 'parseAstAsync'"

## Generated new project with

``` bash
yarn create quasar
quasar ext add @quasar/testing-unit-vitest
```

## Then
Pinned `package.json`  version numbers to specific versions for reproducability.

## Then

Add
``` json
"resolutions": {
  "@vitejs/plugin-vue": "^4.0.0",
  "vite": "^4.0.0"
},
```

to `package.json` per [these instructions](https://testing.quasar.dev/packages/unit-vitest/).

## Then

`yarn test:unit:ci`

gives

``` bash
$ vitest run
file:///C:/Temp/q/quasar-project-with-vitest/node_modules/vitest/dist/vendor/index.c1V_jzyZ.js:23
import { parseAstAsync } from 'vite';
         ^^^^^^^^^^^^^
SyntaxError: The requested module 'vite' does not provide an export named 'parseAstAsync'
    at ModuleJob._instantiate (node:internal/modules/esm/module_job:132:21)
    at async ModuleJob.run (node:internal/modules/esm/module_job:214:5)
    at async ModuleLoader.import (node:internal/modules/esm/loader:329:24)
    at async main (file:///C:/Temp/q/quasar-project-with-vitest/node_modules/vitest/dist/cli-wrapper.js:45:5)

Node.js v20.10.0
error Command failed with exit code 1.
```


