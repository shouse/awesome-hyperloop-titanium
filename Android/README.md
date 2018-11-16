# Awesome Titanium Hyperloop: Android
[![Appcelerator Titanium](http://www-static.appcelerator.com/badges/titanium-git-badge-sq.png)](http://appcelerator.com/titanium/)
![Hyperloop Enabled](https://img.shields.io/badge/hyperloop-enabled-red.svg)&nbsp;
![platform](https://img.shields.io/badge/platform-android-green.svg)&nbsp;
[![License MIT](https://img.shields.io/badge/license-MIT-green.svg?style=flat)](https://writing.kemitchell.com/2016/09/21/MIT-License-Line-by-Line.html)&nbsp;

## Why this README.md?
 I'd like to gather as much good information on Hyperloop and Android as possible.  
 There are several ways that you can use Hyperloop for Android developement
 - Reference Google Frameworks already on device
 - Use AARs and JARs

[Android Hyperloop Programming Guide](https://wiki.appcelerator.org/display/guides2/Android+Hyperloop+Programming+Guide)
has information on running a demo application specifically for Android and you can learn how to use Hyperloop in your own project.

## List of Android Modules
| Name | Description |
|-|-|
|[Pattern Lock View](https://github.com/prashantsaini1/hyperloop-android-pattern-lock)| Create the native Android PatternLock view based on this library [PatternLockView](https://github.com/aritraroy/PatternLockView)|
| [Ti.AndroidCharts](https://github.com/loop-modules/Ti.AndroidCharts) | This HyperLoop module allows you to use highly customizable Charts with the MPAndroidChart library: https://github.com/PhilJay/MPAndroidChart. This module was originally posted on LoopModules: https://loopmodules.com/downloads/ti-androidcharts/ |
|[Ti.Reprint](https://github.com/loop-modules/Ti.Reprint)| This HyperLoop module allows you to implement fingerprint recognition in your Android app|
| [Ti.FAB](https://github.com/loop-modules/Ti.FAB) |Ti.FAB is an Android Hyperloop wrapper of the native Floating Action Button component. A Floating Action Button represents the primary action in an application.|
| [Ti.AndroidViewAnimations](https://github.com/loop-modules/Ti.AndroidViewAnimations) |Ti.AndroidViewAnimations is an Android Hyperloop wrapper of the AndroidViewAnimations library. It provides a wide range of different animations that can be applied to your Titanium components.|
| [Ti.CalendarView](https://github.com/m1ga/Ti.CalendarView) |Axway Hyperloop Calendar View for Android|
| [Youtube View](https://github.com/m1ga/hyperloop.youtube) | Youtube View|
| [Parked Text View](https://github.com/m1ga/hyperloop.parkedText)| Textfield with static and variable text|
| [Scratch View](https://github.com/m1ga/hyperloop.scratchView)| A scratch card module that reveals the image below when you scratch/swipe away a color |
| [Big Image View](https://github.com/m1ga/hyperloop.bigimages)| ImageView for big images that supports zoom and drag |
| [Audio Recorder](https://github.com/m1ga/hyperloop.audiorecorder)| Record void ui element|
| [Text 2 Speech / Speech to text](https://github.com/m1ga/hyperloop.speech)| Text recognition and text to speech |

### Modules

**Cross-Platform (Android and iOS)**

| Name | Description |
| - | - |
| [Ti.hockeyapp](https://github.com/hyperloop-modules/ti.hockeyapp)|Hyperloop-based version of HockeyApp for both Android and iOS|
| [Ti.Firebase](https://github.com/hansemannn/titanium-firebase)|This project will contain all Firebase-related modules for Analytics, Cloud-Messaging, Authentication, Firestore etc.|
| [localytics-hyperloop](https://github.com/centrevilletech/localytics-hyperloop)|This project provides a demo app and library for using the Localytics service in iOS and Android.|

### Other Code Examples
 - [Official Github example](https://github.com/appcelerator/hyperloop-examples) - Hyperloop Examples
>The following application demonstrates direct native API access using Appcelerator Hyperloop.
 - [Imaging Workshops ToDo](https://github.com/appcdev/imagine-workshops-todo/tree/hyperloop?files=1) - Todo Demo App
- [titanium-auth-session.js](https://gist.github.com/hansemannn/71b6181557ec0f6024e29c642dbe52e3) - Use Axway Hyperloop to perform OAuth-sessions with the iOS 11+ API "SFAuthenticationSession"

## Working with Google's Frameworks
Many of the basic Hyperloop examples are just this - extending built in frameworks.  You don't have to load any outside libraries to access this.

## Working with 3rd Party Frameworks (JARs and AARs)
You can include 3rd Party libraries into your project.  
Just put your .jar and .aar files in /app/platform/android/ and require them in your controllers.

## Can I get some Gradle in here?
Long story short, I have heard no talk of Gradle integration.  This would be a top 3 wish of mine for Hyperloop!  
Do you have any idea of how to make it work?  Let's toss around some ideas!

### More Examples
- **Submit a PR with some more examples!  Do it!**
