---
path: "/splash-screen-app-icon"
title: "Splash Screen & App Icon"
order: "4F"
section: "Advanced"
description: "Learn React Native With Youssouf El Azizi"
---

## App Icon

I will introduce how to make an App icon via [react Native Make](https://github.com/bamlab/react-native-make) library.

1. Install react-native-make

```bash
yarn add @bam.tech/react-native-make -D
```

That’s all. We are ready to use react-native-make.

2. When you use react-native-make to create the App icon, you need a 1024x1024 px size png ( Make sure not to use transparent images as you will have some issues with IOS) image.

If the file is ready, execute the command below to make the App icon.

```bash
yarn react-native set-icon --path [path-to-image] --background color
```

## Splash Screen

To create an app splash screen, we Have two option :

- [React Native Splash Screen ](https://github.com/crazycodeboy/react-native-splash-screen)
- [React Native bootsplash](https://github.com/zoontek/react-native-bootsplash)

we are going to choose to React Native bootsplash over the Splash screen Because :

- react-native-splash-screen encourages you to display an image over your application, react-native-bootsplash way-to-go is to design your launch screen using platforms tools (Xcode layout editor and Android drawable resource).

- Instead of displaying the launch screen over the main UIView / Activity, it will be displayed inside it. This prevents "jump" during transition (like in the example: horizontal & vertical centering using iOS auto layout or android gravity params will match perfectly the mounted component which uses { alignItems: "center"; justifyContent: "center" } to center its logo).

- It should not prevent you from seeing red screen errors.

- Hiding the launch screen is configurable: fade it out with a custom duration or hide it without any animation at all (no fade needed if you want to animate it out!).

=> [Setup Splash Screen](https://github.com/zoontek/react-native-bootsplash#setup)

👉 https://github.com/yjose/Tasker/commit/1a14fbe353ce1a5f5e4d372d335d606e1a15f8e1

### Helpful Links

- [React Native Make](https://github.com/bamlab/react-native-make)
- [React Native BootSplash](https://github.com/zoontek/react-native-bootsplash#setup)
