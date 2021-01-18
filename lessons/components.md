---
path: "/components"
title: "Components"
order: "3A"
section: "Basic"
description: "Learn React Native With Youssouf El Azizi"
---

If you're already familiar with React then you've got a head start, lucky you! Before we dive into React Native, let's start by looking at this "hello world" React component:

```js
import React from "react";

const App = () => {
  return <div>Hello, world!</div>;
};

export default App;
```

This is a minimal React component. If you're used React before, this will be familiar to you. If not, let's talk through what's going on here.

React uses what they call JSX as syntax sugar for displaying components. JSX stands for "JavaScript and XML", and although XML is quite dated, it really works out for React, because the XML syntax looks very similar to HTML! The bonus is that we can do JavaScript around it.

At the top of the file we have an import statement - import React from 'react'; - though React is not used in the file. This is because React is needed for the JSX. As a rule of thumb, if the file includes any components with braces (<>) you'll need to import React.

Now let's look at a corresponding React Native component:

```js
import React from "react";
import { View, Text } from "react-native";

const App = () => {
  return (
    <View>
      <Text>Hello, world!</Text>
    </View>
  );
};

export default App;
```

There are a couple of important differences here. We can't use `div`, `span`, `p` or other html elements in React Native. Instead, we have special native components. The notable difference is that you have to import these components from react-native rather than just having them built into jsx.

React Native has many Core Components for everything from form controls to activity indicators. You can find them all [documented in the API section](https://reactnative.dev/components-and-apis). You will mostly work with the following Core Components:

| React Native UI Component | Android View   | iOS View         | Web Analog               | Description                                                                                           |
| ------------------------- | -------------- | ---------------- | ------------------------ | ----------------------------------------------------------------------------------------------------- |
| `<View>`                  | `<ViewGroup>`  | `<UIView>`       | A non-scrollling `<div>` | A container that supports layout with flexbox, style, some touch handling, and accessibility controls |
| `<Text>`                  | `<TextView>`   | `<UITextView>`   | `<p>`                    | Displays, styles, and nests strings of text and even handles touch events                             |
| `<Image>`                 | `<ImageView>`  | `<UIImageView>`  | `<img>`                  | Displays different types of images                                                                    |
| `<ScrollView>`            | `<ScrollView>` | `<UIScrollView>` | `<div>`                  | A generic scrolling container that can contain multiple components and views                          |
| `<TextInput>`             | `<EditText>`   | `<UITextField>`  | `<input type="text">`    | Allows the user to enter text                                                                         |

## 👨🏻‍💻 Exercise

- Open `App.ts`. Then, create a `View` and a `Text` with "Hello, world"

- Create a `src/components` folder and create a `Button` component that accepts an `onPress` and `label` prop. Use the `Pressable` and `Text` components to accomplish this.

- Import your custom button component and render 2 buttons with different labels inside `App.ts`. every button should print a message to our terminal on click.

### Helpful links

[React Native Components API](https://reactnative.dev/components-and-apis)
