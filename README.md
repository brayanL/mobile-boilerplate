mobile-boilerplate
===

# Modules

## Expo

Expo is an important discussion point for React Native, as it does provide a nice starting point and it is the initial method recommended in the React Native Getting Started guide.

Overall I recommend avoiding Expo for long-term projects. It can be good for proof-of-concepts, or some standard CRUD apps. But it does have disadvantages, and while you can eject, you will lose some capabilities like push notifications and OTA updates you will need to find a different solution for.

Make sure to read up about limitations like inability to do background tasks (e.g. audio, GPS).

### Good references

[Understanding Expo for React Native – Hacker Noon](https://hackernoon.com/understanding-expo-for-react-native-7bf23054bbcd)

### Recommendation for using Expo

- Use expo for apps that will be standard, little difference from traditional webapps
- Be slightly cautious using expo for geolocation apps that need backgrounding. It isn't supported yet, but support is slated for SDK31 possibly [Background location tracking | Feature Requests | Expo](https://expo.canny.io/feature-requests/p/background-location-tracking)
- Be more cautious using expo for audio, as backgrounding support is in progress but has seen little progress or updates [Audio playback in background | Feature Requests | Expo](https://expo.canny.io/feature-requests/p/audio-playback-in-background) / [RFC: Audio playback in background · Issue #1195 · expo/expo · GitHub](https://github.com/expo/expo/issues/1195)
- Be cautious otherwise for anything that needs background support of your own. [Background tasks support | Feature Requests | Expo](https://expo.canny.io/feature-requests/p/background-tasks-support)
- Be cautious if the app is sensitive in nature, as Expo builds will be public on S3
- You can always eject, but be wary about losing push notification support and losing the OTA update capabilities.

### Alternatives to Expo

- Ignite has a great set of boilerplates to generate, and tools to add new functionality
- Microsoft App Center or CodePush are excellent tools for replacing OTA capabilities

### Why use Expo

[Frequently Asked Questions - Expo Documentation](https://docs.expo.io/versions/latest/introduction/faq)

[Difference between react-native-init and create-react-native-app · Issue #516 · react-community/create-react-native-app · GitHub](https://github.com/react-community/create-react-native-app/issues/516)

### Good list of pros and cons from Benzer1406

[Understanding Expo for React Native – Hacker Noon](https://hackernoon.com/understanding-expo-for-react-native-7bf23054bbcd)

- Handles config and build steps for native for you, just worry about JS
- Easy developer setup. Running an expo app seamlessly loads the app on your phone, no install process.
- Better deployment. Auto update people who have already installed.
- Ability for other people to quickly install development versions of the app, they just install Expo on their phones and open a URL.
- Easy SDK for camera, accelerometer, maps, location tracking, analytics, etc
- Easy upgrades of React Native, though it might slightly lag behind
- Push notifications are built-in, no certificate setup needed [Is Expo Worth It? : reactnative](https://www.reddit.com/r/reactnative/comments/6artym/is_expo_worth_it/)

### Why not to use Expo

- You can't create your own native modules, unless you eject
- You can't reuse existing native module solutions, such as Airbnb's map component. [React-native first impressions: Expo vs. Native – paulsc – Medium](https://medium.com/@paulsc/react-native-first-impressions-expo-vs-native-9565cce44c92) - you are stuck with the Expo equivalent, or JS only solutions. This might not be as limiting, as 213 / 351 components listed here support Expo [Native Directory](http://native.directory/downloads)
- Publishing puts a public copy on Amazon CloudFront
- Delay in updates to latest React Native version
- [How I ditched Expo for pure React Native – gitconnected | Become a Better Developer](https://levelup.gitconnected.com/how-i-ditched-expo-for-pure-react-native-fc0375361307) - **No background geolocation** (Tracking the location of the device even if the app is not in the foreground): 
  - [Background location tracking | Feature Requests | Expo](https://expo.canny.io/feature-requests/p/background-location-tracking)
  - This may be in progress though, slated for SDK31?
  - [RFC: Audio playback in background · Issue #1195 · expo/expo · GitHub](https://github.com/expo/expo/issues/1195)
- There is apparently also no background audio support, which would definitely hinder a podcasting app [Expo vs React Native CLI: A Guide to Bootstrapping New React Native Apps](https://levelup.gitconnected.com/expo-vs-react-native-cli-a-guide-to-bootstrapping-new-react-native-apps-6f0fcafee58f)
- Missing features (a year ago at least) like in-app purchases, and admob [Is Expo Worth It? : reactnative](https://www.reddit.com/r/reactnative/comments/6artym/is_expo_worth_it/)
- In general, you can't use anything that requires *$ react-native link*


### Ejecting Expo

[Ejecting to ExpoKit - Expo Documentation](https://docs.expo.io/versions/latest/expokit/eject)

- Still dependent on ExpoKit
- Have to build native yourself
- Push notifications will stop working, have to control them yourself
- You still get some advantages from Expo, like automatic updates outside the store as long as your native code hasn't changed.


### Expo for Audio

[Experimenting with React Native & Expo’s Audio API – Hacker Noon](https://hackernoon.com/experimenting-with-react-native-expos-audio-api-6f13eeb729be)

- Good except for not supporting backgrounding yet
- Open sourced: [GitHub - GetStream/react-native-audio-player](https://github.com/getstream/react-native-audio-player)

- No real progress yet on backgrounding [RFC: Audio playback in background · Issue #1195 · expo/expo · GitHub](https://github.com/expo/expo/issues/1195)

---

## Components

### Component Libraries

[NativeBase | Essential cross-platform UI components for React Native](https://nativebase.io/)

Most popular cross platform component library, reusable components that usually use the same code between platforms.

[React Native Community · GitHub](https://github.com/react-native-community)

React Native base components from the community.

[GitHub - Flipkart/recyclerlistview: High performance listview for React Native and web!](https://github.com/Flipkart/recyclerlistview)

Most performance in React Native is as good as native or web, except for long list views. This helped in one company's case.

### Resources

[Native Directory](http://native.directory/)

Browse a directory of React Native components

[GitHub - oblador/react-native-vector-icons](https://github.com/oblador/react-native-vector-icons)

Customizable Icons for React Native with support for NavBar/TabBar/ToolbarAndroid, image source and full styling.

### Libraries

[GitHub - knowbody/react-native-platform-stylesheet: React Native Platform Specific Stylesheet](https://github.com/knowbody/react-native-platform-stylesheet)

Apply separate styling for iOS vs Android in your stylesheets


### Boilerplate

[Ignite 2.0 Has Landed!](https://infinite.red/ignite)

Boilerplate generator for React Native. Includes a lot of functionality. Different generators to choose from, some supported by Infinite Red, others community contributed.

React Native version was maybe 6 months old. Not too bad for a generator, but `react-native init` might be better for larger projects where we want to get things right. React Native isn't as easy to upgrade to new versions as React.

[React Native Seed](https://reactnativeseed.com/)

Another nice boilerplate, from the team that makes NativeBase. Maybe more slim than Ignite. React version was a little older than Ignite, so Ignite is recommended.

Testing
---
[React Native · Enzyme](https://airbnb.io/enzyme/docs/guides/react-native.html)

Allow rendering of components in unit tests. No E2E UI/PhantomJS/Puppeteer required.

Use Enzyme with react-native-mock (or react-native-mock-renderer), which fake the native components to treat it as web DOM, making it testable.

[Testing React Native Apps · Jest](https://jestjs.io/docs/en/tutorial-react-native)

Jest is the go-to test runner / assertion library for React front-ends, and React Native is no exception. Generally a great user experience and little setup required, though Mocha/Chai/Sinon are a little more performant and have their own benefits more for backend dev.

[GitHub - wix/Detox: Gray Box End-to-End Testing and Automation Framework for Mobile Apps](https://github.com/wix/Detox)

End-to-End testing framework I saw mentioned several times in researching React Native E2E frameworks.

[GitHub - pixielabs/cavy: An integration test framework for React Native.](https://github.com/pixielabs/cavy)

End-to-End testing framework specifically made for React Native.

[Appium: Mobile App Automation Made Awesome.](http://appium.io/)

End-to-End testing framework, definitely a popular choice I've heard about many times.

### CI/CD / Builds

#### Reference
[Understanding React Native Deployments – React Native Training – Medium](https://medium.com/react-native-training/understanding-react-native-deployments-6e54157920b7)

#### Tools
[Shipping React Native apps with Fastlane | Carlos Cuesta | Blog](https://carloscuesta.me/blog/shipping-react-native-apps-with-fastlane/)

Fastlane - Automate store release process: code signing, app builds, etc. Free tool. Pushes updates to the mobile stores. It isn't OTA like CodePush, but some things can't be pushed to the store OTA, like native code and app metadata.

[Visual Studio App Center | iOS, Android, Xamarin & React Native](https://www.appcenter.ms/)

CodePush, a free part of App Center. Pushes OTA (Over The Air) updates, similar to Expo but without being restricted by Expo.

[AppHub: Build better apps, faster.](https://apphub.io/)

Can use free open source version as well, or pay for their hosted version

[Bitrise | Bitrise - Mobile Continuous Integration and Delivery - iOS & Android Build Automation](https://www.bitrise.io/)

CI/CD pipeline specifically geared for mobile


### Cross Platform

[GitHub - necolas/react-native-web: React Native for Web](https://github.com/necolas/react-native-web)

Reuse your React Native sites in web-based solutions.

[GitHub - vincentriemer/react-native-dom: An experimental, comprehensive port of React Native to the web.](https://github.com/vincentriemer/react-native-dom)

Alternative to react-native-web

[Proton Native - React Native for the desktop, cross compatible](https://proton-native.js.org/#/)

Reuse your React Native sites on the desktop.

# Usage

## Getting Started

Follow `Build Projects with Native Code` here: https://facebook.github.io/react-native/docs/getting-started.html

You will need your phone connected via USB, or to use an emulator in e.g. Android Studio.

## General commands

`react-native run-android`

Run the solution on your phone or a connected emulator. USB is required for your phone (unless you are using an Expo app).

## Tips & Tricks

### Access developer menu on your phone without shaking

Usually you have to shake your phone to get to the developer menu. Not always ideal.

You can use `adb` instead to send a shake event to the phone, and 

```$ adb shell input keyevent 82; and adb shell input keyevent 66; and adb shell input keyevent 66```

## Issues

[error: bundling failed: Error: Unable to resolve module `./../react-transform-hmr/lib/index.js` · Issue #21490 · facebook/react-native · GitHub](https://github.com/facebook/react-native/issues/21490)

If you see this error:

`Unable to resolve module `./../react-transform-hmr/lib/index.js``

Follow these steps, especially the `react-native start  --reset-cache` seems to help:

```
# Clean cache
rm -rf $TMPDIR/react-*; rm -rf $TMPDIR/haste-*; rm -rf $TMPDIR/metro-*; watchman watch-del-all

# Open a new tab and Start Metro Bundler directly from the project folder
react-native start  --reset-cache

# Now run `react-native run-android` or `react-native run-ios
```