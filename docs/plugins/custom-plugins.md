Custom plugins
=======================

It is possible to add custom plugins to a project under certain conditions.

## Requirements

First of all, they must be on a public github repository. In the future it will be possible to add private plugins, but that feature is not available at the moment.

In addition, those plugins can't have hooks. They are not supported yet. Any present hook will be ignored.

If you plan to add a custom Cordova plugin,  you must take into account that it is necessary to adapt those plugins to run with Cordova Android 4.0.x. and Cordova iOS 4.0.x

## Installation

You can add a custom plugin either using the cloud interface in the project configuration or editing the config.xml directly.

In the project detail page, select the custom tab. You'll find a form to synchronize a github repository with your project. Just fill the required information and click on the installation button.

![[class='center'] Custom plugins](img/custom_plugins.png "Custom plugins")

If you prefer to update manually, select the config.xml tab and add the following line

##### Example
    <cocoon:plugin name="https://github.com/USERNAME/PROJECT.git[#branch]" />

After the custom plugin is added to your project, it can be configured, edited and removed as any other plugin.  
