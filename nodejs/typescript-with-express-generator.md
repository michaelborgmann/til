# Minimal TypeScript Setup with `express-generator`

**Goal:** run an Express app with **.ts** routes using **Node’s built-in type stripping** (no `tsc`, no extra tooling).

## Prereqs

* **Node ≥ 23.6** (built-in TypeScript type-stripping).
* `npx express-generator` installed via `npx`.

## 1) Scaffold the app

```bash
npx express-generator my-app
cd my-app
npm i
```

> (You can use `--no-view` if you don’t want templates. Below uses the default generator output.)

## 2) Switch the project to ESM

Edit `package.json`:

```json
{
  "type": "module",
  "scripts": {
    "start": "node ./bin/www",
    "dev": "node --watch ./bin/www"
  }
}
```

## 3) Convert the app to ESM imports

Edit **`app.js`**:

```js
// import ESM deps
import express from 'express';
import path from 'node:path';
import { fileURLToPath } from 'node:url';
import cookieParser from 'cookie-parser';
import logger from 'morgan';

// import routers (note: one will be TypeScript)
import indexRouter from './routes/index.ts';
import usersRouter from './routes/users.js';

const app = express();

// __dirname in ESM
const __filename = fileURLToPath(import.meta.url);
const __dirname = path.dirname(__filename);

app.use(logger('dev'));
app.use(express.json());
app.use(express.urlencoded({ extended: false }));
app.use(cookieParser());
app.use(express.static(path.join(__dirname, 'public')));

// routes
app.use('/', indexRouter);
app.use('/users', usersRouter);

export default app;
```

## 4) Convert the bootstrap to ESM

Edit **`bin/www`** (keep filename; just use ESM):

```js
#!/usr/bin/env node

import app from '../app.js';
import debug from 'debug';
import http from 'node:http';

...
```

## 5) Make one route TypeScript

Rename **`routes/index.js` → `routes/index.ts`** and replace contents:

```ts
import express, { type Request, type Response } from 'express';

const router = express.Router();

router.get('/', (_req: Request, res: Response) => {
  res.render('index', { title: 'Express (TS route)' });
});

export default router;
```

> Note: we import it **with the `.ts` extension** in `app.js`. Node ≥ 23.6 can load `.ts` directly and strips types at runtime.

## 6) Run it

```bash
npm run dev
# open http://localhost:3000
```

That’s it. You now have an `express-generator` app running with a **TypeScript route** and **no compile step**. If you want editor type-checking later, add `typescript` and `@types/*` as dev deps—but it’s not required to run.

