Memory management
===================

Memory is a critical resource in HTML5/JavaScript game development, especially on mobile devices. In a desktop environment you can load tons of textures but on some low-end mobile devices you can reach the maximum RAM limit quickly. Although JavaScript encourages automatic memory management by using a garbage collection mechanism, you shouldn’t ignore effective memory management techniques. HTML5/JavaScript applications can suffer the same memory related problems as native applications, such as memory leaks, out of memory issues and they must also deal with garbage collection pauses.

This article will give you some general advice on memory optimization for HTML5 games and some Canvas+ specific tips.

## Effective asset loading

Preloading all the assets at the start is the easiest and quickest way to manage the memory but it only works for small games where all the assets fit into the available memory. You shouldn’t preload everything on a heavy game, only the assets that you need each time, and dispose of the unneeded assets as soon as possible. Your game memory usage depends highly on your game engine (some of them do a better job than others). Don’t expect that the browser or the garbage collector will fix all your problems and that you can stop worrying about effective memory management.

## Texture packer

Javascript images and canvas objects are backed into OpenGL textures and FBOs, usually using RGBA format, 32 bits per pixel. Think about it, for example a 2048×2048 image eats 16MB of memory!  Some GPUs require POT (Power Of Two) textures for the best performance, so keep in mind that some images could use more memory than their real size and use 2^n size textures whenever you can.

We recommend that you pack all your textures using one of the Sprite Packer tools out there. That way you’ll waste less memory and improve performance (by avoiding the number of context switchings) and loading times. Some HTML5 engines are able to pack all your textures at runtime, others don’t, so please check your engine features first.

## Garbage Collection

JavaScript automatically frees objects when it detects that they are not used anymore, this process is called garbage collection. During a collection the execution on your page can be suspended for a moment. If your game creates too many JavaScript objects in each frame it can lead to noticeable pause issues. This is another example that proves that it is a mistake to forget about memory management on JavaScript. You should reuse javascript objects whenever possible.

## The dispose method

Image and Canvas objects are disposed when the garbage collector detects that they are not reachable in the JS code. The disposal is not immediate, it may take some seconds depending on the heuristic rules of the JavaScript virtual machine. Using a WebGL context the developer has more precise control over the WebGL texture and buffers disposal but that’s not the case when using a 2d context or when dealing with Image and Canvas objects.

Canvas+ exposes a method called “dispose” on canvas, image and audio objects. This method immediately frees the associated texture or internal buffer, which is very useful for games with heavy textures or for games that need a greater control over the memory.

Using this Canvas+ exclusive feature is very easy. Imagine we have an image object represented by the “myImage” variable.
```
myImage.dispose && myImage.dispose(); // The same for canvas and audio objects.
```

## The memory warning event

iOS and Android native applications are able to receive a memory warning notification from the system. The default implementation in Canvas+ and WebView+ environments is to perform a garbage collection and free as many internal cached data objects as possible.

Canvas webview engine exposes the “memorywarning“ notification as a window listener. It is strongly recommended that you implement this method and free up as much memory as possible by disposing of cached data objects, images on canvases that can be recreated.
```
Cocoon.on(“memorywarning”, function() {
  // dispose of cached images and canvases that can be recreated
});
```
## Texture reducer

Texture reducer is a Canvas+ exclusive feature. When your game targets all resolutions you need huge textures for iPad retina like devices and small textures for small mobile devices. A game developer has many ways to handle this:

Create different asset packages, HD and normal. Good solution but bigger app size.
Scale down HD resources. Excessive memory usage and performance impact on small devices.
Create smaller asset packages on runtime rendering to a canvas/texture. Good solution but some JavaScript engines don’t support this.
Canvas+ texture reducer feature can transparently do the job for you. It uses the third approach and it is highly customizable (for example, you can only apply it to certain resources). Check out the complete API documentation to see how to set it up.

As the texture reduction lowers the quality of the final images to be displayed, an interesting approach that we have recommended to some customers is to apply it only for certain device models, leaving higher resolution for some others (you can use the “navigator.userAgent” property to identify the device model). This, of course, it is not an easy task on Android due to the big number of device types, but on iOS is definitively an interesting option, specially for older devices such as the iPhone4 or the iPad Mini 1st generation.

Check out the [API documentation](http://cocoonio.github.io/cocoon-canvasplus/dist/doc/js/Cocoon.Utils.html#toc12).

## Max Memory Threshold

This new Canvas+ exclusive feature exposes the “setMaxMemory” utility method. When the max memory threshold is set, Cocoon checks the total amount of texture sizes (images and canvases). When the runtime memory size reaches the max memory threshold, Cocoon disposes of the least recently used textures until the memory fits the threshold. It disposes of textures used for JS Image objects (which can be reloaded later if needed or are drawn again). It doesn’t dispose of canvas objects because they cannot be reconstructed if they are used again in a render operation. This extension is designed to be used in 2D contexts, because in WebGL contexts the developer is the one responsible for memory disposal.

Check out the [API documentation](http://cocoonio.github.io/cocoon-canvasplus/dist/doc/js/Cocoon.Utils.html#toc9).

## Lazy Loading

Another Canvas+ exclusive feature available on version 2.1 and higher we have added the “cocoonLazyLoad” boolean property to Image objects (we have also added a duplicate called “idtkLoadDisposed” for retro compatibility with Construct2). When the property is set to true, the image is not loaded until it’s used in a render operation. Engines that load all the assets at startup can benefit from this property. But do not forget to purge the textures when they are not needed again, for example, using the dispose mechanism described earlier!

## NPOT Textures

Canvas+ uses POT (Power Of Two) textures by default in 2d contexts. This is very useful for performance improvements, especially on mobiles with old GPUs. But it can waste memory on games that don’t use packed or 2^n textures. In Canvas+ you can allow NPOT textures in Canvas2D contexts (they were already supported in WebGL).

Check out the [API documentation](http://cocoonio.github.io/cocoon-canvasplus/dist/doc/js/Cocoon.Utils.html#toc10).

## Conclusion

We have covered some basics of memory management in HTML5 games and exposed Canvas+ specific tips and tools.  We are always open to your suggestions. Remember that if you have some problem with memory usage in Canvas+ and you think that the problem is on our side you can send us a testcase and we’ll be glad to help you.

## Additional Notes about Canvas+

Canvas+ is not a full browser, but a highly optimized JavaScript Virtual Machine for Canvas 2D and WebGL environments. Comparing it to a full fetched browser is not recommended as browsers include “a lot of magic tricks” (and that is why sometimes they are big and slow). For example, a browser might be able to handle a 5000 by 5000 pixels image but that does not mean that the underlying device is able to do it, just that the browser is handling some things internally for you either lowering the quality of the image (downscaling it) or subdividing it. Very few native technologies (C++ game engines) allow this kind of features as the developers should know how to handle this situations correctly (do not use 5000×5000 textures in the first place). Here at Ludei we never intended to create a new browser, but provide a highly specialized runtime environment so HTML5 developers can be closer to the native side without ever leaving JavaScript and the great HTML5 APIs.
