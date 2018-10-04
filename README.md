# Optional Monorepo Bug

When using yarn workspaces, some dependencies might get installed in a
subfolder of a package. In this example it would be the dependency `packages/core/node_modules/lodash`.

Since `optional` only uses the NodeJS require resolution, which only checks dependencies
upwards from the root directoy e.g. `rootDirectory/../package.json` and not downwards `rootDirectory/*/package.json`
it can not find the lodash package. 

```
├── index.js
├── node_modules
|  └── optional
├── package.json
└── packages
   └── core
      ├── node_modules
      |  └── lodash
      └── package.json
```