---
path: "/env-vars"
title: "Environment variables"
order: "2E"
section: "Getting Started"
description: "Learn React Native With Youssouf El Azizi"
---

Using a solution to load environment variables for your React Native application is very important to make maintaining your keys and URLs an easy task.

There are multiple solutions like [react-native-config](https://github.com/luggit/react-native-config) which the most popular one but the library requires Native linking and adding or updating new environment variables and that means rebuilding the App.

Also, [react-native-config](https://github.com/luggit/react-native-config) comes with the possibility to use environment variables on native code (Android/Obj-C) but this requires manual steps to follow.

The 2nd solution which we recommend to use is [react-native-dotenv](https://github.com/goatandsheep/react-native-dotenv), a babel plugin that can Load environment variables using import statements.

## Setup react-native-dotenv

```
yarn add react-native-dotenv -D
```

Add plugin to `.babelrc` configuration

```js
plugins: ["module:react-native-dotenv"];
```

Now Create your `.env` and `.env.development` files in the project root folder.

```
API_URL=http://example.com/
```

Now, you can easily import your environment variables

```js
import { API_URL } from "@env";

fetch(`${API_URL}/users`);
```

For typescript, you should add a typing file for "@env" module.
Create a file `types/env.d.ts` in your root folder and type your variables

```ts
declare module "@env" {
  export const API_URL: string;
}
```

⚠️ Make sure to restart your metro server whenever you update the env files

```bash
yarn start --reset-cache
```

👉 https://github.com/yjose/Tasker/commit/d318cf0c43c32dc4602f4d6bdf784f897da0bdb4

### Helpful Links

- [react-native-dotenv](https://github.com/goatandsheep/react-native-dotenv)
