# greeting_package

A simple npm package for greeting someone every day. Exports three tiny helper functions for time-of-day greetings, and is used as the example package for [npm-package-lab](../README.md).

## Install

```bash
npm install greeting_package
```

## Usage

```ts
import { morningGreet, eveningGreet, nightGreet } from "greeting_package";

morningGreet("Vaibhav"); // "Good Morning Vaibhav 🌞!"
eveningGreet("Vaibhav"); // "Good Evening Vaibhav 🌆!"
nightGreet("Vaibhav"); // "Good Night Vaibhav 😴!"
```

The package ships both CommonJS and ESM builds, plus TypeScript type declarations, so it works with `require` and `import`.

## API

| Function                     | Description                  |
| ----------------------------- | ----------------------------- |
| `morningGreet(name: String)` | Returns a morning greeting.   |
| `eveningGreet(name: String)` | Returns an evening greeting.  |
| `nightGreet(name: String)`   | Returns a night-time greeting.|

## Development

Source lives in `src/`. Each build compiles the TypeScript sources to `lib/` using Rollup.

```bash
npm install     # install dependencies
npm run build   # bundle src/ -> lib/ (cjs + esm + type declarations)
```

`npm run build` cleans `lib/` first (via `rollup-plugin-delete`), then emits:

- `lib/index.cjs` — CommonJS bundle
- `lib/index.esm.js` — ES module bundle
- `lib/types/` — TypeScript declaration files

Only the `lib/` folder is published (see the `files` field in [package.json](package.json)); `src/` is not part of the published package.

## Publish checklist

```bash
npm run build
npm publish --dry-run   # inspect what will be published
npm version patch|minor|major
npm publish
```
