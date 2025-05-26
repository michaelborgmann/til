# How to Inspect `[object Object]` in JavaScript

## 🧠 The Problem

When logging JavaScript objects, you might see this unhelpful output:

```bash
Token data: [object Object]
```

This happens because JavaScript tries to convert the object into a string using `toString()`, which results in `[object Object]`.

## ✅ The Fix: Properly Inspect Object Contents

1. Use `JSON.stringify()`

```js
console.log('Token data:', JSON.stringify(tokenData, null, 2));
```

- Converts the object to a readable JSON string.
- `null, 2` makes the output nicely formatted.

2. **Use `console.dir()` (especially in Node.js)**

```js
console.dir(tokenData, { depth: null });
```

- Displays the full structure of deeply nested objects.
- Avoids string coercion.

## 🧪 Bonus: Debug with Node.js Inspector

Run your app with:

```bash
node --inspect-brk app.js
```

## ❌ Don’t Do This

```js
console.log('Token data: ' + tokenData);
```

This coerces the object to a string: `[object Object]`.

## 🏁 Summary

Always use `JSON.stringify()` or `console.dir()` when inspecting objects to avoid the dreaded `[object Object]` output.
