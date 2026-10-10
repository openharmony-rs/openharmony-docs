# Updating Assets in Batches (ArkTS)

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @HarMonkey-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=4406a1fcebfd3a8963726b8dfa66bed58dd98b9c translatedAt=2026-10-09T01:16:12.574Z pushedAt=2026-10-09T11:03:51.832Z -->

## Available APIs

Since version 26.0.0, the system provides the asynchronous API [batchUpdate](../../reference/apis-asset-store-kit/js-apis-asset.md#assetbatchupdate) for you to update assets in batches.

The following table describes the attributes of **AssetMap** for updating assets in batches.

> **NOTE**
>
> In the following table, the attributes **ALIAS** and those starting with **DATA_LABEL** are custom asset attributes reserved for services. These attributes are not encrypted. Therefore, do not put sensitive personal data in these attributes.

- Attributes in **sourceAttributes**:

  | Attribute Name (Tag) | Attribute Content (Value) | Required | Remarks |
  | --------------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------ |
  | ALIAS                 | Type: Uint8Array, length 1-256 bytes.                        | Required | Alias of the asset, which is the unique index of each asset. |
  | ACCESSIBILITY         | Type: number. For the value range, see [Accessibility](../../reference/apis-asset-store-kit/js-apis-asset.md#accessibility). | Optional | Access control based on the lock screen status. |
  | REQUIRE_PASSWORD_SET  | Type: boolean.                                               | Optional | Whether the asset can be accessed only when a lock screen password is set. The value **true** indicates updating assets that can be accessed only when the user has set a lock screen password; the value **false** indicates updating assets that can be accessed regardless of whether the user has set a lock screen password. |
  | AUTH_TYPE             | Type: number. For the value range, see [AuthType](../../reference/apis-asset-store-kit/js-apis-asset.md#authtype). | Optional | Type of user authentication required to access the asset. |
  | SYNC_TYPE             | Type: number. For the value range, see [SyncType](../../reference/apis-asset-store-kit/js-apis-asset.md#synctype). | Optional | Synchronization type supported by the asset. |
  | IS_PERSISTENT         | Type: boolean.                                               | Optional | Whether to retain the asset when the application is uninstalled. The value **true** indicates updating assets that are retained after the application is uninstalled; the value **false** indicates updating assets that are deleted after the application is uninstalled. |
  | DATA_LABEL_CRITICAL_1 | Type: Uint8Array, length 1-2048 bytes.                       | Optional | Attached information of the asset. The content is customized by business and has integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_CRITICAL_2 | Type: Uint8Array, length 1-2048 bytes.                       | Optional | Attached information of the asset. The content is customized by business and has integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_CRITICAL_3 | Type: Uint8Array, length 1-2048 bytes.                       | Optional | Attached information of the asset. The content is customized by business and has integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_CRITICAL_4 | Type: Uint8Array, length 1-2048 bytes.                       | Optional | Attached information of the asset. The content is customized by business and has integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_NORMAL_1   | Type: Uint8Array, length 1-2048 bytes.                       | Optional | Attached information of the asset. The content is customized by business and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_NORMAL_2   | Type: Uint8Array, length 1-2048 bytes.                       | Optional | Attached information of the asset. The content is customized by business and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_NORMAL_3   | Type: Uint8Array, length 1-2048 bytes.                       | Optional | Attached information of the asset. The content is customized by business and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_NORMAL_4   | Type: Uint8Array, length 1-2048 bytes.                       | Optional | Attached information of the asset. The content is customized by business and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1-512 bytes. |
  | DATA_LABEL_NORMAL_LOCAL_1<sup>12+</sup> | Type: Uint8Array, length 1-2048 bytes. | Optional | Local information attached to the asset. The content is customized by business and has no integrity protection. This information will not be synchronized. |
  | DATA_LABEL_NORMAL_LOCAL_2<sup>12+</sup> | Type: Uint8Array, length 1-2048 bytes. | Optional | Local information attached to the asset. The content is customized by business and has no integrity protection. This information will not be synchronized. |
  | DATA_LABEL_NORMAL_LOCAL_3<sup>12+</sup> | Type: Uint8Array, length 1-2048 bytes. | Optional | Local information attached to the asset. The content is customized by business and has no integrity protection. This information will not be synchronized. |
  | DATA_LABEL_NORMAL_LOCAL_4<sup>12+</sup> | Type: Uint8Array, length 1-2048 bytes. | Optional | Local information attached to the asset. The content is customized by business and has no integrity protection. This information will not be synchronized. |
  | REQUIRE_ATTR_ENCRYPTED<sup>14+</sup> | Type: boolean. | Optional | Whether to update data whose business-customized attached information is encrypted. The value **true** indicates updating data whose business-customized attached information is stored encrypted; the value **false** indicates updating data whose business-customized attached information is stored unencrypted. The default value is **false**. |
  | GROUP_ID<sup>18+</sup> | Type: Uint8Array, length 7-127 bytes. | Optional | Group to which the asset to be updated belongs. By default, assets that do not belong to any group are updated. |

- Attributes in **destAttributes**:

  | Attribute Name (Tag)       | Value                     | Mandatory | Description                                                        |
  | --------------------- | -------------------------------| -------- | ------------------------------- |
  | SECRET                | Type: Uint8Array<br>Length: 1-1024 bytes                          | No    | Asset in plaintext.                                                |
  | DATA_LABEL_NORMAL_1   | The type is Uint8Array, and the length is 1 to 2048 bytes.                        | Optional     | Attached information of the asset. The content is defined by the service and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1 to 512 bytes. |
  | DATA_LABEL_NORMAL_2   | The type is Uint8Array, and the length is 1 to 2048 bytes.                        | Optional     | Attached information of the asset. The content is defined by the service and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1 to 512 bytes. |
  | DATA_LABEL_NORMAL_3   | The type is Uint8Array, and the length is 1 to 2048 bytes.                        | Optional     | Attached information of the asset. The content is defined by the service and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1 to 512 bytes. |
  | DATA_LABEL_NORMAL_4   | The type is Uint8Array, and the length is 1 to 2048 bytes.                        | Optional     | Attached information of the asset. The content is defined by the service and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1 to 512 bytes. |
  | DATA_LABEL_NORMAL_LOCAL_1<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local information attached to the asset. The value is assigned by the service without integrity protection and will not be synced.|
  | DATA_LABEL_NORMAL_LOCAL_2<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local information attached to the asset. The value is assigned by the service without integrity protection and will not be synced.|
  | DATA_LABEL_NORMAL_LOCAL_3<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local information attached to the asset. The value is assigned by the service without integrity protection and will not be synced.|
  | DATA_LABEL_NORMAL_LOCAL_4<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local information attached to the asset. The value is assigned by the service without integrity protection and will not be synced.|

## Constraints

The assets to be updated in batches must have the same [GROUP_ID](../../reference/apis-asset-store-kit/js-apis-asset.md#tag) and [REQUIRE_ATTR_ENCRYPTED](../../reference/apis-asset-store-kit/js-apis-asset.md#tag) attributes.

A maximum of 100 assets can be updated in batches.

## Development Procedure

> **NOTE**
>
> The following is an example of using the batch update API.
>
> Before updating an asset, ensure that the asset exists. For details about how to add an asset, see [Adding an Asset](asset-js-add.md). Otherwise, the **NOT_FOUND** error (24000002) is reported.

Update two assets in batches. Update the plaintext of the assets whose aliases are **demo_alias1** and **demo_alias2** to **demo_pwd_new1** and **demo_pwd_new2**, respectively.

1. Include the header file and define the tool function.
   <!-- @[import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/batch_operation.ets) -->

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
   <!-- @[batch_update](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/batch_operation.ets) -->

   ``` TypeScript
   let srcAttrs: asset.AssetMap[] = [];
   let srcAttr1: asset.AssetMap = new Map();
   srcAttr1.set(asset.Tag.ALIAS, stringToArray('demo_alias1'));
   srcAttrs.push(srcAttr1);
   let srcAttr2: asset.AssetMap = new Map();
   srcAttr2.set(asset.Tag.ALIAS, stringToArray('demo_alias2'));
   srcAttrs.push(srcAttr2);
   
   let destAttrs: asset.AssetMap[] = [];
   let destAttr1: asset.AssetMap = new Map();
   destAttr1.set(asset.Tag.SECRET, stringToArray('demo_pwd_new1'));
   destAttrs.push(destAttr1);
   let destAttr2: asset.AssetMap = new Map();
   destAttr2.set(asset.Tag.SECRET, stringToArray('demo_pwd_new2'));
   destAttrs.push(destAttr2);
   
   try {
     asset.batchUpdate(srcAttrs, destAttrs).then((res: asset.BatchResult) => {
       console.info(`Succeeded in batch updating Asset, failedCount: ${res.failedCount}`);
       if (res.failedCount > 0) {
         for (let i = 0; i < res.failedErrorInfos.length; i++) {
           console.error(`Failed to update Asset at index ${res.failedErrorInfos[i].index},
             errCode: ${res.failedErrorInfos[i].errCode}, message: ${res.failedErrorInfos[i].message}`);
         }
       }
     }).catch((err: BusinessError) => {
       console.error(`Failed to batch update Asset. Code is ${err.code}, message is ${err.message}`);
     })
   } catch (error) {
     let err = error as BusinessError;
     console.error(`Failed to batch update Asset. Code is ${err.code}, message is ${err.message}`);
   }
   ```