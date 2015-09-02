Canvas+
=============

## Introduction

Canvas+ is a webview engine that allows you to execute your JavaScript HTML5 applications on mobile devices. It not only accelerates the performance of the game but also allows you to access native device features. Although it runs plain JavaScript, there is no support for the entire HTML5 API.

Canvas+ is perfectly tuned for games and it tries to provide the best acceleration technology using the minimum set of HTML5 functionalities needed. Although these functionalities should be enough to run a game, there are some situations where accessing a full DOM environment could be very useful for developers. In these situations is where a [Webview+](/webview-engines/webview-plus) or a [System Webview](/webview-engines/system-webview) will be more suitable than Canvas+.

### Advantages

* **High performance**: It is the fastest webview engine.
* **Light weight**: Only 5MB of space.
* **Compatibility** with old OS versions.
* **Portability**: Android, iOS, Wearables...
* Specially thought and designed for **Gaming**.
* **Ultra-fast** bindings: box2d, gamepad...

### Disadvantages

* **DOM** access is restricted.
* It is *not* a full browser.
* Less suitable for apps than the other webview engines.

### When to use it

* If you are developing canvas based game that requires mainly high performance and high FPS rate.
* If your game does not require DOM UI elements and you want it to be easily portable to other OS versions and light.
* If you are using a canvas based game engine, such as Phaser, Pixi, PlayCanvas, Kiwi.js ...

## Supported features

* Canvas
* WebGL
* Audio
* Websockets
* XHR
* Localstorage (with no limit)
* Extend it using Plugins for Cordova
* [Cocoon plugins](/plugins/cocoon-plugins)

## Unsupported features

* CSS and DOM UI elements
* WebAudio
* DOMParser class
* WebRTC
* WebWorkers

## Canvas+ special features

* [Canvas+ internal webview](/canvas-plus/internal-webview)
* [Screencanvas](/canvas-plus/screencanvas)
* [NPOT Textures](/canvas-plus/memory-management#npot-textures)
* [Texture reducer](/canvas-plus/memory-management#texture-reducer)
* [Max Memory threshold](/canvas-plus/memory-management#max-memory-threshold)
* Supersampling
* Path rendering

## Canvas+ API

Cocoon Canvas+ are multiplatform Javascript utilities that work in Canvas+. These plugins are included in Canvas+ core, so it is not required to install anything else at the cloud. The required files, if so, will be injected automatically in your project.

*  <a href="http://cocoonio.github.io/cocoon-canvasplus/dist/doc/js/index.html" target="_blank">See Canvas+ full API documentation</a>. Click the different namespaces to move between sections.

Unlike old CocoonJS plugins, Cocoon Canvas+ plugins need to wait for [Cordova deviceready event](https://cordova.apache.org/docs/en/4.0.0/cordova_events_events.md.html#deviceready) to start working. This event fires when Cordova is fully loaded.
```
document.addEventListener("deviceready", onDeviceReady, false);

function onDeviceReady() {
	// Cocoon Canvas+ code here
}
```

## Others

* It is possible to use plugins inside Canvas+ as long as they are supported by Cordova 5.0.
* It does not require the whitelist plugin added by default in the config.xml generation.
