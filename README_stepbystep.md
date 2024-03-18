# Project set up step by step

[Initiate a Vite project with tailwind](https://tailwindcss.com/docs/guides/vite) following the docs from tailwindcss

### Set Eslint and Prettier

Let's remove the default `.eslintrc.cjs` and make a json file of it with the following settings:

```json
{
  "extends": [
    "standard",
    "plugin:react/recommended",
    "plugin:tailwindcss/recommended",
    "prettier"
  ],
  "rules": {
    "max-len": [2, 250],
    "no-multiple-empty-lines": [
      "error",
      {
        "max": 1,
        "maxEOF": 1
      }
    ],
    "object-curly-newline": 0
  }
}
```

Now we need to install the eslint plugins that will work with the project, tailwind and prettier:

```bash
npm install eslint-config-standard eslint-plugin-tailwindcss eslint-config-prettier
```

Let's not forget to install Prettier with the command `npm install prettier`. In order for us to take advantage of better formatting, we need to add the following to the `.vscode/settings.json` file:

```json
{
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true,
        "source.addMissingImports": true
    },
    "prettier.tabWidth": 2,
    "prettier.useTabs": false,
    "prettier.semi": true,
    "prettier.singleQuote": false,
    "prettier.jsxSingleQuote": false,
    "prettier.trailingComma": "es5",
    "prettier.arrowParens": "always",
    "[typescriptreact]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    }
}
```

### Update assets and boilerplate code

We'll be updating the assets for the code, populating all the assets we will be using at the public folder. Then, we need to update some boilerplate coed at the `index.css`(base styles that will be srving globally), the `src/constants/index.js`(constants that will handle all the texts from the app and other constant info) and the `src/utils/index.js`(utils that will handle all the assets import/export so we can only do it using shorthand notation).