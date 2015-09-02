Canvas+ internal webview
===========================

Canvas+ allows accessing a full DOM environment via Webview. Thus, there are two environments that live together: Canvas+ and WebView. Although both are two different JavaScript environments, Cocoon allows to render a transparent Webview on top of the Canvas+ OpenGL ES rendering context and it also provides a bidirectional communication channel between them. In this way, the final visual result seems to integrate both environments seamlessly.

## How to manage both Canvas+ and Canvas+ internal WebView

The main point to remember when managing Canvas+ and Canvas+ internal WebView is that different code will be executed in each, but by default the application will be loaded inside Canvas+.

The index.html file that the platform looks for will be loaded in the Canvas+. So, now the question is how it can be managed the WebView.

### loadInTheWebView

The easiest way to load the WebView is by using the Cocoon.App plugin and its [loadInTheWebView](http://cocoonio.github.io/cocoon-canvasplus/dist/doc/js/Cocoon.App.html#toc10) function.The WebView will load the resource and use an event object to specify if the operation succeed or failed.

The example below is one of the most simple ones. As we are managing two different environments, two different HTML files will be loaded.

This code should be present or linked in the index.html file:
```
Cocoon.App.WebView.on("load", {
	success : function(){
		Cocoon.App.showTheWebView();
	},
	error : function(){
	    console.log("Cannot show the Webview for some reason :/");
		console.log(JSON.stringify(arguments));
	}
});
Cocoon.App.loadInTheWebView("wv.html");
```
### forward and forwardAsync

Once both environments are loaded, it is time to understand how the communication between both environments works.
Both environments have a couple of functions to communicate with the other environment. For Canvas+, they are in the Cocoon.App namespace, meanwhile for the Webview they are in the Cocoon.Webview namespace.

These are the functions:

* **forward:** It sends some JS code to be executed in the other environment and wait for the result to be returned synchronously.
* **forwardAsync:** It sends some JS code to be executed in the other environment and do not wait for the result. The last parameter *MUST* be a callback function where the result will be forwarded back.

In the example below some code is sent from one webview engine to the other using the forward function.

Once a webpage is loaded in the WebView using the loadInTheWebView function, the WebView should be visible. In order to do that, the WebView has a show function inside the Cocoon.App namespace.

It is possible to call this function from the WebView code or from Canvas+ using the forward mechanism.
```
Cocoon.App.WebView.on("load", {
	success : function(){
		Cocoon.App.forward("Cocoon.WebView.show(0, 0, " + canvas.width/2 * window.devicePixelRatio + "," + canvas.height * window.devicePixelRatio + ");");
	},
	error : function(){
		console.error("Could not load the HTML file in the Webview");
	}
});
Cocoon.App.loadInTheWebView("WV.html");
```

## Required files

Unlike the previous cloud, as Cordova only injects automatically the required clobbers in the main webview engine, it is neccesary to add manually the following files to the content that will be sent and displayed in Canvas+ internal Webview:

* <a href="https://github.com/ludei/cocoon-common/blob/master/src/js/cocoon.js" target="_blank">cocoon.js</a>
* <a href="https://github.com/CocoonIO/cocoon-canvasplus/blob/master/dist/js/cocoon_canvasplus.js" target="_blank">cocoon_canvasplus.js</a>

If these files are not present, Canvas+ internal Webview will not have access to Cocoon object.
