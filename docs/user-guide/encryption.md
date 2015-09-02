Encryption
==================

The encryption feature allows you to cipher your application assets using a key. This a Gold feature, if you don't have a Gold Plan, please upgrade to get this feature available.

The encryption feature is completely transparent to the developer. It is initially disabled until you generate a new encryption key. If the encryption key is left empty, the encryption is disabled.


Encryption is supported in the following Webview Engines:
- Canvas+ iOS
- Canvas+ Android
- System Webview iOS
- System Webview Android
- Webview+ Android

Encryption for Webview+ iOS is not yet supported.

![[class='center'] Plugins installation](img/encryption-upgrade.png "Upgrade to Gold plan to get encryption support")

## Enable encryption

To enable the encryption for your project, just set a key manually or generate a random key using the key generation button.

![[class='center'] Plugins installation](img/encryption-key.png "Set a key to add encryption support")

Once a key has been set, just click "Save" to enable encryption and set the key. You can now compile your application and all your code and assets will be encrypted using that key.

![[class='center'] Plugins installation](img/encryption-save.png "Save the key to enable encryption")

You can change your encryption key at any time setting a new key.

## Disable encryption

To disable encryption just remove the encryption key and save.

![[class='center'] Plugins installation](img/encryption-unset.png "To disable encryption leave the key empty")

## Supported assets

Encryption feature supports ciphering files with any of the following extensions:

- js
- xml
- json
- png
- jpg

The rest of the resources will remain unencrypted.
