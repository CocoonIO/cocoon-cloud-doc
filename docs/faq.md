FAQ
================

### What is Cordova?
Cordova an open source project that has become the de-facto solution to create hybrid apps. You can learn more about cordova <a href="http://cordova.apache.org/#about" target="_blank">here</a>.

### Which benefits does cordova report to my projects?
Extensibility. Cocoon has been traditionally an ad-hoc solution for creating hybrid games. This led to complex updates and limited capability to extend the platform. Relying on cordova brings automatic compatibility with all the existent cordova plugins.

### What is the Cocoon version?
Cocoon is now built on top of cordova. Cocoon has its own version, and corresponds with different cordova version. Current cocoon is based on cordova 5.0.0 command line interface. It'll evolve with the time, for sure ;-)

### What is the cordova version reported?
Cordova is a complex system with different products. Each one with its own version. Current cocoon is based on cordova 5.0.0 command line interface.

The plugins for each platform must be compatible with the versions reported in the settings tab for each platform.

### My plugin doesn't work with the cocoon compiler. Why?
Each plugin must support the cordova version for each platform. Check the plugin compatibility, because it may not have been adapted to the running version of cordova android and cordova iOS.

### What is the config.xml file?
The config.xml is the soul of the new cocoon. This file determines the plugins to be installed, the configuration and version of each plugin, and the resources for the project: splashes, and icons.

The config.xml can be edited directly from the cocoon site in either two ways:

 * Setting the config values using the Settings and plugins tabs
 * Editing the config.xml file directly from the config.xml tab

Our recommendation is to use the raw editing as less as possible, since it's more error prone.

### I don't want to edit the config.xml online. What can I do?
The source code of your project must contain a config.xml file in its root directory. Either if you upload a zip file, or if you synchronize a github project, the config.xml must be accessible in the root folder.

### Is Canvas+ a cordova plugin?
Yes, but it can only be added to your projects using the cocoon platform.

### Is Webview+ a cordova plugin?
Yes, both versions (for Android and iOS) are cordova plugins. Webview+ for Android is based on crosswalk project. Webview+ for iOS can only be enjoyed with cocoon, as Canvas+.

### Can I still use old CocoonJS plugins / Canvas+ extensions?
Yes, you can. There are some namespaces that are deprecated in Cocoon.io, but the rest will work in exactly the same way but *only* in Canvas+. In addition, it is no longer required to add any extra file to your project. The required ones will be injected during the project compilation. You can visit the full documentation <a href="http://cocoonio.github.io/cocoon-canvasplus/dist/doc/js/index.html" target="_blank"> here</a>.

### I don't see "your desired target os here". Can I compile for it?
At the moment Cocoon supports Android and iOS. We're about to add more platforms in the future, but depends on the demand of our clients.

### How can I give access from webview+ to any external resource not in my domain?
Use the whitelist plugin. If you let the platform to create the default config.xml, we will install it for you.

### Do I need the whitelist plugin in canvas+?
No, by default Canvas+ doens't limit access to any external resources.

### What about the splash screen in Canvas+? Can I remove it?
No, you can't. But don't panic, it will be possible really soon.

### What is a testcase? Why did you ask me for one?
A testcase is the minimum sample of code required to reproduce an issue or bug. Sometimes, "less is more". The smaller the tescase is, the easier it will be for us to detect where the problem is.

### Do you have something extra to tell us?
We plan to support not only cordova's target OSs but other platforms like desktop, tv and others.
