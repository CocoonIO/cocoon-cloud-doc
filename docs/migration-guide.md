Migration guide
==================

If you are one CocoonJS cloud compiler user, you are probable wondering why we released a new cloud compiler and what advantages the new Cocoon.io can provide to your project.

The main difference is that Cocoon.io is based on Cordova. But, why is this so important? Because now we are following a standard. Thus, it is much easier than before to customize all the assets and permissions your project requires . In addition, all the features you had in the old cloud not only are available but also improved. The only bad side of all of this is that, as this new cloud is based on Cordova, your project might require some few changes.

In this guide you will find a fast and easy to follow summary of all the elements you must take into account to adapt your project and why these changes are necessary.

## The project structure

If you have ever created a project using Cordova, you might be familiar with this structure:  

```
project_folder/
|-- config.xml
|-- plugins/		--> installed plugins
|-- platforms/      --> available platforms
|-- res/
|   |-- android/	--> icons for android
|   |-- ios/		--> icons for ios
|   `-- screen/ 	--> splashes
`-- www/			--> your code

```
However, most of these elements can be added, installed and customized inside the cloud after the project is created (platforms, icons, splashes, plugins, ...). By now, let's focus only in two of them: the **www** folder and the **config.xml** file.

### www/

This folder should contain all the source code your project need. The content of this folder is the minimum required to create a valid project.  

In the old cloud, all the files contained in this folder would be the ones you compress on a zip file to drag and drop it before compilation.

In addition, you must:

#### Wait for the deviceready event

Unlike the old cloud, in Cocoon.io all the plugins need to wait for [Cordova deviceready event](https://cordova.apache.org/docs/en/4.0.0/cordova_events_events.md.html#deviceready) to start working. This event fires when Cordova is fully loaded. It is required even in Canvas+ and its special features.

#### Attach the cordova.js file to your index.html

As Cocoon.io is based on Cordova, the cordova.js file must be referred in your index.html file.

This file will be added during compilation, so it is enough if you copy and paste this line in your code:
```
<script src="cordova.js"></script>
```
### config.xml

Through this global configuration file it is possible to control many aspects of an app's behavior. If you have never used Cordova, it is better if you let the cloud to generate a default one for the specific project. A default config.xml would have more or less this aspect:

```
<?xml version='1.0' encoding='utf-8'?>
<widget id="com.example.hellococoon" version="1.0.0" xmlns="http://www.w3.org/ns/widgets" xmlns:cocoon="http://cocoon.io/ns/1.0">
    <name>HelloCocoon</name>
    <description>
        A sample Cocoon application that responds to the deviceready event.
    </description>
    <author email="user@example.com" href="https://cocoon.io">
        Author's name according to the user profile
    </author>
    <content src="index.html" />
    <plugin name="cordova-plugin-whitelist" version="1" />
    <access origin="*" />
    <allow-intent href="http://*/*" />
    <allow-intent href="https://*/*" />
    <allow-intent href="tel:*" />
    <allow-intent href="sms:*" />
    <allow-intent href="mailto:*" />
    <allow-intent href="geo:*" />
    <platform name="android">
        <allow-intent href="market:*" />
    </platform>
    <platform name="ios">
        <allow-intent href="itms:*" />
        <allow-intent href="itms-apps:*" />
    </platform>
</widget>
```
You can edit this file directly at the cloud from the project configuration, in the config.xml tab.

However, our recommendation is to use the raw editing as less as possible, since it's more error prone. If it is possible, it is better to use the settings tab:

![[class='center'] Settings tab](img/settings-tab.png "Settings tab")

In any case, remember to save or discard the changes before compiling.

If you want to know more about all the options that can be changed and set using the config.xml file, you can visit [Cordova oficial config.xml documentation](http://cordova.apache.org/docs/en/5.0.0/config_ref_index.md.html#The%20config.xml%20File)

## CocoonJS plugins and Canvas+

CocoonJS plugins are no longer valid in this cloud, or at least not exactly in the same way. Instead of them, we have developed the new Atomic plugins. It is possible to use them in any webview engine, and not only inside the cloud, as these plugins are available in many languages.

Apart from these new plugins, there exist some Canvas+ special features that were contained in CocoonJS plugins and, from now on, they have their own specific section: Canvas+ API. Unlike Atomic Plugins, these features will only work inside Canvas+ and they don't require additional files or installation.

In addition, it is important to mention that Canvas+ not only supports the new Atomic Plugins, but any other plugin for Cordova adapted for Cordova 5.0.0 or more.

### Atomic plugins

Atomic Plugins represent a new paradigm for creating plugins that work across many platforms and with the same API in several programming languages.

Atomic plugins are available for Cordova and they can be installed directly at the cloud using the "Cocoon" tab in the plugins installation panel. These are the Cocoon plugins.

![[class='center'] Plugins installation](img/cocoon-tab.png "Cocoon Tab")

You can find more information about the Cocoon Plugins [here](/plugins/cocoon-plugins).

### Canvas+ API

Cocoon Canvas+ are multiplatform Javascript utilities that work in Canvas+. These plugins are included in Canvas+ core, so it is not required to install anything else at the cloud. The required files, if so, will be injected automatically in your project.

*  <a href="http://cocoonio.github.io/cocoon-canvasplus/dist/doc/js/index.html" target="_blank">See Canvas+ full API documentation</a>. Click the different namespaces to move between sections.

## Canvas+ & Webview

It is still possible to render a transparent Webview on top of the Canvas+ OpenGL ES rendering context in order to have DOM access inside Canvas+. However, even if we said it was no longer required to add additonal files to your code in order to use Canvas+ special features, as this internal webview is not the main webview engine where the code will be executed, it is neccesary to add manually several files to the content that will be displayed in internal webview.

You can read more about these files and why they have to be added manually in [Canvas+ internal webview section](/webview-engines/canvas-plus).

## The Developer App

In Cocoon.io the old CocoonJS Launcher is replaced by the Developer App. To get a Developer App it is necessary to compile it at the cloud. The Developer App can be created at the project configuration and it will have all the plugins and settings the original project has.

You can learn more about the Developer App and its settings [here](/user-guide/developer-app).
