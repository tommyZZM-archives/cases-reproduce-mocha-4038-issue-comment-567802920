### Cases

**node:** 13.5.0

**node -r esm ./entry-async-import.mjs**
```
123
[Module] { default: 1 }
```

**npm run mocha -- ./entry-async-import.mjs**
```
(node:72572) ExperimentalWarning: The ESM module loader is experimental.
123

  0 passing (0ms)

[Module] { default: 1 }
```

**npm run mocha -- -r esm ./entry-async-import.mjs** (FAILED)
```
TypeError: Invalid host defined options ...
    at Object.exports.requireOrImport (/Users/xxx/Downloads/node_modules/mocha/lib/esm-utils.js:9:30)
    at Object.exports.loadFilesAsync (/Users/xxx/Downloads/node_modules/mocha/lib/esm-utils.js:32:34)
    at Mocha.loadFilesAsync (/Users/xxx/Downloads/mocha-esm-bug-reproduce/node_modules/mocha/lib/mocha.js:342:19)
```

**node ./entry-import.mjs**
```
(node:72831) ExperimentalWarning: The ESM module loader is experimental.
123 typeof expect function
```

**node -r esm ./entry-import.mjs**
```
123 typeof expect function
```

**npm run mocha -- ./entry-import.mjs**
``` 
(node:72840) ExperimentalWarning: The ESM module loader is experimental.
123 typeof expect function

  0 passing (0ms)

```

**npm run mocha -- -r esm ./entry-import.mjs** (FAILED)
```
TypeError [ERR_VM_DYNAMIC_IMPORT_CALLBACK_MISSING]: A dynamic import callback was not specified.
    at exports.importModuleDynamicallyCallback (internal/process/esm_loader.js:41:9)
    at Object.exports.requireOrImport (/Users/xxx/Downloads/mocha-esm-bug-reproduce/node_modules/mocha/lib/esm-utils.js:9:30)
    at Object.exports.loadFilesAsync (/Users/xxx/Downloads/mocha-esm-bug-reproduce/node_modules/mocha/lib/esm-utils.js:32:34)
    at Mocha.loadFilesAsync (/Users/xxx/Downloads/mocha-esm-bug-reproduce/node_modules/mocha/lib/mocha.js:342:19)
    at Mocha.runAsync (/Users/xxx/Downloads/mocha-esm-bug-reproduce/node_modules/mocha/lib/mocha.js:953:12)
```
