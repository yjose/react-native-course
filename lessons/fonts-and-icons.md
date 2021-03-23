---
path: "/fonts-and-icons"
title: "Fonts & Icons"
order: "3D"
section: "Basic"
description: "Learn React Native With Youssouf El Azizi"
---

### Fonts

Adding Custom Fonts to React Native App is quite easy and only needs a few steps.

1. Go [Google Fonts](https://fonts.google.com/), select styles and download your custom font: [Inter](https://fonts.google.com/specimen/Inter?query=Inter&sidebar.open=true&selection.family=Inter:wght@400;700)

2. Create a fonts folder `assets/fonts` in the root of your project and paste downloaded fonts files in it.

3. Copy and the paste the code below into your `react-native.config.js` file

```js
module.exports = {
  project: {
    ios: {},
    android: {},
  },
  assets: ["./assets/fonts/"],
};
```

4. run `yarn react-native link` from the root of the project.
5. rebuild your app `yarn ios` or `yarn android`

Voila!. You now have custom fonts set up.

```tsx
const styles = StyleSheet.create({
  title: {
    fontFamily: "Inter",
    fontWeight: "bold",
    //or
    fontFamily: "Inter-Bold",
  },
});
```

👉 https://github.com/yjose/Tasker/commit/c8e9bc6dc3beea92ab696c19debc7e32784da0de

### Icons

For a long time, I used `react-native-vector-icons` to create my custom icons assets, this approach comes with some difficulty as I always find myself regenerating a new font whenever our designer changes an icon in the design system. Also, this approach has some limits on supporting some SVG properties.

Using [`react-native-svg`](https://github.com/react-native-svg/react-native-svg) will fix most of those issues, also I found it very simple to add new icons as Most of the design tools Nowadays export the SVG icon as React Native component.

1. install `react-native-svg`

```bash
yarn add react-native-svg

## on IOS only ( need to install native deps )
yarn setup:ios

## rebuild app
yarn ios

```

2. Install [SVG to JSX Figma plugin](https://www.figma.com/community/plugin/749818562498396194/SVG-to-JSX) to start exporting your Figma icons as React Native Component.

```tsx
import * as React from "react";
import Svg, { SvgProps, Path } from "react-native-svg";

export function Check(props: SvgProps) {
  return (
    <Svg width={28} height={28} fill="none" {...props}>
      <Path
        fillRule="evenodd"
        clipRule="evenodd"
        d="M28 14c0 7.732-6.268 14-14 14S0 21.732 0 14 6.268 0 14 0s14 6.268 14 14zm-14.893 2.053a1 1 0 01-1.414 0l-2.556-2.556a1 1 0 00-1.414 1.415l3.899 3.898a1 1 0 001.482.075l7.778-7.778a1 1 0 10-1.414-1.414l-6.36 6.36z"
        fill="#006CFF"
      />
    </Svg>
  );
}
```

👉 https://github.com/yjose/Tasker/commit/16d4e1a1d9029ba365d122a199687dd820a2d0a3
