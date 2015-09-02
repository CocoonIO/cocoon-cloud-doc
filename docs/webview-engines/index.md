Webview Engines
==================

The webview engines, previously known as environments or runtimes, are the elements in which an application packed using Cocoon is running. Currently, a developer can pick between three webview engines: Canvas+, System Webview and Webview+. Depending on the nature of your project, some of them will be more suitable than the others.

Except the system webview, the rest of the webview engines will be included in each project as any other plugin. Project detail screen can be used to include them easily and without editing the config.xml file. It is recommended to use this option as some of them require a specific version of cordova in order to work properly. If you are interested on installing them manually, there is a brief explanation in every webview engine dedicated section.

## Canvas+
Canvas+ is a custom webview engine optimized for canvas operations. It provides a subset of the standard HTML5 functionalities and is specially designed to run canvas based games and 2D/3D animation. It has limited DOM access, but you gain native performance to your 2D/3D games.

To learn more about Canvas+ and how to install it in your projects, visit [this dedicated](/webview-engines/canvas-plus) section.

## System Webview
System Webview provides a complete HTML5 webview engine based in the webview of the host device. It has full DOM access. However, the performance and features available rely on the host OS.

In order to get more information about when to use it, you can visit our [Webview](/webview-engines/system-webview) section

## Webview+
Webview+ is a custom webview engine exclusive for android 4.0.0 and higher or iOS 8 and higher. Webview+ on android is based on [crosswalk project](https://crosswalk-project.org/). Webview+ for iOS is based on iOS 8's [WKWebview](https://developer.apple.com/library/ios/documentation/WebKit/Reference/WKWebView_Ref/) It provides a uniform execution environment for any android and iOS devices.

To learn more about it, and its features and the installation, you can visit the [Webview+](/webview-engines/webview-plus) section.
