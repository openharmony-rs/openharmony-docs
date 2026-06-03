# Querying Assets (ArkTS)

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @HarMonkey-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=4c605d27e0af7c49e44095d77dd99bf8c13d3e25 translatedAt=2026-06-03T09:08:14.841Z pushedAt=2026-06-03T09:45:13.459Z -->

## Available APIs

You can refer to the API documentation for detailed descriptions of the asset query API [query(query: AssetMap)](../../reference/apis-asset-store-kit/js-apis-asset.md#assetquery) and the synchronization API [querySync(query: AssetMap)](../../reference/apis-asset-store-kit/js-apis-asset.md#assetquerysync12).

When querying a asset, the content (**AssetMap**) parameter for the asset attribute are as shown in the following table:
> **NOTE**
>
> In the following table, the asset attributes **ALIAS** and those with names containing **DATA_LABEL** are used to store service-defined information. Their content is not encrypted, so do not store sensitive personal data in them.
> Querying the plaintext SECRET of an asset requires decryption. Currently, batch query is not supported, and the query time is long. You need to set **RETURN_TYPE** to **ALL**. Querying only other asset attributes does not require decryption, supports batch query, and the query time is short. You need to set **RETURN_TYPE** to **ATTRIBUTES**.

| Attribute Name (Tag)       | Value                                            | Mandatory | Description                                                        |
| --------------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| ALIAS                 | Type: Uint8Array<br>Length: 1-256 bytes                           | No    | Asset alias, which uniquely identifies an asset.                      |
| ACCESSIBILITY         | Type: number<br>Value range: see [Accessibility](../../reference/apis-asset-store-kit/js-apis-asset.md#accessibility)| No    | Access control based on the lock screen status.                               |
| REQUIRE_PASSWORD_SET  | Type: Boolean                                                  | No    | Whether the asset is accessible only when a lock screen password is set. The value **true** means the asset is accessible only when a lock screen password is set. The value **false** means that the asset can be accessed regardless of whether a lock screen password is set.                |
| AUTH_TYPE             | Type: number<br>Value range: see [AuthType](../../reference/apis-asset-store-kit/js-apis-asset.md#authtype)| No    | Type of user authentication required for accessing the asset.                              |
| SYNC_TYPE             | Type: number<br>Value range: see [SyncType](../../reference/apis-asset-store-kit/js-apis-asset.md#synctype)| No    | Type of sync supported by the asset.                                     |
| IS_PERSISTENT         | Type: Boolean                                                  | No    | Whether to retain the asset when the application is uninstalled. The value **true** means to retain the asset even after the application is uninstalled. The value **false** means the opposite.              |
| DATA_LABEL_CRITICAL_1 | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service with integrity protection.<br>**Note**: The data length is 1 to 512 bytes before API version 12.|
| DATA_LABEL_CRITICAL_2 | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service with integrity protection.<br>**Note**: The data length is 1 to 512 bytes before API version 12.|
| DATA_LABEL_CRITICAL_3 | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service with integrity protection.<br>**Note**: The data length is 1 to 512 bytes before API version 12.|
| DATA_LABEL_CRITICAL_4 | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service with integrity protection.<br>**Note**: The data length is 1 to 512 bytes before API version 12.|
| DATA_LABEL_NORMAL_1   | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service without integrity protection.<br>**Note**: The data length is 1 to 512 bytes before API version 12.|
| DATA_LABEL_NORMAL_2   | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service without integrity protection.<br>**Note**: The data length is 1 to 512 bytes before API version 12.|
| DATA_LABEL_NORMAL_3   | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service without integrity protection.<br>**Note**: The data length is 1 to 512 bytes before API version 12.|
| DATA_LABEL_NORMAL_4   | Type: Uint8Array<br>Length: 1-2048 bytes                       | No    | Asset attribute information customized by the service without integrity protection.<br>**Note**: The data length is 1 to 512 bytes before API version 12.|
| DATA_LABEL_NORMAL_LOCAL_1<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
| DATA_LABEL_NORMAL_LOCAL_2<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
| DATA_LABEL_NORMAL_LOCAL_3<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
| DATA_LABEL_NORMAL_LOCAL_4<sup>12+</sup> | Type: Uint8Array<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
| RETURN_TYPE           | Type: number<br>Value range: see [ReturnType](../../reference/apis-asset-store-kit/js-apis-asset.md#returntype)| No    | Type of the asset query result to return.            |
| RETURN_LIMIT          | Type: number                                                | No    | Maximum number of asset records returned.                                        |
| RETURN_OFFSET         | Type: number<br>Value range: 1-65536                             | No    | Offset of the asset query result.<br>**Note**: This parameter specifies the starting asset record to return in batch asset query.                                |
| RETURN_ORDERED_BY     | Type: number<br>Value: asset.Tag.DATA_LABEL_xxx.            | No    | How the query results are sorted. Currently, the results can be sorted only by **DATA_LABEL**.<br>**Note**: By default, assets are returned in the order in which they are added.|
| REQUIRE_ATTR_ENCRYPTED<sup>14+</sup> | Type: Boolean| No| Whether to query the encrypted data of service customized supplementary information. The value **true** means to query the encrypted data of service customized supplementary information; the value **false** means to query the non-encrypted data of service customized supplementary information. The default value is **false**.|
| GROUP_ID<sup>18+</sup> | Type: Uint8Array<br>Length: 7-127 bytes| No| Group to which the asset to be queried belongs. By default, this parameter is not specified.|

## Constraints

Assets queried in batches need to be transmitted to services through the IPC channel. Due to the limitation of the IPC buffer size, you are advised to query a maximum of 40 assets at a time.

## Example

> **NOTE**
>
> This module provides both asynchronous and synchronous APIs. The following is an example of using the asynchronous API. For details about the synchronous API, see [@ohos.security.asset (Asset Store Service)](../../reference/apis-asset-store-kit/js-apis-asset.md).
>
> For a usage example of querying the plaintext of a single asset in a specified group, see [Querying the Plaintext of an Asset in a Group](asset-js-group-access-control.md#querying-the-plaintext-of-an-asset-in-a-group). For a usage example of querying the attributes of a single asset in a specified group, see [Querying the Attributes of an Asset in a Group](asset-js-group-access-control.md#querying-the-attributes-of-an-asset-in-a-group).
> 
> Before querying, ensure that an asset already exists. If it does not exist, [add it](asset-js-add.md). Otherwise, a NOT_FOUND error (error code 24000002) will be thrown.

### Querying the Plaintext of an Asset

Query the plaintext of asset **demo_alias**.

1. Include the header file and define the tool function.

   <!-- @[import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/query_plaintext.ets) -->

   ``` TypeScript
   import { asset } from '@kit.AssetStoreKit';
   import { util } from '@kit.ArkTS';
   import { BusinessError } from '@kit.BasicServicesKit';
   
   function stringToArray(str: string): Uint8Array {
     let textEncoder = new util.TextEncoder();
     return textEncoder.encodeInto(str);
   }
   
   function arrayToString(arr: Uint8Array): string {
     let textDecoder = util.TextDecoder.create('utf-8', { ignoreBOM: true });
     let str = textDecoder.decodeToString(arr, { stream: false });
     return str;
   }
   ```

2. Develop the desired feature.

   <!-- @[query_single_plaintext](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/query_plaintext.ets) -->

   ``` TypeScript
   let query: asset.AssetMap = new Map();
   query.set(asset.Tag.ALIAS, stringToArray('demo_alias')); // Specify the alias of the asset to query.
   query.set(asset.Tag.RETURN_TYPE, asset.ReturnType.ALL); // Return all asset information, including the attributes and asset plaintext. The plaintext needs to be decrypted, so the query takes a long time.
   try {
     asset.query(query).then((res: Array<asset.AssetMap>) => {
       for (let i = 0; i < res.length; i++) {
         // Parse the secret.
         let secret: Uint8Array = res[i].get(asset.Tag.SECRET) as Uint8Array;
         // Convert Uint8Array into the string type.
         let secretStr: string = arrayToString(secret);
       }
       // ...
     }).catch((err: BusinessError) => {
       console.error(`Failed to query Asset plaintext. Code is ${err.code}, message is ${err.message}`);
       // ...
     });
   } catch (error) {
     let err = error as BusinessError;
     console.error(`Failed to query Asset plaintext. Code is ${err.code}, message is ${err.message}`);
     // ...
   }
   ```

### Querying Attributes of an Asset

Query attributes of asset **demo_alias**.

1. Include the header file and define the tool function.

   <!-- @[import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/query_attr.ets) -->

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

   <!-- @[query_single_attribute](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/query_attr.ets) -->

   ``` TypeScript
   let query: asset.AssetMap = new Map();
   query.set(asset.Tag.ALIAS, stringToArray('demo_alias')); // Specify the alias of the asset to query.
   query.set(asset.Tag.RETURN_TYPE, asset.ReturnType.ATTRIBUTES); // Return only the attributes of the asset, that is, the result does not include the asset plaintext.
   try {
     asset.query(query).then((res: Array<asset.AssetMap>) => {
       for (let i = 0; i < res.length; i++) {
         // Parse the attributes.
         let accessibility: number = res[i].get(asset.Tag.ACCESSIBILITY) as number;
         console.info(`Succeeded in getting accessibility, which is: ${accessibility}.`);
       }
       // ...
     }).catch((err: BusinessError) => {
       console.error(`Failed to query Asset attribute. Code is ${err.code}, message is ${err.message}`);
       // ...
     });
   } catch (error) {
     let err = error as BusinessError;
     console.error(`Failed to query Asset attribute. Code is ${err.code}, message is ${err.message}`);
     // ...
   }
   ```

### Querying Attributes of Assets

Query attributes of assets whose label is **demo_label** in batches. A total of 10 records that meet the conditions are returned. The results are sorted by the content of the **DATA_LABEL_NORMAL_1** attribute.

1. Include the header file and define the tool function.

   <!-- @[import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/query_batch_attrs.ets) -->

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

   <!-- @[query_batch_attributes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/query_batch_attrs.ets) -->

   ``` TypeScript
   let query: asset.AssetMap = new Map();
   query.set(asset.Tag.RETURN_TYPE, asset.ReturnType.ATTRIBUTES); // Return only the attributes of the asset, that is, the result does not include the asset plaintext.
   query.set(asset.Tag.DATA_LABEL_NORMAL_1, stringToArray('demo_label'));
   query.set(asset.Tag.RETURN_LIMIT, 10); // Return information about 10 assets that match the search criteria.
   query.set(asset.Tag.RETURN_ORDERED_BY, asset.Tag.DATA_LABEL_NORMAL_1); // Sort the query results by DATA_LABEL_NORMAL_1.
   try {
     asset.query(query).then((res: Array<asset.AssetMap>) => {
       for (let i = 0; i < res.length; i++) {
         // Parse the attributes.
         let accessibility: number = res[i].get(asset.Tag.ACCESSIBILITY) as number;
         console.info(`Succeeded in getting accessibility, which is: ${accessibility}.`);
       }
       // ...
     }).catch((err: BusinessError) => {
       console.error(`Failed to query batch Asset attributes. Code is ${err.code}, message is ${err.message}`);
       // ...
     });
   } catch (error) {
     let err = error as BusinessError;
     console.error(`Failed to query batch Asset attributes. Code is ${err.code}, message is ${err.message}`);
     // ...
   }
   ```