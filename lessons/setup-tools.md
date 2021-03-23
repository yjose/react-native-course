---
path: "/tools"
title: "Tools & Scripts"
order: "2B"
section: "Getting Started"
description: "Learn React Native With Youssouf El Azizi"
---

I recommend using [VS Code ](https://code.visualstudio.com/) and installing the following extensions for this workshop, but feel free to use your favorite code editor ( sublime ... ).

- [React Native Vs Code Snippet](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets)
- [Visual Studio Code extension for Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [Integrates ESLint JavaScript into VS Code.](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [Auto Import - ES6, TS, JSX, TSX](https://marketplace.visualstudio.com/items?itemName=NuclleaR.vscode-extension-auto-import)
- [Auto Close Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-close-tag)
- [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)

### Setup Husky pre-commit hook with ESLint.

Husky lets us run commands or script before committing or pushing our code to git, its very useful to To stupe some pre-commit hook easily, we are going to use it to run Eslint and Prettier to validate our commit. We can use the power of pre-commit to Make sure our commit messages meet the conventional commit format.

- Install Deps :

```bash
yarn add husky lint-staged @commitlint/config-conventional @commitlint/cli -D
```

- Configure commitlint to use conventional config (optional)

```bash
echo "module.exports = {extends: ['@commitlint/config-conventional']}" > commitlint.config.js
```

- Add the following code to your `package.json`

```json
"scripts": {
    "prepare": "husky install"
  }

"lint-staged": {
    "*.{js,jsx,tsx}": "eslint"
  }
```

- Run the following commands to init husky

```bash
#init husky
npx husky init

npx husky add .husky/commit-msg 'yarn commitlint --edit "$1"'

npx husky add .husky/pre-commit "yarn lint"

```

### Useful npm scripts

Some Npm script to be added to your `package.json`

```json
 "clean:android": "cd android && ./gradlew cleanBuildCache && ./gradlew clean && cd ..",
 "clean:ios": "rm -rf ios/build",
 "clean": "run-p clean:*",
 "setup:ios": "cd ios && pod install --repo-update && cd ..",

```

> Make sure to install [npm-run-all](https://github.com/mysticatea/npm-run-all) as Dev deps

👉 https://github.com/yjose/Tasker/commit/196b94dde797f3ee480a6ab54fc5289c72f881bd

### Useful Links

[Husky](https://typicode.github.io/husky/#/)

[Conventional commits](https://www.conventionalcommits.org/en/v1.0.0/)
