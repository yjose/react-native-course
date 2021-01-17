---
path: "/getting-started"
title: "Getting Started"
order: "2A"
section: "Getting Started"
description: "Learn React Native With Youssouf El Azizi"
---

For getting started, follow the React Native CLI quickstart in the [environment setup](https://reactnative.dev/docs/environment-setup) guide until the section titled "Creating a New Application". If you are on a Mac, you may want to choose iOS for this workshop, as the setup tends to be easier than Android on a Mac. Once you're done, let's pick up from "Creating a New Application" together.

## Creating a New Application

Now that we've got all the environment prep out of the way, let's get started and create our application. Open your terminal and run:

```bash
# Make sure to remove React Native cli global install in case you already install it globally
# npm uninstall -g react-native-cli

npx react-native init MyApp
```

Here, `npx` is a command line utility that's bundled with npm (installed with Node.js) and allows you to run command line programs from npm without globally installing them. `react-native init AwesomeProject` tells the cli tool to create a new project called AwesomeProject. You can use a different name if you prefer.

To use Typescript you need to init your app using the official typescript template

```bash
npx react-native init MyApp --template react-native-template-typescript
```

> I recommend using typescript 😉

Now it's time to run the project! For native projects, we need to do two things:

1. start the packager that inserts our JavaScript code into our app
2. build the native app

First, lets start the packager:

```bash
cd MyApp
yarn start
```

You can omit this step if you want, since the run command does also open a new window with and starts packager automatically, but I always do it explicitly, since I like knowing that the packager is up to.

## iOS - running on a simulator

Open a new terminal window, navigate back to AwesomeProject and run:

```bash
npx react-native run-ios
# or
yarn run-ios
```

This usually takes a little while to build, but once done it'll open your default simulator.

## Android - running on an emulator

First, we need to open an emulator. iOS simulator gets opened automatically, but for Android you'll have to do it yourself. Open Android Studio, click on the "Configure" option and choose "AVD Manager". AVD stands for "Android Virtual Device" and this is the menu where you can install, delete, edit and run emulators from.

Here you can create a new virtual device if you don't have on yet. Once you have a device, double click on it to launch.

Now that the emulator is running, open a new terminal window, navigate back to AwesomeProject and run:

```bash
npx react-native run-android
# or
yarn run-android

```

That's it! You're now up and running on your android device.

More info, consult the [documentation](https://reactnative.dev/docs/environment-setup)

## 👨🏻‍💻 Exercise

Create new React Native Project using React Native Typescript template.

Then, Install deps, open the project in Vs Code and run the project on an emulator 📱.
