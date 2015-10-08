Developer app
=================

The developer app is a mobile native app to ease the development and debugging process of a Cocoon project. This application is created in the project settings and it will have the same configuration as the project has at that very moment: plugins, icons and splashes and preferences. It will allow the developer to test the source under the same circumstances the final compilation would use.

## How to get a Developer app

In the near future, it will be possible to download an official Developer App from the store. However, it is not possible yet. The only way of getting a developer app is compiling it at the cloud.

Compiling a developer app is as easy as cliking the button just under the project settings menu.

![[class='center'] Developer App - compilation](img/dev-app-cloud.png "Developer app - compilation")

Once the developer app is compiled, you can download it to your pc and install it on your mobile device.

## How to use it

As soon as the app is launched, there are two options to load your files for testing.

### External URL

The first option to load your source code on the developer app is to use an external URL. This URL can point to an index.html file or directly to a zip file that will be downloaded and uncompressed. In any case, it is necessary that the index.html file is in the root of the zip of the external resource.

The Cordova plugins and the cordova.js scripts are already bundled in the Developer App so you don't really need to have them there but you need to have the cordova.js script tag reference somewhere in your index.html.

![[class='center'] Developer app external url](img/developer_app_urls.png "Developer app - external URL")

Once the url is written, or loaded using a QR, all the possible webview engines in which to run your source code will appear at the bottom of the screen.

Just clicking one of them, the project will be launched using that specific webview engine.

### Documents stored in the device

It is possible also to run a zip file placed inside the device. From the Developer App's documents tab, you will have access to the Application Documents on iOS devices. On Android, it will be possible to load the zip file from the external SD card.

The zip must contain an index.html with relative references to all the resources you need in the zip file.

![[class='center'] Developer app documents](img/developer_app_doc.png "Developer app - documents")

If the icon of the folder is blue and detected as a zip file, it will be possible to select it and, after selecting the webview engine, it will be launched.

## Settings

Clicking on the settings button on the top right corner of the screen, will open the settings menu in which it will be possible to distinguish three main sections: General, Debug and Canvas+.

![[class='center'] Developer App - settings](img/developer_app_settings.png "Developer app - settings")

### General settings

All the options placed on this section will be available for any webview engine and it will affect every project launched with the developer app. Even if these options are set in the config.xml file when the developer app is created, they can be modified from here.

### Debug settings

This section allows the user to show/hide de debugging console and customize its options (Possition when the project is launched and FPS type to show when the project is running).

It is important to mention that the FPS text shown when the project is running works as a button that opens the debugging console. Enabling the debug options will allow the user to visit this console in order to relaunch the project or see the console log reported by the developer app.

*Note:* currently this section is only available for Canvas+.

### Canvas+ special features

This section will only apply to Canvas+ webview engine. In order to make persistent all the options included, it is necessary to add certain functions to your source code.

You can learn more about these features and how to use them [here](/canvas-plus).

### Favorites

If you double tap a file or a url entrance, they will appear two new options. One for deleting the reference from the list, the second one for favoriting it. Once an entrance is marked as favorite, it will be kept in the Favorites section in order to have a faster access.

![[class='center'] Developer app favourites](img/developer_app_fav.png "Developer app - favourites")

To unfavorite an entrance in any list, just double tap the entrance and unselect the "favorite" icon.
