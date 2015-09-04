User profile
====================

Once you are logged in, you can access the user profile by clicking your name in the top right corner of the screen.

In the user profile, there are two main tabs: signing keys and profile.

## Signing keys

Each platform requires different settings and files for configuring signing keys.

### Android

Required elements to add a new Android signing key:

![Android - New key](img/android-key.png "Android - New key")

* **Title:** *(required)* A title for the new key.

* **Alias:** *(required)* A name you will use when you sign your project.

* **Certificate password:** *(required)*

* **Keystore file:** *(required)* A binary file that contains a set of private keys.

* **Keystore password:** *(required)*

For more information about this settings, you can visit <a href=http://developer.android.com/tools/publishing/app-signing.html target="_blank">Android Developers</a> site.

### iOS

Required elements to add a new iOS signing key:

![iOS - New key](img/ios-key.png "iOS - New key")

* **Title:** *(required)* A title for the new key.

* **Password:** *(required)*

* **<a href=https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html target="_blank">Provisioning profile</a>:** *(required)*

The provisioning profile must be Distribution one. You can create an "Ad Hoc" provisioning profile if you plan you distribute it internally to a group of persons or an "App Store" provisioning profile for uploading the final app to the Apple App Store.

Always use a Distribution Provisioning Profile.

![Provisioning profile](img/signing-ios-provisioning.png "Always use a distribution provisioning profile")

* **<a href=https://developer.apple.com/support/technical/certificates/ target="_blank">Certificate (p12) file</a>:** *(required)*

The Signing certificate must be a production one either you are creating an "Ad Hoc" IPA or an IPA to upload to the Apple App Store.

Always use a Production Signing Certificate.

![Signing certificate](img/signing-ios-cert.png "Always user a production signing certificate")

## Profile

At the user profile tab, it is possible to configure the following information:

![User profile](img/profile-info.png "User profile")

* **Username:** *(required)* Shown at the [forums](https://forums.cocoon.io).

* **Name:** *(required)* Your name.

* **Last name:** *(optional)* Your last name.

* **Email:** *(required)* Email in which to receive the logs and notifications.

From the user profile it is also possible to *change your password* and, soon, *upgrade* the user plan.

Remember to read the Terms of Use and Privacy policy and save your changes before leaving the user profile.

<!--## Delete a user account

You can delete your user account whenever you want. However, if a user account is deleted, all data linked to that account will be removed from our servers, including the projects, the source code, the compilations and, of course, the signing keys.

Please, ensure you have a copy of all the relevant data before deleting it, because it can't be recovered. -->
