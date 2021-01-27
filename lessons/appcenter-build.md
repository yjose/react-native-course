---
path: "/appcenter-build"
title: "Build & Release Using AppCenter"
order: "4G"
section: "Advanced"
description: "Learn React Native With Youssouf El Azizi"
---

Continuous integration is the practice of frequently committing small changes to a shared repository. This can range from once per day to multiple times per day.

Continuous deployment/delivery picks up after continuous integration. CD automates the delivery of applications to selected infrastructures (like Play Store and App Store in our case). Most teams work with multiple environments other than the production, such as development and testing environments, and CD ensures there is an automated way to push code changes to them.

## CI/CD Workflow

One of the Main Advantages of using React Native is that you can build one app that works on both ios and android platforms, same thing for CI/CD we can setup App Center for automatic builds and also ensuring smooth delivery to the App Store/Play Store.
For CI we will use the same [GIT Workflow](https://guides.github.com/introduction/flow/), and we will create two main branches, a Develop and release branches, each time you add a new feature or you fix a bug it should be tested on dev branch and each time you want to release a new version you can do it using the release branch. If this version is stable of course you can make a PR to master so you can save the stable version on the master.

\*\* You don't need to follow the same workflow, it depends on your needs.

After Building the app you always use App Center to publish it on the App Store or Play store.

## Setup App Center?

AppCenter lets us continuously build, test, release, and monitor apps for every platform, we will use it to automate the build and release our app, to do that we need to follow a workflow in order to get everything works as it should.

2. Connect your project to AppCenter: sign up for a new account on the [App Center website](https://appcenter.ms/), and create a new Organization, inside this organization you should create two applications:<br />
   `your_app_name_android`<br />
   `your_app_name_ios`<br />
   \*OS: android/ios, Platform: React Native

3. Once you create each app, it will show you a guide on how to add AppCenter to your app. Note that you should follow the guidelines for both android and ios. if you face any issue while installing dependencies you can check the [App Center Documentation](https://docs.microsoft.com/en-us/appcenter/sdk/getting-started/react-native)

4. Go back now to App Center and click on the Build menu on the sidebar so you can connect your code repo.

5. From the branches list, click on the config icon to configure the build for the targeted branch, the build configuration screen will have the following options:
   - Project: select package.json (it should be selected by default).
   - Shared Scheme(ios): project schema.
   - Xcode version(id): XCode version you want use to build the app.
   - Node.js version: Node Js version you want to use.
   - Build scripts: check the last section for more information.
   - Build frequency: choose to build the app each time you push something to this branch or choose manually
   - Automatically increment build number(ios): set On
   - Build Android App Bundle(android): set On, cause we should use the [app bundle(.aab)](https://developer.android.com/guide/app-bundle) to publish the app.
   - Automatically increment version code(android): set On
   - Run unit tests: set On, if you want to run unit tests
   - Environment variables: Add Android singing Environmental variables `KEYSTORE_PASSWORD` , `KEY_ALIAS` and `KEY_PASSWORD` from To store env variables [More infos](https://docs.microsoft.com/en-us/appcenter/build/custom/variables/)
   - Sign builds: on, to sign the app(next step).
   - Test on a real device: this will let you test the app on a real device(a launch test) to be sure it works.
   - Distribute builds: on, only for collaborators group(usually developers ) as we need to make sure every think work as expected before sending the APK to testers.
     then you need to upload/config the certificates from ios and the Keystore for android, I will show you how to do it.<br />
     for Debug mode this configuration is enough for android and you can save & build the app, but the bad news is that you can't generate an IPA file for ios without an [Apple Developer Program member](https://developer.apple.com/programs/enroll/), this is what we will do next.
6. [sign build for Android](https://reactnative.dev/docs/signed-apk-android.html):

- You need a Keystore file to do that you need to execute the following command on your terminal:

```bash
keytool -genkey -v -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000
```

- Once the Keystore file is generated, upload it to App Center and enter the Keystore password, key alias, and key password.

6. [Sign builds for iOS](https://docs.microsoft.com/en-us/appcenter/build/ios/code-signing), the bad news here is that you won't be able to install or run the .ipa file if you're not an [Apple Developer Program Member](https://developer.apple.com/programs/enroll/). if you already have a member account:

- generate an [iOS - Creating an Ad Hoc Distribution Provisioning Profile](https://support.magplus.com/hc/en-us/articles/204270188-iOS-Creating-an-Ad-Hoc-Distribution-Provisioning-Profile)
- generate an [iOS - Creating a Distribution Certificate and .p12 File](https://support.magplus.com/hc/en-us/articles/203808748-iOS-Creating-a-Distribution-Certificate-and-p12-File)
- after generating the P12 and Provisioning Profile upload both on App Center (ios app build configurations).

## Custom build scripts

You can add up to three custom build steps that run at [pre-defined](https://docs.microsoft.com/en-us/appcenter/build/custom/scripts/) stages during build time, these are Bash scripts which can be executed throughout the lifecycle of the entire build, all you have to do is create any of these files inside the root of your project directory (same level as your package.json file):

- post-clone - executed right after your code repo has been cloned `appcenter-post-clone.sh`.
- pre-build - executed right before App Center begins the build process for your app. This is usually right after the dependencies for your project are installed `appcenter-pre-build.sh`.
- post-build - executed right after your app is built `appcenter-post-build.sh`.

You can use pre-defined, custom, or in-script environment variables to help write your Build scripts, [for more info](https://docs.microsoft.com/en-us/appcenter/build/custom/variables/).

## Distribute your app to stores from App Center

You can also Distribute your app directly to stores from App Center, by connecting it with Apple App Store and Google Play Store:

1. [App Store and TestFlight Distribution](https://docs.microsoft.com/en-us/appcenter/distribution/stores/apple)
2. [Publish to Google Play Store](https://docs.microsoft.com/en-us/appcenter/distribution/stores/googleplay)
