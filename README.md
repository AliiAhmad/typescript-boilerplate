# Node Typescript Boilerplate Project

A bilerplate code setup enforcing development style

## Technologies utilized

- Node
- Typescript
- ESLint
- Prettier
- Husky

## Setup Procedure

Steps to recreate this environment

### Node

We initalize a barebone node project with only package.json file

```shell
npm init --y
```

### Typescript

Add Typescript to dev dependencies

```shell
yarn add typescript --dev
```

After adding the dev dependency, initalize the Typescript configuration file

```shell
tsc --init
```

This will create a `tsconfig.json` file under the root of the node project. Edit the file as per requirements.

**For more detailed configuration of `tsconfig.json` refer to [ESLint Documentation](https://eslint.org/docs/user-guide/getting-started)**

Adding the following line to `package.json`

```json
{
  "scripts": {
    "build": "tsc"
  }
}
```

To build, run the following in shell:

```shell
yarn build
```

### ESLint

To set-up ESLint execute the following command and follow through:

```shell
yarn create @eslint/config
```

This will create `.eslintrc.<FILETYPE>`.

It will also install the dev dependencies

- `@typescript-eslint/eslint-plugin`
- `@typescript-eslint/parser`

Add the folowing script to `package.json` for ESLint

```json
{
  "scripts": {
    "lint:check": "eslint src/**/*.ts",
    "link:fix": "eslint src/**/*.ts --fix"
  }
}
```

To check, run the following in shell:

```shell
yarn lint:check
```

To format the code to comply with linting rules, run the following in shell:

```
yarn lint:fix
```

## Prettier

Install the dev dependencies by running:

```shell
yarn add prettier --dev
```

To configure Prettier create `.prettierrc` to the root of the project and add rules to it.

**Sample Content**

```json
{
  "semi": true,
  "tabWidth": 2,
  "useTabs": false,
  "printWidth": 100,
  "singleQuote": true,
  "trailingComma": "es5",
  "jsxBracketSameLine": true
}
```

**For more detailed configuration of `.prettierrc` refer to [Prettier Documentation](https://prettier.io/docs/en/configuration.html)**

Adding the following line to `package.json`

```json
{
  "scripts": {
    "format:check": "prettier --check .",
    "format:write": "prettier --write ."
  }
}
```

### Husky

Husky is used for commit hooks.
Here we have set it up to Lint and Pretty check before commit

Install and Initialize Husky by following command:

```shell
npx husky-init && yarn
```

Edit the pre-commit file to manage the commit scripts

Sample:

```shell
npm run format:check
npm run lint:check
```
