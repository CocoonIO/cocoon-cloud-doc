Webview+
=============

## Introduction

The Webview+ is aimed at developers that need good DOM support and a stable platform to work with. For developers using canvas or WebGL, our accelerated canvas solution, [Canvas+](/webview-engines/canvas-plus), is still much faster and fine-tuned for high-performance, graphics-intensive apps, and that's what we still recommend for high-paced games.

The Webview+ for Android is a uniform webview engine on any Android 4.x device based on Crosswalk. Webview+ for iOS is a webview engine that provides a replacement for the UIWebView that includes the Nitro JS engine based on the WKWebView.

### Advantages

* HTML5 API is fully supported: WebAudio, CSS, DOM UI elements, ...
* Good performance
* It is a full browser
* In iOS it is light weight as it is included in the same device.

### Disadvantages

* Performance is not as good as in Canvas+, specially noticeable at startup
* In Android it takes around 20MB to include this webview engine.
* Only supports Cordova <content src="index.html"/> as content origin for iOS. The Content URL setting must point to index.html in your settings.

### When to use it

For application that target wide range of devices.

## Others

* It is possible to use plugins inside Webview+ as long as they are supported by Cordova 4.0.x.
