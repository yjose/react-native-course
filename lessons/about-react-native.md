---
path: "/about-react-native"
title: "About React Native"
order: "1C"
section: "Welcome"
description: "Learn React Native With Youssouf El Azizi"
---

## About React Native

Lets imagine you need to build a new mobile application. In Order to target 99% of smartphone users, we'll have to build two apps: one for Android and one for iOS. that's mean you'll have to manage two of everything: language, codebases, developer teams, feature sets, release schedules etc.

Hiring two developer teams is expensive, and hiring a single team that has in depth knowledge of both Android and iOS is almost impossible.

React Native is a framework for building cross-platform apps developed by Facebook for solving this problem of managing two of everything Their goal was to build a platform that enables you to have:

- fully native apps (not webviews/PWAs)
- one codebase
- one development team
- one language
- fully extensible (you should be anything that is possible without using React Native)

The platform offers a way to build mobile applications using React and JavaScript.

Instead of the `span` primitive, which we have on the web, React Native offers the `Text` primitive. If we are building an iOS app, React Native will make sure that the `Text` results with a native iOS `UIView` containing the text. If we are building an Android application, it will result with a native `TextView`.

## What makes React Native unique?

The difference between React Native and other cross-platform development solutions (for example, Cordova and PhoneGap) is that React Native doesn’t render WebViews in its code. It runs on actual, native views and components. This is one of the reasons for React Native’s spectacular success.

## How Does React Native Work?

React Native allows the development of apps consisting of JS code and native by making the bridge between an app and a target platform. When JavaScript has been running along with some native code, the React Native’s bridge system leverages the React library and transfers components’ hierarchy to the mobile device view.

![](./images/how-react-native-works.png)

In case of any updates, for example, if a user presses the button, React Native translates this case into the event that the JS can handle. And then, by relaying messages between a particular native platform and a JS codebase, the React Native bridge translates native events into ones React components can understand and respond to.

Such architecture has certain challenges. On the one hand, default components may not cover both platforms or may look very different. On the other hand, bridging architecture allows using all existing native views from platforms SDK and JS libraries.

Being single-threaded, React Native apps are easy to understand since everything that works with JavaScript on the web, will work the same way on React Native. But it’s important to consider JS specifics while developing an app architecture in order to avoid performance issues. If the architecture of the future app involves many events and a lot of data, React Native app development may not be the best option since the bridge structure may cause delays.

## Popular React Native apps

- Facebook
- Instagram
- Skype
- Tesla
- Walmart
- Discord
- Bloomberg
- UberEats

## Useful Links :

- [React Native Home Page](https://facebook.github.io/react-native/)
- [React Native Reddit Channel](https://www.reddit.com/r/reactnative/)
- [React Native NewsLatter](https://reactnative.cc/)
- [React Native Now NewsLatter](https://reactnativenow.com/)
- [React Native Twitter Account](https://twitter.com/reactnative)
- [React Native Directory](https://reactnative.directory/)
