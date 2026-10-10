# Removing Assets in Batches (ArkTS)

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @JeremyXu-->
<!--Designer: @skye_you-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=b3dcf2109b956a292ded4a48a27d9302526f580a translatedAt=2026-10-09T01:14:03.956Z pushedAt=2026-10-09T09:00:35.917Z -->

## Available APIs

Since version 26.0.0, the system provides the asynchronous API [batchRemove](../../reference/apis-asset-store-kit/js-apis-asset.md#assetbatchremove) for you to remove assets in batches.

The following table describes the attributes of **AssetMap** for removing assets in batches.

> **NOTE**
>
> In the following table, the attributes **ALIAS** and those starting with **DATA_LABEL** are custom asset attributes reserved for services. These attributes are not encrypted. Therefore, do not put sensitive personal data in these attributes.

| Attribute Name (Tag)       | Value                                            | Mandatory | Description                                            |
| --------------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------ |
| ALIAS                 | Type: Uint8Array<br>Length: 1-256 bytes                           | No    | Asset alias, which uniquely identifies an asset.           |
| REQUIRE_ATTR_ENCRYPTED<sup>14+</sup> | Type: boolean| No| Whether to delete encrypted data of service-defined additional information. **true** is to delete the service-defined additional information stored in encrypted form, and **false** is to delete the service-defined additional information stored in unencrypted form. The default value is **false**.|
| GROUP_ID<sup>18+</sup> | Type: Uint8Array<br>Length: 7-127 bytes| No| Group to which the asset to be removed belongs. By default, this parameter is not specified.|

## Constraints

The assets to be removed in batches must have the same [GROUP_ID](../../reference/apis-asset-store-kit/js-apis-asset.md#tag) and [REQUIRE_ATTR_ENCRYPTED](../../reference/apis-asset-store-kit/js-apis-asset.md#tag) attributes.

A maximum of 100 assets can be removed in batches.

## Development Procedure

> **Note:**
>
> The following is an example of using the Batch Delete API.
>
> Before deletion, ensure that assets already exist. You can refer to the [guide](asset-js-add.md) to add assets. Otherwise, a NOT_FOUND error (error code 24000002) will be thrown.

Remove two assets whose aliases are demo_alias1 and demo_alias2 in batches.

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
   <!-- @[batch_remove](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/batch_operation.ets) -->

   ``` TypeScript
   let assetsToBeRemoved: asset.AssetMap[] = [];
   let query1: asset.AssetMap = new Map();
   query1.set(asset.Tag.ALIAS, stringToArray('demo_alias1'));
   assetsToBeRemoved.push(query1);
   let query2: asset.AssetMap = new Map();
   query2.set(asset.Tag.ALIAS, stringToArray('demo_alias2'));
   assetsToBeRemoved.push(query2);
   
   try {
     asset.batchRemove(assetsToBeRemoved).then(() => {
       console.info(`Succeeded in batch removing Asset.`);
     }).catch((err: BusinessError) => {
       console.error(`Failed to batch remove Asset. Code is ${err.code}, message is ${err.message}`);
     })
   } catch (error) {
     let err = error as BusinessError;
     console.error(`Failed to batch remove Asset. Code is ${err.code}, message is ${err.message}`);
   }
   ```