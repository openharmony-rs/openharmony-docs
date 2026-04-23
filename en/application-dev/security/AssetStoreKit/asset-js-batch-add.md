# Adding Assets in Batches (ArkTS)

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @JeremyXu-->
<!--Designer: @skye_you-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

## Available APIs

Since version 26.0.0, the system provides the asynchronous API [batchAdd](../../reference/apis-asset-store-kit/js-apis-asset.md#assetbatchadd) for you to add assets in batches.

The following table describes the attributes of **AssetMap** for adding assets in batches.

> **NOTE**
>
> In the following table, the attributes **ALIAS** and those starting with **DATA_LABEL** are custom asset attributes reserved for services. These attributes are not encrypted. Therefore, do not put sensitive personal data in these attributes.

| Attribute Name (Tag)       | Value                                            | Mandatory | Description                                                        |
| --------------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| SECRET                | Type: Uint8Array<br>Length: 1-1024 bytes                          | Yes    | Asset in plaintext.                                             |
| ALIAS                 | Type: Uint8Array<br>Length: 1-256 bytes                           | Yes    | Asset alias, which uniquely identifies an asset.                       |
| ACCESSIBILITY         | Type: number<br>Value range: see [Accessibility](../../reference/apis-asset-store-kit/js-apis-asset.md#accessibility)| No    | Access control based on whether the screen is locked. The default value is **DEVICE_FIRST_UNLOCKED**, indicating that the asset can be accessed after the device is unlocked for the first time.     |
| REQUIRE_PASSWORD_SET  | Type: Boolean                                                  | No    | Whether the asset is accessible only when a lock screen password is set. The value **true** means that the asset can be accessed only when the user sets a screen lock password. The value **false** means that the asset can be accessed regardless of whether the user sets a screen lock password. The default value is **false**.             |
| AUTH_TYPE             | Type: number<br>Value range: see [AuthType](../../reference/apis-asset-store-kit/js-apis-asset.md#authtype)| No    | User authentication type required for accessing an asset. The default value is **NONE**, indicating that user authentication is not required before the user accesses an asset.        |
| SYNC_TYPE             | Type: number<br>Value range: see [SyncType](../../reference/apis-asset-store-kit/js-apis-asset.md#synctype)| No    | Sync type supported by the asset. The default value is **NEVER**, indicating that the asset cannot be synced.               |
| IS_PERSISTENT         | Type: Boolean                                                  | No    | Whether to retain the asset when the application is uninstalled. The value **true** means to retain the asset when the application is uninstalled; the value **false** means the opposite. The default value is **false**.<br>**NOTE**: If this parameter is set, the application must [apply for](../AccessToken/declare-permissions.md) the ohos.permission.STORE_PERSISTENT_DATA permission.|
| DATA_LABEL_CRITICAL_1 | Type: Uint8Array<br>Length: 1-2048 bytes                        | No    | Asset attribute information customized by the service with integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
| DATA_LABEL_CRITICAL_2 | Type: Uint8Array<br>Length: 1-2048 bytes                      | No    | Asset attribute information customized by the service with integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
| DATA_LABEL_CRITICAL_3 | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service with integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
| DATA_LABEL_CRITICAL_4 | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service with integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
| DATA_LABEL_NORMAL_1   | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
| DATA_LABEL_NORMAL_2   | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
| DATA_LABEL_NORMAL_3   | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
| DATA_LABEL_NORMAL_4   | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
| DATA_LABEL_NORMAL_LOCAL_1<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
| DATA_LABEL_NORMAL_LOCAL_2<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
| DATA_LABEL_NORMAL_LOCAL_3<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
| DATA_LABEL_NORMAL_LOCAL_4<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
| CONFLICT_RESOLUTION   | Type: number<br>Value range: see [ConflictResolution](../../reference/apis-asset-store-kit/js-apis-asset.md#conflictresolution)| No    | Conflict (for example, duplicate aliases) resolution when an asset is added. The default value is **THROW_ERROR**, indicating that an exception is thrown for subsequent processing by the service. |
| REQUIRE_ATTR_ENCRYPTED<sup>14+</sup> | Type: Boolean| No| Whether to encrypt the additional asset information customized by the service. The value **true** means to encrypt the additional asset information customized by the service; the value **false** means the opposite. The default value is **false**.|
| GROUP_ID<<sup>18+</sup> | Type: Uint8Array<br>Length: 7-127 bytes| No| Group to which the asset to be added belongs. By default, this parameter is not specified.|
| WRAP_TYPE<sup>18+</sup> | Type: number<br>Value range: see [WrapType](../../reference/apis-asset-store-kit/js-apis-asset.md#wraptype18)| No| Encrypted import/export type supported by the asset. The default value is **NEVER**, indicating that encrypted import/export is not supported.|

## Constraints

- Alias-based access

  Assets are stored in the ASSET database in ciphertext and uniquely identified by the service identity and alias. The alias of each asset must be unique.

- Custom data storage

  Asset Store Kit provides 12 custom asset attributes starting with **DATA_LABEL** for services. If the 12 custom attributes are used, you can combine multiple data segments in a certain format (for example, JSON) into an attribute of this kit.

  Asset Store Kit provides integrity protection for attributes starting with **DATA_LABEL_CRITICAL**. Such attributes cannot be updated after being written.

- Batch operation

  The assets to be added in batches must have the same [GROUP_ID](../../reference/apis-asset-store-kit/js-apis-asset.md#tag) and [REQUIRE_ATTR_ENCRYPTED](../../reference/apis-asset-store-kit/js-apis-asset.md#tag) attributes.

  A maximum of 100 assets can be added in batches.

## Development Procedure

> **NOTE**
>
> The following is an example of using the batch addition API.

Add two assets in batches. Their passwords are demo_pwd1 and demo_pwd2, and aliases are demo_alias1 and demo_alias2 respectively.

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
   <!-- @[batch_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/batch_operation.ets) -->
   
   ``` TypeScript
   let attributesArray: asset.AssetMap[] = [];
   let attr1: asset.AssetMap = new Map();
   attr1.set(asset.Tag.SECRET, stringToArray('demo_pwd1'));
   attr1.set(asset.Tag.ALIAS, stringToArray('demo_alias1'));
   attributesArray.push(attr1);
   
   let attr2: asset.AssetMap = new Map();
   attr2.set(asset.Tag.SECRET, stringToArray('demo_pwd2'));
   attr2.set(asset.Tag.ALIAS, stringToArray('demo_alias2'));
   attributesArray.push(attr2);
   
   try {
     asset.batchAdd(attributesArray).then((res: asset.BatchResult) => {
       console.info(`Succeeded in batch adding Asset, failedCount: ${res.failedCount}`);
       if (res.failedCount > 0) {
         for (let i = 0; i < res.failedErrorInfos.length; i++) {
           console.error(`Failed to add Asset at index ${res.failedErrorInfos[i].index},
             errCode: ${res.failedErrorInfos[i].errCode}, message: ${res.failedErrorInfos[i].message}`);
         }
       }
     }).catch((err: BusinessError) => {
       console.error(`Failed to batch add Asset. Code is ${err.code}, message is ${err.message}`);
     })
   } catch (error) {
     let err = error as BusinessError;
     console.error(`Failed to batch add Asset. Code is ${err.code}, message is ${err.message}`);
   }
   ```
