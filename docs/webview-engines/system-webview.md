System Webview
==============

## Introduction

System Webview provides a complete HTML5 webview engine. It is the default webview of each device. It has full DOM access and low footprint. However, the performance of your project might be affected. In addition, the behavior of your app might vary slightly from one device to another as the System Webview is not the same in all devices.

### Advantages

* As this webview engine is part of the device in which the application is installed, it doesn't require additional space.

### Disadvantages

* The same application might have different behavior or aspect depending on the device. This is specially remarkable on Android-based devices below 4.4 version. The System Webview may vary from one device to another, being necessary different CSS and/or JS behavior depending on the host OS.

### Debugging

Depending on the OS version and the System Webview version, you can be able to debug your applications running in the System Webview in some cases following these steps:

#### Android

- Follow the instructions to enable remote debugging in your Android device: https://developer.chrome.com/devtools/docs/remote-debugging
- Open your the Developer App and launch your app using the System Webview
- Open a Chrome browser and go to chrome://inspect/
- Click on the app you want to inspect and the Chrome Developer tools should be opened. If your application doesn't appear is because your System Webview version is not compatible.

#### iOS

- Connect your iOS device to your Mac computer using the USB cable
- Go to Settings -> Safari -> Advanced and enable the "Web Inspector"
- Open you Developer App and launch your app using the System Webview
- Open A Safari browser and go to the "Develop" menu. You should see the connected device there. If your application doesn't appear is because your System Webview version is not compatible.
- Select the application and the Web Inspector should be opened

### When to use it

When you are targeting a small range of devices with a well-known version of OS and the project doesn't have any performance objectives.
