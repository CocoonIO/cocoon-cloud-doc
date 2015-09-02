ScreenCanvas
==============

ScreenCanvas is a canvas+ specific high performance canvas. In canvas+ you can create 2 types of canvas:

* A standard canvas renders everything to an internal drawing buffer (render to texture). At the end of the frame the texture is drawn to the screen buffer.
* A screencanvas doesn’t create any internal drawing buffers. It renders directly to the screen buffer. This allows huge rendering performance improvements in some GPUs. It also uses less memory because it avoids the creation of an offscreen texture.

Screencanvas should only be used for the main canvas added to the DOM: the canvas where you render all your stuff.

## Possible side effects

When using screencanvas it is very important to render the whole screen in every frame to avoid flickering issues in some devices. Just render a fullscreen image or clear the background color from/of each frame.

When using screencanvas with a webgl context, CSS canvas scales are omitted, so your game might not render in full screen. To fix this issue scale or layout your game with a projection matrix instead of using canvas.style

## How to enable ScreenCanvas

Set the screencanvas property of a canvas to true before calling to getContext():
```
var canvas = document.createElement("canvas");
canvas.screencanvas = true;
canvas.width = window.innerWidth * window.devicePixelRatio;
canvas.height = window.innerHeight * window.devicePixelRatio:
var ctx = canvas.getContext("experimental-webgl");
```
You can also use the screencanvas DOM attribute:
```
<canvas ... screencanvas='true' ...>
```
