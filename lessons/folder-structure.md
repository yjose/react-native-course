---
path: "/folder-structure"
title: "Folder Structure"
order: "2C"
section: "Getting Started"
description: "Learn React Native With Youssouf El Azizi"
---

Open the project in VS Code and you will see the following folder structure :

tree here

- `index.js` - this is the main entry point of your application. It is equivalent to React on the web mounting the project to the root DOM node
- `App.js` - this is the file that we care the most about. This is where we'll be writing all our code
- `/android` and `/ios` - these are the folders where all the native code lives. If we needed to add or edit any platform specific native code, this is where we'd have to look. We also need to go into these folders if we have to install any native libraries
- `.buckconfig` and `.flowconfig` - the facebook react native template comes with flow pre-installed. Using this is optional though and we will be sticking with plain React Native in this workshop.
- `.prettierrc.js` this is a code formatter which is again optional, but you can read more about it in our code style chapter

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
    'module:react-native-dotenv',
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
