Getting started
==================

This section will guide you in your first steps using Cocoon services. First of all, you must log in the system.

## Login process

In order to use our services, it is required to get an invitation. For requesting an invitation, please, sign up <a href=https://cocoon.io target="_blank">here</a>. After receiving it, you will get access as a free user and you can log in the system using a Gmail account, a Github account or a Cocoon account.

To learn more about the different accounts and user plans, you can visit the [user profile](/user-guide/user-profile) section.

## The cloud compiler

As soon as you are logged in, you will have access to the [cloud compiler](/user-guide/project-creation). Creating a project is easier than ever using the guided creation wizard.

In addition, it is possible to create a project dragging and dropping content of your cordova based project www folder compressed in a zip folder or using a github public repository that has a cordova structure. If you want to know more about the project creation process, have a look at this [section](/user-guide/project-creation).

It is important to notice that Cocoon.io compiler is based on [Cordova](/faq#what-is-cordova-). Cordova needs an initialization of the environment, and this is performed using the cordova library (using a cordova.js file). Thus, the cordova.js file must be referred in your index.html file.

This file will be added during compilation, so it is enought if you copy and paste this line in your code:
```
<script src="cordova.js"></script>
```
In addition, this library exposes an event ([ondeviceready](https://cordova.apache.org/docs/en/4.0.0/cordova_events_events.md.html#deviceready)) that signals that Cordova's device APIs have loaded and are ready to access. Thus, remember to wait for the deviceready event before running your code.

Once the project is created, you will be able to edit and save changes in the config.xml directly at the cloud. You can edit the config.xml directly, or using the UI in the project detail page. You can also  download the source code of your project whenever you want.

In addition, if you include a signing key in your [user profile](/user-guide/user-profile) and you select it from the [project configuration](/user-guide/project-configuration), after compilation you will get your project already signed for uploading it to the stores.

It is also possible to include a signing key directly on a project. Automatically, that key will be linked to the user profile. If the key is removed from the profile, it will be automatically deleted from any project in which that key is included.

To learn more about the cloud compiler and its features, you can visit the [cloud compiler](/user-guide/project-creation) section.

## Platforms

A platform is a group of technologies that are used as a base upon which other applications, processes or technologies are developed.

Currently the supported platforms are iOS and Android for mobile devices, but it is in our plans to increase this list along time to include, for example, wearables and more OS, as many plugins already support other OS.

To learn more about how to choose a platform, you can visit the [platforms](/user-guide/platforms) section.

## Plugins

A plugin is a package of injected code that allows the webview engines to communicate with the host mobile OS. Adding plugins will extend your project's features. Using them, you will be able to include in your project from in-app purchases and ads to monetize your app, to social integration, analytics or something easier, such as camera features.

To learn more about which plugins are supported and how to add them to your project, you can visit the [plugins](/plugins) section.

## Webview engines

There are three webview engines available to build your project with. Depending on the nature of the project, you might prefer one or another. You can pick between:
* **Canvas+**, which is specifically designed for games and the increase of the performance but it has some features limited, like DOM access. More info [here](/webview-engines/canvas-plus)
* **Webview+**, which has more features than Canvas+, less performance but still a pretty good one and it is more suitable for web apps.More info [here](/webview-engines/webview-plus)
* **System Webview**, which is the one that device itself has inside. More info [here](/webview-engines/system-webview)

To learn more about these webview engines, you can visit the [webview engines](/webview-engines) section.

## Questions and problem solving  

* You can visit our [FAQ](/faq) page to see if your questions is answered there.

* You can ask in our [forums](https://forums.cocoon.io) to the rest of the users. Our team members will be there too.
