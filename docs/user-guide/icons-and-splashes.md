Icons and Splashes
==================

This section shows how to configure an app's icons and optional splash screen for the supported platforms. This configuration will be similar to another Cordova based project.

## Automatic generation

This is the easiest way of adding icons and splashes to your project.

### Generating icons

To generate the icons, it is just necessary to drag and drop a PNG image and the cloud will generate all the resources your project requires for all the platforms. The recommended size is 1024x1024, so the image won't lose quality.

![[class='center'] Adding icons](img/icons-wizard.png "Adding icons")

If you don't want to use this system, you can always add the icons manually editing the config file using the editor.

### Generating Splashes

To generate the splashes for your project, just drag and drop the resources in the dragging and dropping area of the splash menu in the project settings. In is not necessary to install additional plugins.

Once the resources are loaded at the cloud, it is possible to customize them.

![[class='center'] Adding splashes](img/splash-wizard.png "Adding splashes")

You can upload an icon and place it in the center with a fixed background color you can select directly on the settings. If you want a custom background we recommend that you select a 2048x2048 PNG where the logo or other important artwork is placed within the center 1000x1000 pixels or so. In any case, you can simulate how the splash would look like after compilation using the device simulator (the device icon just next to the dragging and dropping area).

![[class='center'] Device simulator](img/device-simulator.png "Device simulator")

Remember to save or discard the changes before compiling.

**Note**: In iOS apps, the user splash will also be used as the [Launch image](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/LaunchImages.html), this is something mandatory for any iOS app. In case you want to have only Launch Image and no user splash, you can configure an splash and set the delay to 0.

## Manual configuration

### Configuring Icons

You can define app icon(s) via the *icon* element in the [config.xml](/user-guide/project-configuration) file. If you do not specify an icon the Cocoon compiler will set some default icons for you. The following configuration can be used to define single default icon which will be used for all platforms. As you can see, the src attribute is mandatory and the minimum one required.

    <icon src="res/icon.png" />

* **src:** *(required)* specifies the location of the image file, relative to your project directory.

It is important to notice that, as it is said in the description, the src attribute is relative to the project directory and not to the www directory. You can name the source image whatever you like.

Apart from this compulsory attribute there are also several optional ones. Here it is a more complete example showing how to use them:  

	<icon src="res/ios/icon.png" platform="ios" width="57" height="57" density="mdpi" />

* **platform:** *(optional)* target platform.

* **width:** *(optional)* icon width in pixels.

* **height:** *(optional)* icon height in pixels.

* **density:** *(optional)* android specific, specifies icon density.

In additon, for each platform you can also define a pixel-perfect icons set to fit different screen resolutions using a combination of the *platform* element and the *name* label.

This example is specific for Android:

    <platform name="android">
        <icon src="res/android/ldpi.png" density="ldpi" />
        <icon src="res/android/mdpi.png" density="mdpi" />
        <icon src="res/android/hdpi.png" density="hdpi" />
        <icon src="res/android/xhdpi.png" density="xhdpi" />
        <icon src="res/android/xxhdpi.png" density="xxhdpi" />
        <icon src="res/android/xxxhdpi.png" density="xxxhdpi" />
    </platform>

And this one is for iOS:

    <platform name="ios">
        <!-- iOS 8.0+ -->
        <!-- iPhone 6 Plus  -->
        <icon src="res/ios/icon-60@3x.png" width="180" height="180" />
        <!-- iOS 7.0+ -->
        <!-- iPhone / iPod Touch  -->
        <icon src="res/ios/icon-60.png" width="60" height="60" />
        <icon src="res/ios/icon-60@2x.png" width="120" height="120" />
        <!-- iPad -->
        <icon src="res/ios/icon-76.png" width="76" height="76" />
        <icon src="res/ios/icon-76@2x.png" width="152" height="152" />
        <!-- iOS 6.1 -->
        <!-- Spotlight Icon -->
        <icon src="res/ios/icon-40.png" width="40" height="40" />
        <icon src="res/ios/icon-40@2x.png" width="80" height="80" />
        <!-- iPhone / iPod Touch -->
        <icon src="res/ios/icon.png" width="57" height="57" />
        <icon src="res/ios/icon@2x.png" width="114" height="114" />
        <!-- iPad -->
        <icon src="res/ios/icon-72.png" width="72" height="72" />
        <icon src="res/ios/icon-72@2x.png" width="144" height="144" />
        <!-- iPhone Spotlight and Settings Icon -->
        <icon src="res/ios/icon-small.png" width="29" height="29" />
        <icon src="res/ios/icon-small@2x.png" width="58" height="58" />
        <!-- iPad Spotlight and Settings Icon -->
        <icon src="res/ios/icon-50.png" width="50" height="50" />
        <icon src="res/ios/icon-50@2x.png" width="100" height="100" />
    </platform>

If you want more information regarding different platforms, please, see the Cordova section for [configuring icons](http://cordova.apache.org/docs/en/4.0.0/config_ref_images.md.html#Icons%20and%20Splash%20Screens_configuring_icons_in_the_cli).

### Configuring Splashes

If you want your project to have a custom splash screen but you don't want to use the automatic generation, it is necessary to install this plugin in your project: <a href=https://github.com/apache/cordova-plugin-splashscreen target="_blank">cordova-plugin-splashscreen</a>.

It is possible to install it using the wizard. However, there are two preferences that must be added to the config.xml by the user:

    <!-- Splash screen -->
    <preference name="SplashScreen" value="screen" />

    <!-- Splash screen delay -->
    <preference name="SplashScreenDelay" value="5000" />

In addition, it is important to mention that this plugin works different on iOS devices. On iOS, it is necessary to add this slice of code in your project, for example, in the index.html to hide the Splash:

    document.addEventListener("deviceready", function() {
        setTimeout(function() {
            navigator.splashscreen.hide();
        }, 5000, false);
    });

Otherwise, the splash screen will be stuck and always visible. On Android devices, the plugin will work fine even if this code is not present.

The configuration of the splashes is done in the config.xml file and all the attributes mentioned in the previous section are available, including the src attribute which, as in the icons configuration, it is compulsory.

The following example shows how to create the splash screen for an Android project:

	<platform name="android">
        <splash src="res/screen/android/drawable-land-hdpi/screen.png" density="land-hdpi" />
        <splash src="res/screen/android/drawable-land-ldpi/screen.png" density="land-ldpi" />
        <splash src="res/screen/android/drawable-land-mdpi/screen.png" density="land-mdpi" />
        <splash src="res/screen/android/drawable-land-xhdpi/screen.png" density="land-xhdpi" />
        <splash src="res/screen/android/drawable-port-hdpi/screen.png" density="port-hdpi" />
        <splash src="res/screen/android/drawable-port-ldpi/screen.png" density="port-ldpi" />
        <splash src="res/screen/android/drawable-port-mdpi/screen.png" density="port-mdpi" />
        <splash src="res/screen/android/drawable-port-xhdpi/screen.png" density="port-xhdpi" />
    </platform>

And this is an example for an iOS project:

    <platform name="ios">
        <splash height="480" src="res/screen/ios/Default~iphone.png" width="320" />
        <splash height="1136" src="res/screen/ios/Default-568h@2x~iphone.png" width="640" />
        <splash height="1024" src="res/screen/ios/Default-Portrait~ipad.png" width="768" />
        <splash height="768" src="res/screen/ios/Default-Landscape~ipad.png" width="1024" />
        <splash height="1334" src="res/screen/ios/Default-667h.png" width="750" />
        <splash height="2048" src="res/screen/ios/Default-Portrait@2x~ipad.png" width="1536" />
        <splash height="2208" src="res/screen/ios/Default-736h.png" width="1242" />
        <splash height="1242" src="res/screen/ios/Default-Landscape-736h.png" width="2208" />
        <splash height="960" src="res/screen/ios/Default@2x~iphone.png" width="640" />
        <splash height="1536" src="res/screen/ios/Default-Landscape@2x~ipad.png" width="2048" />
    </platform>

If you want more information regarding different platforms and which image sizes are supported in each of them, here you will find a <a href=http://cordova.apache.org/docs/en/4.0.0/config_ref_images.md.html#Example%2520configuration target="_blank">complete example</a>.
