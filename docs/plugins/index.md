Plugins
==================

A plugin is a package of injected code that allows you to access to device and platform functionalities that are normally unavailable to web-based projects. It consists of a single JavaScript interface along with corresponding native code libraries for each supported platform. In consequence, this hides the various native code implementations behind a common JavaScript interface.

Currently, they are supported all plugins for Cordova which are on the public <a href=http://plugins.cordova.io/npm/index.html?q= target="_blank">plugins registry</a>, and that includes our [Cocoon plugins](/plugins/cocoon-plugins) and [Cocoon webview engines](/webview-engines). If you want to add a [custom plugin](/plugins/custom-plugins), it is possible if it is on a public repository in github.

## Installing a plugin

To install a plugin in your project, it is better to edit the config.xml or to select it from the plugins list at the [project configuration](/user-guide/project-configuration) rather than importing a project with all the plugins already installed. That list will show all the public plugins available from cordova public registry.

To install a plugin directly editing the config.xml file, it is just necessary  to add the cocoon:plugin tag including the full id of the plugin and, if required, a param as, for example, the version:  

	<cocoon:plugin name="cordova-plugin-name" version="plugin_version" />  

* **name:** *(required)* plugin name.
* **version:** *(optional)* plugin version.

Each time you edit the config.xml, remember to save the changes clicking the save button at the end of the editor. Once the changes are saved, it is necessary to complete a new compilation. During that compilation, the plugins included in the config.xml will be added to the project.

## Uninstalling a plugin

In case you want to uninstall a plugin, just remove the line that corresponds to the name of that plugin in the config.xml file. The next compilation won't have that plugin.

It is also possible to uninstall plugins from the plugin list at the [project configuration](/user-guide/project-configuration).
