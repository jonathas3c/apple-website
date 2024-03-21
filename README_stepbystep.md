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

Build project as usual: Navbar, Hero sections. When building hero section, let's install gsap to allow us to use the tweening functions to animate the hero section.

```bash
npm install gsap @gsap/react
```

We can use the example codes from the `Hero.jsx` file to see how to implement gsap animations. Basically, we can make all the components that will be animated to have an opacity of 0 initially, and then we animate the way this specific component will be set to opacity 1 usin the useGSAP hook, like below:

```js
useGSAP(() => {
  gsap.to("#hero", { opacity: 1, delay: 2 });
  gsap.to("#cta", { opacity: 1, y: -50, delay: 2 });
}, []);
```
