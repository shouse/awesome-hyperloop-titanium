https://github.com/hyperloop-modules/ti.mapbox/blob/master/Podfile

# Awesome Titanium Hyperloop: iOS

[![Appcelerator Titanium](http://www-static.appcelerator.com/badges/titanium-git-badge-sq.png)](http://appcelerator.com/titanium/)

## Why this README.md?
 I'd like to gather as much good information on Hyperloop and iOS as possible.  
 There are several ways that you can use Hyperloop for iOS developement
 - Reference Apple Frameworks
 - Import Cocoapods
 - Reference custom frameworks

General Information
- [iOS Hyperloop Programming Guide](https://wiki.appcelerator.org/display/guides2/iOS+Hyperloop+Programming+Guide) has information on running a demo application specifically for iOS and you can learn how to use Hyperloop in your own project.
- [User Interface Builder: XIB](https://github.com/appcelerator/hyperloop-examples/blob/master/app/controllers/ios/xib.js) - Using Interface Builder via XIBs

## Working with Apple's Frameworks
Many of the basic Hyperloop examples are just this - extending built in frameworks.  You don't have to load any outside libraries to access this.

## Working with 3rd Party Frameworks
You can include 3rd Party Frameworks into your project.

## Working with Custom Frameworks
This is currently pretty cutting edge for Titanium.  Support has existed for a decent amount of time, and the support keeps picking up speed.

## Working with Cocoapods
Being able to access dependency management platforms really is essential to modern development.  Don't reinvent the wheel.
 Hyperloop largely covers this, though currently it is not as intuitive or automatic as I'd like
 
 Up front there are some limitations: you can only support ObjectiveC pods.  
 Well, pods that expose an ObjectiveC interface.  
 They can reference Swift frameworks, but I still don't have that figured out 100%.
 Additionally you will have to pay attention specifically to the Podfile and understand some nuances around it.  
 If you are already familiar with pods it won't be a problem, but if you are not it makes it difficult to attribute blame 
 to why your project isn't working like you expected
 
- [Using the Podfile](https://guides.cocoapods.org/using/the-podfile.html) - Cocoapods.org
- [Cocopods App](http://cocoapods.org/app) - Edit your Podfile in a custom environment.                                             
    Have easy access to running pod install and pod update on your projects. It also supports running every CocoaPods command via a hosted ruby environment.
    We’re just getting started with this app, want to help out and make contributions to hundreds of thousands of developer’s work flow? Get involved.

## Working with Cocoapods AND 3rd Party Frameworks
When I figure this out I'll let you know!

## List of iOS Modules
- [Ti.MTTCircularSlider by nazrdogan](https://github.com/nazrdogan/Ti.MTTCircularSlider) - Hyperloop module for https://github.com/MTT-IOS/MTTCircularSlider
- [Ti.FSCalendar by nazrdogan](https://github.com/nazrdogan/Ti.FSCalendar) - Hyperloop module for https://github.com/WenchaoD/FSCalendar
- [Ti.DrawView by nazrdogan](https://github.com/nazrdogan/Ti.DrawView) - Draw on your screen on iOS
- [Ti.IRLDocumentScanner by nazrdogan](https://github.com/nazrdogan/Ti.IRLDocumentScanner) - Hyperloop module for https://github.com/charlymr/IRLDocumentScanner
- [Ti.HCSStarRatingView by nazrdogan](https://github.com/nazrdogan/Ti.HCSStarRatingView) - Hyperloop module for https://github.com/hsousa/HCSStarRatingView

- [Ti.Firebase by LoopModules](https://github.com/loop-modules/Ti.Firebase) - Ti.Firebase is an iOS Hyperloop wrapper of the Firebase SDK.
- [Ti.UICollectionView by LoopModules](https://github.com/loop-modules/Ti.UICollectionView) - Ti.UICollectionView is an iOS Hyperloop wrapper of the native UICollectionView component.
- [Ti.EaIntroView by LoopModules](https://github.com/loop-modules/Ti.EaIntroView) - Ti.EaIntroView is an iOS Hyperloop wrapper of the EAIntroView library. Ti.EaIntroView provides a highly customizable solution for introduction views.
- [Ti.speech by LoopModules](https://github.com/hyperloop-modules/ti.speech) - Use the iOS 10 SFSpeechRecognizer API in JavaScript with Appcelerator Hyperloop.
- [Ti.mapbox by LoopModules](https://github.com/hyperloop-modules/ti.mapbox) - Use the MapBox SDK with Axway Hyperloop
- [Ti.cloudsharing by LoopModules](https://github.com/hyperloop-modules/ti.cloudsharing) - Use the UICloudSharingController with Hyperloop in Titanium
- [Ti.snackbar by LoopModules](https://github.com/hyperloop-modules/ti.snackbar) - Use the Android Snackbar in Appcelerator Titanium.

- [Ti.GoogleVR by LoopModules](https://github.com/loop-modules/Ti.GoogleVR) - Ti.GoogleVR is an iOS Hyperloop wrapper of the Google VR SDK. Ti.GoogleVR provides an easy way develop your own virtual reality experience using what Google best provides.
- [Ti.Estimote by LoopModules](https://github.com/loop-modules/Ti.Estimote) - Ti.Estimote is an iOS Hyperloop wrapper of the Estimote SDK.
- [Ti.Oauth by LoopModules](https://github.com/loop-modules/Ti.Oauth) - This HyperLoop module allows you to use the awesome OAuth.IO SDK for iOS.
- [Ti.WebView by LoopModules](https://github.com/loop-modules/Ti.WebView) - Ti.WebView is an iOS Hyperloop wrapper for two native iOS components: WKWebView, SFSafariViewController
- [Ti.Spinkit by LoopModules](https://github.com/loop-modules/Ti.Spinkit) - Ti.SpinKit is an iOS Hyperloop wrapper of the SpinKit-ObjC library.

- [Ti.Parallax by trkfabi](https://github.com/trkfabi/Ti.Parallax/blob/master/app/controllers/index.js) - Parallax effect with Titanium using Hyperloop. iOS only.

- [Ti.reCAPTCHA by hansemannn](https://github.com/hansemannn/titanium-recaptcha) - Use the native reCAPTCHA API in Appcelerator Titanium (currently Android-only)
- [AppC Github Client by AppC Dev Relations](https://github.com/appcelerator-developer-relations/appc-github-client) - Dashboard used to monitor Github organizations, repositories and more!



### Podfile Examples
- [Ti.mapbox](https://github.com/hyperloop-modules/ti.mapbox) - Use the MapBox SDK with Axway Hyperloop
- [Ti.MTTCircularSlider](https://github.com/nazrdogan/Ti.MTTCircularSlider/blob/master/Podfile)
- [Ti.FSCalendar](https://github.com/nazrdogan/Ti.FSCalendar/blob/master/Podfile)
- [Ti.DrawView](https://github.com/nazrdogan/Ti.DrawView/blob/master/Podfile)
- [Ti.IRLDocumentScanner](https://github.com/nazrdogan/Ti.IRLDocumentScanner/blob/master/Podfile)
- [Ti.HCSStarRatingView](https://github.com/nazrdogan/Ti.HCSStarRatingView/blob/master/Podfile)
- [Ti.Firebase](https://github.com/loop-modules/Ti.Firebase/blob/master/Podfile) - [3rd Party Framework - appc.js](https://github.com/loop-modules/Ti.Firebase/blob/master/appc.js)
- [Ti.EaIntroView](https://github.com/loop-modules/Ti.EaIntroView/blob/master/Podfile)
- [Ti.GoogleVR](https://github.com/loop-modules/Ti.GoogleVR/blob/master/Podfile) - [3rd Party Framework - appc.js](https://github.com/loop-modules/Ti.GoogleVR/blob/master/appc.js)
- [Ti.Estimote](https://github.com/loop-modules/Ti.Estimote/blob/master/Podfile)
- [Ti.Spinkit](https://github.com/loop-modules/Ti.Spinkit/blob/master/Podfile)

 