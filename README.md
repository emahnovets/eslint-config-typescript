# eslint-config-typescript

![Node.JS CI workflow](https://github.com/emahnovets/eslint-config-typescript/actions/workflows/main.yaml/badge.svg)

## How to enable in projects?

1. Configure project to read packages started from `@emahnovets` from github package registry by running
```bash
npm config set @emahnovets:registry=https://npm.pkg.github.com --userconfig ./.npmrc
```
2. Install npm package
```bash
npm install --save-dev eslint @emahnovets/eslint-config-typescript prettier
```
3. Create `.eslintrc.js` file with following content
```js
module.exports = {
  extends: '@emahnovets/eslint-config-typescript',
  parserOptions: {
    project: './tsconfig.json', // Specify path to your tsconfig file
  }
}
```
4. Create `.prettierrc.js` file locally:
```js
module.exports = {
  "printWidth": 120,
  "tabWidth": 2,
  "useTabs": false,
  "semi": true,
  "singleQuote": true,
  "trailingComma": "all",
  "bracketSpacing": true,
  "bracketSameLine": false,
  "arrowParens": "always",
  "quoteProps": "consistent",
  "endOfLine": "lf"
}
```
5. Create `lint` script in your `package.json` file
```json
{
  // ...
  "scripts": {
    // ...
    "lint": "eslint --ext .js,.ts src" // specify file extensions and folders to run eslint
  },
}
```
6. (optionally) configure VSCode to fix eslint errors on file save by creating `.vscode/settings.json` file in your repo
```json
{
  "eslint.validate": [
    "javascript",
    "typescript"
  ],
  "eslint.packageManager": "npm",
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```
