This is a [Next.js](https://nextjs.org/) project template.

## Usage

```bash
git clone https://github.com/qhj/nextjs-template.git my-nextjs-app
```

## Steps to create this template

1. install `create-next-app`

```bash
pnpm add -g create-next-app
```

2. create next.js project

```bash
create-next-app --use-pnpm --ts nextjs-template
```

3. automatically install peer dependencies

```bash
echo "auto-install-peers=true" > .npmrc
```

4. add ESLint and Prettier

```bash
pnpm add -D prettier eslint-config-prettier eslint-plugin-prettier 
```

add prettier config and ignore file

`prettier.config.js`:

```js
module.exports = {
  semi: false,
  singleQuote: true,
  jsxSingleQuote: true,
}
```

`.prettierignore`:

```
.next
pnpm-lock.yaml
```

init eslint

```bash
pnpm create @eslint/create-config
```

```
✔ How would you like to use ESLint? · style
✔ What type of modules does your project use? · esm
✔ Which framework does your project use? · react
✔ Does your project use TypeScript? · No / Yes
✔ Where does your code run? · browser
✔ How would you like to define a style for your project? · guide
✔ Which style guide do you want to follow? · standard-with-typescript
✔ What format do you want your config file to be in? · JSON
✔ Would you like to install them now? · No / Yes
✔ Which package manager do you want to use? · pnpm
```

edit `.eslintrc.json`:

```json
{
  "env": {
    "browser": true,
    "es2021": true
  },
  "extends": [
    "next/core-web-vitals",
    "plugin:react/recommended",
    "standard-with-typescript",
    "plugin:react/jsx-runtime",
    "plugin:prettier/recommended"
  ],
  "parserOptions": {
    "ecmaVersion": "latest",
    "sourceType": "module",
    "project": "./tsconfig.json"
  },
  "plugins": ["react"],
  "rules": {
    "@typescript-eslint/explicit-function-return-type": "off",
    "@typescript-eslint/triple-slash-reference": "off"
  },
  "ignorePatterns": [
    "next.config.js",
    "prettier.config.js",
    "out"
  ],
  "reportUnusedDisableDirectives": true
}
```

set script:

```bash
npm pkg set scripts.lint="pnpm eslint ."
npm pkg set scripts.lint:fix="pnpm eslint --fix ."
```
