# CommonJS vs ES Modules in Node.js

## 🧩 Background

Node.js supports two module systems:

- **CommonJS (CJS)** — classic `require()` and `module.exports`
- **ECMAScript Modules (ESM)** — modern `import` / `export` syntax (also used in browsers)

---

## ✨ Key Differences

| Feature               | CommonJS                    | ES Modules                     |
|----------------------|-----------------------------|--------------------------------|
| Import syntax         | `const fs = require('fs')`  | `import fs from 'fs'`         |
| Export syntax         | `module.exports = ...`      | `export default ...` / `export const ...` |
| File extension        | `.js`                       | `.mjs` or set `"type": "module"` in `package.json` |
| Loading type          | Synchronous                 | Asynchronous                   |
| Top-level `await`     | ❌ Not allowed               | ✅ Allowed                     |
| Filename vars         | `__filename`, `__dirname`   | ❌ Not available directly      |

---

## 📦 Declaring ESM in Node.js

You can tell Node.js to treat files as ESM in two ways:

1. Use the `.mjs` file extension
2. Or add `"type": "module"` to your `package.json`:

```json
{
  "type": "module"
}
```

## 🔄 Interop Between ESM and CommonJS

### ✅ Importing CommonJS from ESM

```js
// file: index.mjs
import legacy from './legacy-cjs.js';
legacy.hello(); // "Hello from CommonJS"
```

```js
// file: legacy-cjs.js
module.exports = {
  hello: () => console.log("Hello from CommonJS"),
};
```

ESM can import a CJS module using a default import.

---

## ⚠️ Importing ESM from CommonJS

```js
// file: legacy-cjs.js
(async () => {
  const { default: esmFn } = await import('./esm-file.js');
  esmFn();
})();
```

```js
// file: esm-file.js
export default () => console.log("Hello from ESM!");
```

You **must** use dynamic `import()` — `require()` will not work with ESM files.

---

## 🚨 Gotchas

- Mixing CJS and ESM can cause compatibility issues and break tree-shaking.
- `require()` is not available in ESM modules.
- Named exports from CommonJS can be awkward when imported into - ESM — use `export default` when possible.

---

## 🧠 Pro Tip

If you're starting a new Node.js project, go **full ESM**:

- Cleaner syntax
- Compatible with browser code
- Future-friendly

---

## 🛠️ Bonus: Get __dirname and __filename in ESM

```js
// file: index.mjs
import { fileURLToPath } from 'url';
import { dirname } from 'path';

const __filename = fileURLToPath(import.meta.url);
const __dirname = dirname(__filename);

console.log(__dirname);
```
