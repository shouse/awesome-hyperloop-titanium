# Awesome: Titanium Hyperloop

[![Appcelerator Titanium](http://www-static.appcelerator.com/badges/titanium-git-badge-sq.png)](http://appcelerator.com/titanium/)
![Hyperloop Enabled](https://img.shields.io/badge/hyperloop-enabled-red.svg)&nbsp;
![platform](https://img.shields.io/badge/platform-ios-blue.svg)&nbsp;
![platform](https://img.shields.io/badge/platform-android-blue.svg)&nbsp;
![platform](https://img.shields.io/badge/platform-windows-orange.svg)&nbsp;
[![License MIT](https://img.shields.io/badge/license-MIT-green.svg?style=flat)](https://writing.kemitchell.com/2016/09/21/MIT-License-Line-by-Line.html)&nbsp;

### A curated list of awesome links to resources around Axway's Hyperloop for Titanium

**What is Hyperloop?**

Use any native API via JavaScript
Anything you can write in Objective-C, Swift, Java, or C# can be represented with JavaScript.

**What is this repo for?**

There's so much **awesomeness about Hyperloop**, but it's **difficult to find** an aggregated spot of up-to-date **information about it**.

This repo is an attempt to bridge that gap and link the community to relevant information so that we can **make more badass software**!

**Cool!  What can I do?**

- Got something that belongs here? [Fork](https://github.com/shouse/awesome-hyperloop-titanium/edit/master/README.md#fork-destination-box) and Submit a PR!
- Want information about something but don't have a link?  [Create an issue!](https://github.com/shouse/awesome-hyperloop-titanium/issues)

## Table of Contents
 - [iOS and Android Modules and Code](https://github.com/shouse/awesome-hyperloop-titanium#platform-specific-resources)
 - [Information and Articles](https://github.com/shouse/awesome-hyperloop-titanium/blob/master/README.md#information-and-articles)
 - [I Need Help!!!](http://tislack.org/) - We gotcha covered!  Join our awesome Slack team and get help with hyperloop in the ```#hyperloop```, ```#help-me```, or ```#jobs``` channels!  If it can be done somewhere there can help it happen.

### Platform Specific Resources

- **Android**
[This page dedicated to Android and Hyperloop](Android/README.md)

- **iOS**
[This page dedicated to iOS and Hyperloop](iOS/README.md) - Links to working podfiles and relevant information

- **Windows**
[Windows Hyperloop Programming Guide](https://wiki.appcelerator.org/display/guides2/Windows+Hyperloop+Programming+Guide) has information on running a demo application specifically for Windows and you can learn how to use Hyperloop in your own project.


### Information and Articles
 - [Sample App](https://github.com/appcelerator/hyperloop-examples)
 - [Axway Docs](https://docs.axway.com/bundle/Titanium_SDK_allOS_en/page/hyperloop.html) - Some of the best documentation currently
 - [Hyperloop FAQ](https://docs.axway.com/bundle/Titanium_SDK_allOS_en/page/hyperloop_faq.html)
 - [Hyperloop Builds](https://github.com/appcelerator-modules/hyperloop-builds) - Collection of the latest Hyperloop releases, including pre-release versions and master builds.

 - [Medium.com](https://medium.com/all-titanium/titanium-an-introduction-to-hyperloop-by-hans-knoechel-47d4326ca52e) - Blog post by Rene Pot - Featuring Hans Knoechel.   At the TitaniumNL meetup in Amsterdam at February 3rd, Hans Knoechel talked about Hyperloop and what Hyperloop actually is.
In short, Hyperloop allows you to talk from Javascript straight to Objective-C/Swift or Java without having to write wrapper modules. This makes it really really easy to extend native API’s for Titanium.
The presentation has been recorded and can be seen in full on YouTube.
- [Developing Native APIs with Hyperloop](http://www.appcelerator.com/blog/2017/10/developing-native-apis-with-hyperloop-a-beginners-guide/) -  
By Erin Bailey
October 25, 2017: 
Intreview with Nazir Dogan, Mobile Application Developer and Software Developer at Etiya, has been using Hyperloop since its early days to create six unique open-sourced modules.

[Enabling Hyperloop](https://wiki.appcelerator.org/display/guides2/Enabling+Hyperloop)
> Each Titanium project that want to use Hyperloop requires the Hyperloop-services to be enabled. By default, Hyperloop is disabled and you can enable it for your projects via the CLI or within Studio.
**TL;DR**

- For ```iOS``` add ```<use-jscore-framework>true</use-jscore-framework>``` to ```tiapp.xml``` 
- Add ```<module>hyperloop</module>``` to ```tiapp.xml``` 
- Add ```<plugin version="2.2.1">hyperloop</plugin>``` to ```tiapp.xml``` 


[AppC Blog - Tech Tutorial: Hyperloop Modules](http://www.appcelerator.com/blog/2017/07/tech-tutorial-hyperloop-modules/)

> In this in-depth video, Developer Evangelist **Jason Kneen** provides an overview of Titanium, its benefits and how it works. The tutorial delves into best practices for UI and views, navigation, buttons and labels, event handling, and data binding. Jason also demonstrates how these concepts are used in practice with a sample project code walkthrough.

 - [Release Notes](https://docs.appcelerator.com/platform/latest/?print=/guide/Hyperloop_Release_Notes)

**JIRA**

- [AppC Hyperloop Jira - Component:Hyperloop](https://jira.appcelerator.org/browse/TIMOB-25481?jql=project%20%3D%20TIMOB%20AND%20component%20%3D%20Hyperloop)
- [AppC Hyperloop Jira - Label:Hyperloop](https://jira.appcelerator.org/browse/TISTUD-8658?jql=labels%20%3D%20hyperloop)

- [AppC Hyperloop Jira - Open Tickets](https://jira.appcelerator.org/browse/TIMOB-25478?jql=status%20%3D%20Open%20AND%20labels%20%3D%20hyperloop) - See what issues are open

- [AppC Hyperloop Jira - Update Recently](https://jira.appcelerator.org/browse/TIMOB-25478?filter=-8&jql=labels%20%3D%20hyperloop)
