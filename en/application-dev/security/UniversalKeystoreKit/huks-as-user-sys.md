# Specifying the User for Key Operations (for System Applications Only)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

To implement isolation and access control for key data, HUKS provides APIs with the user ID specified for concurrent key operations initiated by multiple users.

>**NOTE**<br>
> The mini-system devices do not support the operation described in this topic.

## Constraints

- The range of the caller user ID is **0** to **99**, including **0** and **99**.
- The APIs are available only for system applications.

## Available APIs

APIs with the **userId** parameter are provided as enhancement to existing APIs.

When using these APIs, observe the following:

1. You can pass in [HUKS_TAG_AUTH_STORAGE_LEVEL](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_authstoragelevel) in **options** to specify the security level for the key stored.
2. If you do not pass [HUKS_TAG_AUTH_STORAGE_LEVEL](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_authstoragelevel) in **options**, this API uses the key in the CE storage area corresponding to the specified **userId** by default, which is equivalent to passing in [HUKS_AUTH_STORAGE_LEVEL_CE](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_authstoragelevel).

The algorithm specifications and the usage of the APIs are the same as those of the APIs without **userId**.

| API with userId| Description| API Without userId|
| -------- | -------- | ----------| 
| [generateKeyItemAsUser](../../reference/apis-universal-keystore-kit/js-apis-huks-sys.md#huksgeneratekeyitemasuser)              |   Generates a key.          |  [generateKeyItem](huks-key-generation-arkts.md)             |
| [deleteKeyItemAsUser](../../reference/apis-universal-keystore-kit/js-apis-huks-sys.md#huksdeletekeyitemasuser)                  |   Deletes a key.          |  [deleteKeyItem](huks-delete-key-arkts.md)               |
| [importKeyItemAsUser](../../reference/apis-universal-keystore-kit/js-apis-huks-sys.md#huksimportkeyitemasuser)                  |   Imports a key in plaintext.     |  [importKeyItem](huks-import-key-in-plaintext-arkts.md)                |
| [importWrappedKeyItemAsUser](../../reference/apis-universal-keystore-kit/js-apis-huks-sys.md#huksimportwrappedkeyitemasuser)    |  Imports an encrypted key.       |  [importWrappedKeyItem](huks-import-wrapped-key-arkts.md)             |
| [exportKeyItemAsUser](../../reference/apis-universal-keystore-kit/js-apis-huks-sys.md#huksexportkeyitemasuser)                  |   Exports a key.       |  [exportKeyItem](huks-export-key-arkts.md)                |
| [getKeyItemPropertiesAsUser](../../reference/apis-universal-keystore-kit/js-apis-huks-sys.md#huksgetkeyitempropertiesasuser)    |  Obtains key properties.    |  [getKeyItemProperties](huks-obtain-key-properties-arkts.md)             |
| [hasKeyItemAsUser](../../reference/apis-universal-keystore-kit/js-apis-huks-sys.md#hukshaskeyitemasuser)                        |  Checks whether a key exists.   |  [hasKeyItem](huks-check-key-arkts.md)               |
| [initSessionAsUser](../../reference/apis-universal-keystore-kit/js-apis-huks-sys.md#huksinitsessionasuser)                      |  Initializes a key session.      |  initSession in [encryption and decryption](huks-encryption-decryption-arkts.md), [signing and signature verification](huks-signing-signature-verification-arkts.md), [key agreement](huks-key-agreement-arkts.md), and [key derivation](huks-key-derivation-arkts.md)          |
| [attestKeyItemAsUser](../../reference/apis-universal-keystore-kit/js-apis-huks-sys.md#huksattestkeyitemasuser)                  |  Performs non-anonymous key attestation.   |  [attestKeyItem](huks-key-attestation-arkts.md)                |
| [anonAttestKeyItemAsUser](../../reference/apis-universal-keystore-kit/js-apis-huks-sys.md#huksanonattestkeyitemasuser)          | Performs anonymous key attestation.    |  [anonAttestKeyItem](huks-key-anon-attestation-arkts.md)                |
