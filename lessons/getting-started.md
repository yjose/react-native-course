---
path: "/getting-started"
title: "Getting Started"
order: "2A"
section: "Getting Started"
description: "Learn React Native With Youssouf El Azizi"
---

For getting started, follow the React Native CLI quickstart in [the environment setup](https://reactnative.dev/docs/environment-setup) guide until the section titled "Creating a New Application".

If you are on a Mac, you may want to choose iOS for this workshop, as the setup tends to be easier than Android on a Mac.

## Creating a New Application

Now that we've got all the environment prep out of the way, let's get started and create our application. Open your terminal and run:

```bash
# Make sure to remove React Native cli global install in case you already install it globally
# npm uninstall -g react-native-cli

npx react-native init Tasker
```

Here, `npx` is a command line utility that's bundled with npm (installed with Node.js) and allows you to run command line programs from npm without globally installing them. `react-native init Tasker` tells the cli tool to create a new project called Tasker. You can use a different name if you prefer.

To use Typescript you need to init your app using the official typescript template

```bash
npx react-native init Tasker --template react-native-template-typescript
```

> we rae going to use typescript for this course 😉

First, go to Tasker App folder.

```bash
cd Tasker

```

## iOS - running on a simulator

Open a new terminal window, navigate back to Tasker and run:

```bash
npx react-native run-ios
# or
yarn ios
```

This usually takes a little while to build, but once done it'll open your default simulator.

This command will :

1. build the native app
2. start the packager that inserts our JavaScript code into our app

## Android - running on an emulator

First, we need to open an emulator. iOS simulator gets opened automatically, but for Android you'll have to do it yourself. Open Android Studio, click on the "Configure" option and choose "AVD Manager". AVD stands for "Android Virtual Device" and this is the menu where you can install, delete, edit and run emulators from.

Here you can create a new virtual device if you don't have on yet. Once you have a device, double click on it to launch.

Now that the emulator is running, open a new terminal window, navigate back to AwesomeProject and run:

```bash
npx react-native run-android
# or
yarn android

```

That's it! You're now up and running on your android device.

## 👨🏻‍💻 Exercise

Create new React Native Project `Tasker` using React Native Typescript template.

Then, run the project on an emulator 📱.

### Helpful Links

- [React Native Docs](https://reactnative.dev/docs/environment-setup)
