# Updating Assets in Batches (ArkTS)

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @JeremyXu-->
<!--Designer: @skye_you-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

## Available APIs

Since version 26.0.0, the system provides the asynchronous API [batchUpdate](../../reference/apis-asset-store-kit/js-apis-asset.md#assetbatchupdate) for you to update assets in batches.

The following table describes the attributes of **AssetMap** for updating assets in batches.

> **NOTE**
>
> In the following table, the attributes **ALIAS** and those starting with **DATA_LABEL** are custom asset attributes reserved for services. These attributes are not encrypted. Therefore, do not put sensitive personal data in these attributes.

- Attributes in **sourceAttributes**:

  | Attribute Name (Tag)       | Value                                            | Mandatory | Description                                            |
  | --------------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------ |
  | ALIAS                 | Type: Uint8Array<br>Length: 1-256 bytes                           | Yes    | Asset alias, which uniquely identifies an asset.          |
  | ACCESSIBILITY         | Type: number<br>Value range: see [Accessibility](../../reference/apis-asset-store-kit/js-apis-asset.md#accessibility)| No    | Access control based on the lock screen status.                                    |
  | REQUIRE_PASSWORD_SET  | Type: Boolean                                                  | No    | Whether the asset is accessible only when a lock screen password is set. The value **true** means the asset is accessible only when a lock screen password is set. The value **false** means that the asset can be accessed regardless of whether a lock screen password is set.    |
  | AUTH_TYPE             | Type: number<br>Value range: see [AuthType](../../reference/apis-asset-store-kit/js-apis-asset.md#authtype)| No    | Type of user authentication required for accessing the asset.                  |
  | SYNC_TYPE             | Type: number<br>Value range: see [SyncType](../../reference/apis-asset-store-kit/js-apis-asset.md#synctype)| No    | Type of sync supported by the asset.                          |
  | IS_PERSISTENT         | Type: Boolean                                                  | No    | Whether to retain the asset when the application is uninstalled. The value **true** means to retain the asset even after the application is uninstalled. The value **false** means the opposite.              |
  | DATA_LABEL_CRITICAL_1 | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service with integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | DATA_LABEL_CRITICAL_2 | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service with integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | DATA_LABEL_CRITICAL_3 | Type: Uint8Array<br>Length: 1-2048 bytes                      | No    | Asset attribute information customized by the service with integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | DATA_LABEL_CRITICAL_4 | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service with integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | DATA_LABEL_NORMAL_1   | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | DATA_LABEL_NORMAL_2   | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | DATA_LABEL_NORMAL_3   | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | DATA_LABEL_NORMAL_4   | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | DATA_LABEL_NORMAL_LOCAL_1<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
  | DATA_LABEL_NORMAL_LOCAL_2<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
  | DATA_LABEL_NORMAL_LOCAL_3<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
  | DATA_LABEL_NORMAL_LOCAL_4<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
  | REQUIRE_ATTR_ENCRYPTED<sup>14+</sup> | Type: Boolean| No| Whether to update the encrypted data of service customized supplementary information. The value **true** means to update the encrypted data of service customized supplementary information; the value **false** means to update the non-encrypted data of service customized supplementary information. The default value is **false**.|
  | GROUP_ID<sup>18+</sup> | Type: Uint8Array<br>Length: 7-127 bytes| No| Group to which the asset to be updated belongs. By default, this parameter is not specified.|

- Attributes in **destAttributes**:

  | Attribute Name (Tag)       | Value                     | Mandatory | Description                                                        |
  | --------------------- | -------------------------------| -------- | ------------------------------- |
  | SECRET                | Type: Uint8Array<br>Length: 1-1024 bytes                          | No    | Asset in plaintext.                                                |
  | DATA_LABEL_NORMAL_1   | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | DATA_LABEL_NORMAL_2   | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | DATA_LABEL_NORMAL_3   | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | DATA_LABEL_NORMAL_4   | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | DATA_LABEL_NORMAL_LOCAL_1<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
  | DATA_LABEL_NORMAL_LOCAL_2<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
  | DATA_LABEL_NORMAL_LOCAL_3<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
  | DATA_LABEL_NORMAL_LOCAL_4<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|

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
<!--no_check-->