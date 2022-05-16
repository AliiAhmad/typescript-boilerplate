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
yarn init -y
```

Create gitignore

```shell
touch .gitignore
```

Add the following gitignore

```
node_modules
yarn.lock
dist
```

Add entry point file to folder

```shell
mkdir src
touch src/index.ts
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

This will create a `tsconfig.json` file under the root of the node project.

Add the following to the `tsconfig.json` to include and exclude desired

```json
{
  "include": ["src/**/*.ts"],
  "exclude": ["node_modules"]
}
```

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
yarn run build
```

### ESLint

To set-up ESLint execute the following commands and follow through:

```shell
yarn add eslint --dev
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
    "lint:fix": "eslint src/**/*.ts --fix"
  }
}
```

To check, run the following in shell:

```shell
yarn run lint:check
```

To format the code to comply with linting rules, run the following in shell:

```
yarn run lint:fix
```

## Prettier

Install the dev dependencies by running:

```shell
yarn add prettier --dev
```

To configure Prettier create `.prettierrc` to the root of the project and add rules to it.

```shell
touch .prettierrc
```

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
    "pretty:check": "prettier --check .",
    "pretty:fix": "prettier --write ."
  }
}
```

### Husky

Husky is used for commit hooks.
Here we have set it up to Lint and Pretty check before commit

Install Husky to dev dependencies:

```shell
yarn add husky --dev
```

Add the following script to the `package.json`

```json
{
  "scripts": {
    "prepare": "husky install"
  }
}
```

Run script to prepare husky

```shell
yarn run prepare
```

Execute the following command to execute the pre-commit file to manage the commit scripts

```shell
yarn husky add .husky/pre-commit "<SCRIPT TO EXECUTE>"
```

Sample:

```shell
yarn husky add .husky/pre-commit "yarn run lint:check"
```
