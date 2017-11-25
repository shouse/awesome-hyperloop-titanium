# Awesome Titanium Hyperloop: iOS

[![Appcelerator Titanium](http://www-static.appcelerator.com/badges/titanium-git-badge-sq.png)](http://appcelerator.com/titanium/)
![Hyperloop Enabled](https://img.shields.io/badge/hyperloop-enabled-red.svg)&nbsp;
![platform](https://img.shields.io/badge/platform-ios-blue.svg)&nbsp;
[![License MIT](https://img.shields.io/badge/license-MIT-green.svg?style=flat)](https://writing.kemitchell.com/2016/09/21/MIT-License-Line-by-Line.html)&nbsp;

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
Support has existed for a decent amount of time, but it appears to finally be picking up speed.

### Hyperloop Version >= 2.2
The appc.js magic has been moved into the CLI core, and doesn't require all of the shenannigans it did before.
To access **3rd party frameworks**, 
- Copy the ```frameworkName.framework``` folder into ```[APP_ROOT]/app/platform/ios```
- If the folder doesn't exist, create it.
- Access the framework in your controller by : ```var myFavFramework = require('frameworkHeader');```
- You might have to try to play around with the exact require statement.  See some examples of other HyperLoop require statements.
 
 **Pitfalls**  
- There's a few that I will add here soon


### Hyperloop Version <= 2.1

Prior to Hyperloop 2.2 you had to pay more attention to a file called `appc.js` which has now been automated and deprecated.  
  It appears there's other functions it handles, serving as a [unified metadata file](https://github.com/appcelerator/cspec-appc-appc.js/tree/master).
  So, don't currently take my word for what the full functionality of this file is.
  
Here's an example:
```
hyperloop: {
    ios: {
        xcodebuild: {
            flags: {
                GCC_PREPROCESSOR_DEFINITIONS: 'foo=bar'
            },
            frameworks: [
                'StoreKit'
            ]
        },
        thirdparty: {
            'MyFramework': {
                // these can be an array or string
                source: ['src'],
                header: 'src',
                resource: 'src'
            }
        }
    }
}
```
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
Cocoapods have have dependencies for 3rd party frameworks.  You'll see this used in a Podfile: `!use_frameworks`.  
Frameworks are already handled [for native modules](https://github.com/appcelerator-modules/hook-swift-frameworks) 
But a different approach is required.  

If you are using a version of Titanium SDK before 6.2.0, (hooks are the way to go)[https://github.com/appcelerator-modules/hook-embedded-frameworks].
Steps to enable:
- Add the above to the hyperloop.ios.xcodebuild.flags object of your appc.js
- Place the ti.dynamiclib.js file in <your-project-root>/plugins/ti.dynamiclib/hooks
- Add the plugin to your tiapp: ```<plugin>ti.dynamiclib</plugin>```

If you are using Titanium SDK 6.2+, specifically Hyperloop 2.2.0+, according to (TIMOB-23853)[https://jira.appcelerator.org/browse/TIMOB-23853] Embedded binaries are now supported

Some frameworks include Simulator architectures ("fat libraries"). 
Those frameworks usually provide a script to strip the unused architectures for distribution, 
e.g. strip-framework.sh. If you use such a framework, adjust the path of the variable scriptPath, 
otherwise null it to skip the build script phase. 
An example of this file is included in this repo linked above(© Realm).

Here is a recent example that I found:
[PSPDFKit](https://github.com/PSPDFKit/Appcelerator-iOS) - Appcelerator Titanium Bridge for PSPDFKit for iOS https://pspdfkit.com

### Here's the difference.  It's with how XCode build steps are set
- **Native Modules**: [CLI hook](https://github.com/appcelerator-modules/hook-swift-frameworks/blob/master/ti.swiftsupport.js#L18) - `cli.on('build.ios.xcodeproject', cb)`
```'use strict';
   
   exports.id = 'ti.swiftsupport';
   exports.cliVersion = '>=3.2';
   exports.init = init;
   
   /**
    * Main entry point for our plugin which looks for the platform specific
    * plugin to invoke
    */
   function init(logger, config, cli, appc) {
   	cli.on('build.ios.xcodeproject', {
   		pre: function(data) {
   			logger.info('Enabling Swift support ...');
   
   			var xobjs = data.args[0].hash.project.objects;
   			var SWIFT_VERSION = 3.1; // Change to desired Swift version
   															
   			Object.keys(xobjs.PBXNativeTarget).forEach(function (targetUuid) {
   				var target = xobjs.PBXNativeTarget[targetUuid];
   				if (target && typeof target === 'object') {
   					xobjs.XCConfigurationList[target.buildConfigurationList].buildConfigurations.forEach(function (buildConf) {
   						var buildSettings = xobjs.XCBuildConfiguration[buildConf.value].buildSettings;
   						buildSettings.ALWAYS_EMBED_SWIFT_STANDARD_LIBRARIES = 'YES';
   
   						if (!buildSettings.SWIFT_VERSION) {
   							buildSettings.SWIFT_VERSION = SWIFT_VERSION;
   						}					
   					});
   				}
   			});
   		}
   	});
   }
```


- **Podfile**:
```post_install do |installer|
       installer.pods_project.targets.each do |target|
           target.build_configurations.each do |config|
               config.build_settings['SWIFT_VERSION'] = '3.1'
               config.build_settings['SWIFT_OPTIMIZATION_LEVEL'] = '-Onone'
               config.build_settings['ALWAYS_EMBED_SWIFT_STANDARD_LIBRARIES'] = 'YES'
           end
       end
   end
```
You can see the power of manipulating build settings on targets, especially if you come from 
 a native iOS development background

So now back in Ti world, how do we get access to these frameworks?
The documentation says to put the framework(s) in `/app/platform/ios`.
Although

## Other Alternatives
If you can't get the Pod working, maybe [make it into a framework](https://github.com/CocoaPods/cocoapods-packager) and use that.
YMMV.  If this works for you, please let us know!

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

### Modules

**Cross-Platform (Android and iOS)**
- [Ti.hockeyapp](https://github.com/hyperloop-modules/ti.hockeyapp) - Hyperloop-based version of HockeyApp for both Android and iOS
- [Ti.Firebase](https://github.com/hansemannn/titanium-firebase) - This project will contain all Firebase-related modules for Analytics, Cloud-Messaging, Authentication, Firestore etc.

### Other Code Examples
 - [Official Github example](https://github.com/appcelerator/hyperloop-examples) - Hyperloop Examples
>The following application demonstrates direct native API access using Appcelerator Hyperloop.
 - [Imaging Workshops ToDo](https://github.com/appcdev/imagine-workshops-todo/tree/hyperloop?files=1) - Todo Demo App
- [titanium-auth-session.js](https://gist.github.com/hansemannn/71b6181557ec0f6024e29c642dbe52e3) - Use Axway Hyperloop to perform OAuth-sessions with the iOS 11+ API "SFAuthenticationSession"

### Podfile Examples
These are listed to see if there are any gems on the Podfiles.  From a short secon look it sees that most are normal ObjectiveC podfiles
If you know of some referencing 3rd Party frameworks, especially Swift ones, please let us know!
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

 
 ### appc.js
 The following is an example of a Hyperloop enabled appc.js:
 
 ```/**
     * Hyperloop configuration
     */
    module.exports = {
    	type: 'app',
    	group: 'titanium',
    	dependencies: {
    	},
    	hyperloop: {
    		ios: {
    			xcodebuild: {
    				/**
    				 * any flags available to be passed into the Xcode can be
    				 * included here to further customize the xcode build
    				 */
    				flags: {
    					GCC_PREPROCESSOR_DEFINITIONS: 'foo=bar'
    				},
    				/**
    				 * this sample doesn't use StoreKit but this demonstrates
    				 * how you can bring in frameworks explicitly. Hyperloop
    				 * will automatically determine the required frameworks
    				 * but in case you want to force a specific version, you can
    				 * include it here
    				 */
    				frameworks: [
    					'StoreKit'
    				]
    			},
    			/**
    			 * optionally, you can bring in third-party or first-party libraries,
    			 * source code, resources etc. by including them here. The 'key' is the
    			 * name of the package that will be used in the require (if code).
    			 * the values can either be an Array or String value to the directory
    			 * where the files are located
    			 */
    			thirdparty: {
    				'MyFramework': {
    					// these can be an array or string
    					source: ['src'],
    					header: 'src',
    					resource: 'src'
    				}
    			}
    		}
    	}
    };
```

### A Deeper Dive
While doing experiments with Hyperloop it was useful and sometimes necessary to see what is happening behind the scenes
- Metabase Generation
- Build folder: ```/build/hyperloop/ios/js/[FRAMEWORK]```
- Using Safari's Web Inspector as a debugger


## Metabase Generation


## Build Folder
After you build your app if you have configured Hyperloop you will be able to find some information Build folder: ```/build/hyperloop/ios/js/[FRAMEWORK]```
It's mostly ```*.js``` files with an occasional ```*.m``` file.

***Files in ```/build/hyperloop/ios/ ```***
- ```symbol_references.js``` - This is a JSON object composed of the following: ```setter```,```getter```,```functions```.
 It's pretty verbose but verfied that it has strings of frameworks' variables and classes that were specifically invoked.
 It also has a lot of more common invocations like ```"createController": 1```.  Possibly more to follow on this if it's worth a revisit.
 I'll guess that with Axway moving to use Hyperloop integration in the base SDK, the ported parts will show here.

- ```metabase-framework-[UID]``` - This file maps framework headers to a this consolidated resource
 ```{
      "name": "[FRAMEWORK_NAME]",
      "path": "[PROJECT_ROOT]/platform/ios/[FRAMEWORK_NAME].framework",
      "type": "dynamic",
      "includes": {
        "[FRAMEWORK_HEADER_1]": "[PROJECT_ROOT]/platform/ios/[FRAMEWORK_NAME].framework/Headers/[FRAMEWORK_HEADER].h",
        "[FRAMEWORK_HEADER_2]": "[PROJECT_ROOT]/platform/ios/[FRAMEWORK_NAME].framework/Headers/[FRAMEWORK_HEADER].h",
        "[FRAMEWORK_HEADER_3]": "[PROJECT_ROOT]/platform/ios/[FRAMEWORK_NAME].framework/Headers/[FRAMEWORK_HEADER].h",
        // ...
      }
    }```
 
- ```metabase-8.0-[PLATFORM]-[UID].h``` - This is where frameworks' main headers are imported.
 ```
  /**
   * HYPERLOOP GENERATED - DO NOT MODIFY
   */
  #import "/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneSimulator.platform/Developer/SDKs/iPhoneSimulator11.1.sdk/System/Library/Frameworks/Foundation.framework/Headers/Foundation.h"
  #import "[PROJECT_ROOT]/platform/ios/[FRAMEWORK_NAME]/Headers/[FRAMEWORK_HEADER].h"
  ```

- ```metabase-8.0-[PLATFORM]-[UID].json```

***Files in ```/build/inspectFrameworks/ ```***
- ```frameworks.json``` - Appears to be references to third party frameworks included in the project 
Example entry:
```"[PROJECT_ROOT]/platform/ios/FrameworkName.framework": {
         "name": "Framework Name",
         "path": "[PROJECT_ROOT]/platform/ios/FrameworkName.framework",
         "type": "dynamic",
         "architectures": [
           "i386",
           "x86_64",
           "armv7",
           "arm64"
         ]
       } ```