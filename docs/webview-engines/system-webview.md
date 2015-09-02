Webview
==============

## Introduction

System Webview provides a complete HTML5 webview engine. It is the default webview of each device. It has full DOM access and low footprint. However, the performance of your project might be affected. In addition, the behavior of your app might vary slightly from one device to another as the System Webview is not the same in all devices.

### Advantages

* As this webview engine is part of the device in which the application is installed, it doesn't require additional space.

### Disadvantages

* The same application might have different behavior or aspect depending on the device. This is specially remarkable on Android-based devices below 4.4 version. The System Webview may vary from one device to another, being necessary different CSS and/or JS behavior depending on the host OS.

### When to use it

When you are targeting a small range of devices with a well-known version of OS and the project doesn't have any performance objectives.
