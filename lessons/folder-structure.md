---
path: "/folder-structure"
title: "Folder Structure"
order: "2C"
section: "Getting Started"
description: "Learn React Native With Youssouf El Azizi"
---

Open the project in VS Code and you will see the following folder structure :

```bash
.
├── App.tsx
├── __tests__
├── android
├── app.json
├── babel.config.js
├── index.js
├── ios
├── metro.config.js
├── node_modules
├── package.json
├── tsconfig.json
├── .eslintrc.js
├── .prettierrc.js
└── yarn.lock
```

- `index.js` - this is the main entry point of your application. It is equivalent to React on the web mounting the project to the root DOM node
- `App.ts` - this is the file when we can find the root component.
- `/android` and `/ios` - these are the folders where all the native code lives. If we needed to add or edit any platform specific native code, this is where we'd have to look. We also need to go into these folders if we have to install any native libraries.
- `tsconfig.json` - typescript config.
- `.eslintrc.js`, `.prettierrc.js` - eslint and prettier config.
- `metro.config.js` - Development server configuration.
- `babel.config.js` - babel config file.

### Setup typescript for easy import

During your journey writing clean and reusable code, for sure you are going to use `import x for "file"` statement and as you code source grow you will find yourself writing import some wired import statement like the following:

```js
import foo from "../.../../folder/foo";
```

The best way to make your code clean in such cases is to use absolute import.

To start using absolute import in your project you need to update `baseUrl` config inside the `tsconfig.json` configuration file to `./src`.

Aso you will need to use module-resolver babel plugin to update resolver root folder for babel like the following:

```js
plugins: [
    [
      'module-resolver',
      {
        root: ['./src'],
        extensions: [
          '.ios.ts',
          '.android.ts',
          '.ts',
          '.ios.tsx',
          '.android.tsx',
          '.tsx',
          '.jsx',
          '.js',
          '.json',
        ],
      },
    ],
  ],




```

## 👨🏻‍💻 Exercise

Open your project on VS Code and configure `babel-plugin-module-resolver`.
