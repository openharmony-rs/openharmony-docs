# Updating an Asset (ArkTS)

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @yhf-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=4406a1fcebfd3a8963726b8dfa66bed58dd98b9c translatedAt=2026-10-09T01:21:02.521Z pushedAt=2026-10-09T11:27:06.667Z -->

## Available APIs

You can use [update(query: AssetMap, attributesToUpdate: AssetMap)](../../reference/apis-asset-store-kit/js-apis-asset.md#assetupdate) (asynchronous API) or [updateSync(query: AssetMap, attributesToUpdate: AssetMap)](../../reference/apis-asset-store-kit/js-apis-asset.md#assetupdatesync12) (synchronous API) to update an asset.

The following table describes the attributes of **AssetMap** for updating an asset.

> **NOTE**
>
> In the following table, the attributes **ALIAS** and those containing **DATA_LABEL** are custom asset attributes reserved for services. These attributes are not encrypted. Therefore, do not put sensitive personal data in these attributes.

- Attributes in **query**:

  | Attribute Name (Tag)       | Value                                            | Mandatory | Description                                            |
  | --------------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------ |
  | ALIAS                 | Type: Uint8Array<br>Length: 1-256 bytes                           | Yes    | Asset alias, which uniquely identifies an asset.          |
  | ACCESSIBILITY         | Type: number<br>Value range: see [Accessibility](../../reference/apis-asset-store-kit/js-apis-asset.md#accessibility)| No    | Access control based on the lock screen status.                                    |
  | REQUIRE_PASSWORD_SET  | Type: Boolean                                                  | No    | Whether the asset is accessible only when a lock screen password is set. The value **true** means to update the asset accessible only when a lock screen password is set. The value **false** means to update the asset that can be accessed regardless of whether a lock screen password is set.    |
  | AUTH_TYPE             | Type: number<br>Value range: see [AuthType](../../reference/apis-asset-store-kit/js-apis-asset.md#authtype)| No    | Type of user authentication required for accessing the asset.                  |
  | SYNC_TYPE             | Type: number<br>Value range: see [SyncType](../../reference/apis-asset-store-kit/js-apis-asset.md#synctype)| No    | Asset sync type.                          |
  | IS_PERSISTENT         | Type: Boolean                                                  | No    | Whether to retain the asset when the application is uninstalled. The value **true** means to retain the asset even after the application is uninstalled. The value **false** means the opposite.              |
  | DATA_LABEL_CRITICAL_1 | Type: Uint8Array, length: 1-2048 bytes.                        | Optional     | Attached information of a key asset. The content is defined by business and has integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_CRITICAL_2 | Type: Uint8Array, length: 1-2048 bytes.                        | Optional     | Attached information of a key asset. The content is defined by business and has integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_CRITICAL_3 | Type: Uint8Array, length: 1-2048 bytes.                       | Optional     | Attached information of a key asset. The content is defined by business and has integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_CRITICAL_4 | Type: Uint8Array, length: 1-2048 bytes.                        | Optional     | Attached information of a key asset. The content is defined by business and has integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_NORMAL_1   | Type: Uint8Array, length: 1-2048 bytes.                        | Optional     | Attached information of a key asset. The content is defined by business and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_NORMAL_2   | Type: Uint8Array, length: 1-2048 bytes.                        | Optional     | Attached information of a key asset. The content is defined by business and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_NORMAL_3   | Type: Uint8Array, length: 1-2048 bytes.                        | Optional     | Attached information of a key asset. The content is defined by business and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_NORMAL_4   | Type: Uint8Array, length: 1-2048 bytes.                        | Optional     | Attached information of a key asset. The content is defined by business and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_NORMAL_LOCAL_1<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local information attached to the asset.  The value is assigned by the service without integrity protection and will not be synced.|
  | DATA_LABEL_NORMAL_LOCAL_2<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local information attached to the asset.  The value is assigned by the service without integrity protection and will not be synced.|
  | DATA_LABEL_NORMAL_LOCAL_3<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local information attached to the asset.  The value is assigned by the service without integrity protection and will not be synced.|
  | DATA_LABEL_NORMAL_LOCAL_4<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local information attached to the asset.  The value is assigned by the service without integrity protection and will not be synced.|
  | REQUIRE_ATTR_ENCRYPTED<sup>14+</sup> | Type: Boolean| No| Whether to update encrypted data of service-defined additional information. The value **true** means to update the service-defined additional information stored in encrypted form; the value **false** means to update the service-defined additional information stored in unencrypted form.  Default value: **false**.|
  | GROUP_ID<sup>18+</sup> | Type: Uint8Array<br>Length: 7-127 bytes| No| Group to which the asset to be updated belongs. By default, the asset that does not belong to any group is updated.|

- Attributes in **attributesToUpdate**:

  | Attribute Name (Tag)       | Value                     | Mandatory | Description                                                        |
  | --------------------- | -------------------------------| -------- | ------------------------------- |
  | SECRET                | Type: Uint8Array<br>Length: 1-1024 bytes                          | No    | Asset in plaintext.                                                |
  | DATA_LABEL_NORMAL_1   | Type: Uint8Array, length: 1-2048 bytes.                        | Optional     | Attached information of the asset. The content is defined by the business and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_NORMAL_2   | Type: Uint8Array, length: 1-2048 bytes.                        | Optional     | Attached information of the asset. The content is defined by the business and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_NORMAL_3   | Type: Uint8Array, length: 1-2048 bytes.                        | Optional     | Attached information of the asset. The content is defined by the business and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_NORMAL_4   | Type: Uint8Array, length: 1-2048 bytes.                        | Optional     | Attached information of the asset. The content is defined by the business and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_NORMAL_LOCAL_1<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local information attached to the asset.  The value is assigned by the service without integrity protection and will not be synced.|
  | DATA_LABEL_NORMAL_LOCAL_2<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local information attached to the asset.  The value is assigned by the service without integrity protection and will not be synced.|
  | DATA_LABEL_NORMAL_LOCAL_3<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local information attached to the asset.  The value is assigned by the service without integrity protection and will not be synced.|
  | DATA_LABEL_NORMAL_LOCAL_4<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local information attached to the asset.  The value is assigned by the service without integrity protection and will not be synced.|

## Example

> **NOTE**
>
> This module provides asynchronous and synchronous APIs. The following uses the asynchronous APIs as an example. For more information about the APIs, see [@ohos.security.asset (Asset Store Service)](../../reference/apis-asset-store-kit/js-apis-asset.md).
>
> For details about how to update an asset in a group, see [Updating an asset in a Group](asset-js-group-access-control.md#updating-an-asset-in-a-group).
>
> Before updating an asset, ensure that the asset exists. For details about how to add an asset, see [Adding an Asset](asset-js-add.md). Otherwise, the **NOT_FOUND** error (24000002) is reported.

Update asset **demo_alias** as follows: change the asset plaintext to **demo_pwd_new** and additional attribute to **demo_label_new**.

1. Include the header file and define the tool function.
   <!-- @[import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/update.ets) -->

   ``` TypeScript
   import { asset } from '@kit.AssetStoreKit';
   import { util } from '@kit.ArkTS';
   import { BusinessError } from '@kit.BasicServicesKit';
   
   function stringToArray(str: string): Uint8Array {
     let textEncoder = new util.TextEncoder();
     return textEncoder.encodeInto(str);
   }
   ```

2. Develop the desired feature.
   <!-- @[update_asset](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/update.ets) -->

   ``` TypeScript
   let query: asset.AssetMap = new Map();
   query.set(asset.Tag.ALIAS, stringToArray('demo_alias'));
   let attrsToUpdate: asset.AssetMap = new Map();
   attrsToUpdate.set(asset.Tag.SECRET, stringToArray('demo_pwd_new'));
   attrsToUpdate.set(asset.Tag.DATA_LABEL_NORMAL_1, stringToArray('demo_label_new'));
   try {
     asset.update(query, attrsToUpdate).then(() => {
       console.info(`Succeeded in updating Asset.`);
       // ...
     }).catch((err: BusinessError) => {
       console.error(`Failed to update Asset. Code is ${err.code}, message is ${err.message}`);
       // ...
     });
   } catch (error) {
     let err = error as BusinessError;
     console.error(`Failed to update Asset. Code is ${err.code}, message is ${err.message}`);
     // ...
   }
   ```

