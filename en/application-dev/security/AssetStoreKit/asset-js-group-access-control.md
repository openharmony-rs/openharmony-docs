# Managing Assets in a Group (ArkTS)

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @JeremyXu-->
<!--Designer: @skye_you-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

Before managing assets in a group, ensure that you are familiar with the following operations:

- [Adding an Asset (ArkTS)](asset-js-add.md)
- [Removing Assets (ArkTS)](asset-js-remove.md)
- [Updating an Asset (ArkTS)](asset-js-update.md)
- [Querying Assets (ArkTS)](asset-js-query.md)

## Prerequisites

Set the group ID, such as **demo_group_id**, in the **app.json5** file. You can set multiple group IDs for a group.

```json5
{
  "app": {
    // Other configuration items are omitted here.
    "assetAccessGroups": [
      "demo_group_id",
      // "another_group_id",
      // ...
    ]
  }
}
```

## Adding an Asset to a Group

Add an asset to the group, with the password **demo_pwd**, alias **demo_alias**, and additional attribute **demo_label**.

<!-- @[add_group_asset](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/add_group.ets) -->

``` TypeScript
import { asset } from '@kit.AssetStoreKit';
import { util } from '@kit.ArkTS';
import { BusinessError } from '@kit.BasicServicesKit';

function stringToArray(str: string): Uint8Array {
  let textEncoder = new util.TextEncoder();
  return textEncoder.encodeInto(str);
}

export async function addGroupAsset(): Promise<string> {
  let result: string = '';
  let attr: asset.AssetMap = new Map();
  attr.set(asset.Tag.SECRET, stringToArray('demo_pwd'));
  attr.set(asset.Tag.ALIAS, stringToArray('demo_alias'));
  attr.set(asset.Tag.DATA_LABEL_NORMAL_1, stringToArray('demo_label'));
  attr.set(asset.Tag.GROUP_ID, stringToArray('demo_group_id'));
  try {
    await asset.add(attr).then(() => {
      console.info(`Succeeded in adding Asset to the group.`);
      result = 'Succeeded in adding Asset to the group';
    }).catch((err: BusinessError) => {
      console.error(`Failed to add Asset to the group. Code is ${err.code}, message is ${err.message}`);
      result = 'Failed to add Asset to the group';
    })
  } catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to add Asset to the group. Code is ${err?.code}, message is ${err?.message}`);
    result = 'Failed to add Asset to the group';
  }
  return result;
}
```


## Removing an Asset from a Group

Remove asset **demo_alias** from group **demo_group_id**.

<!-- @[remove_group_asset](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/remove_group.ets) -->

``` TypeScript
import { asset } from '@kit.AssetStoreKit';
import { util } from '@kit.ArkTS';
import { BusinessError } from '@kit.BasicServicesKit';

function stringToArray(str: string): Uint8Array {
  let textEncoder = new util.TextEncoder();
  return textEncoder.encodeInto(str);
}

export async function removeGroupAsset(): Promise<string> {
  let result: string = '';
  let query: asset.AssetMap = new Map();
  query.set(asset.Tag.ALIAS, stringToArray('demo_alias')); // Specify the alias to delete a single asset from the group. You can also delete multiple assets without specifying the alias.
  query.set(asset.Tag.GROUP_ID, stringToArray('demo_group_id'));
  try {
    await asset.remove(query).then(() => {
      console.info(`Succeeded in removing Asset from the group.`);
      result = 'Succeeded in removing Asset from the group';
    }).catch((err: BusinessError) => {
      console.error(`Failed to remove Asset from the group. Code is ${err.code}, message is ${err.message}`);
      result = 'Failed to remove Asset from the group';
    });
  } catch (err) {
    console.error(`Failed to remove Asset from the group. Code is ${err?.code}, message is ${err?.message}`);
    result = 'Failed to remove Asset from the group';
  }
  return result;
}
```


## Updating an asset in a Group

Update asset **demo_alias** in group **demo_group_id** as follows: change the asset plaintext to **demo_pwd_new** and the additional attribute to **demo_label_new**.

<!-- @[update_group_asset](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/update_group.ets) -->

``` TypeScript
import { asset } from '@kit.AssetStoreKit';
import { util } from '@kit.ArkTS';
import { BusinessError } from '@kit.BasicServicesKit';

function stringToArray(str: string): Uint8Array {
  let textEncoder = new util.TextEncoder();
  return textEncoder.encodeInto(str);
}

export async function updateGroupAsset(): Promise<string> {
  let result: string = '';
  let query: asset.AssetMap = new Map();
  query.set(asset.Tag.ALIAS, stringToArray('demo_alias'));
  query.set(asset.Tag.GROUP_ID, stringToArray('demo_group_id'));
  let attrsToUpdate: asset.AssetMap = new Map();
  attrsToUpdate.set(asset.Tag.SECRET, stringToArray('demo_pwd_new'));
  attrsToUpdate.set(asset.Tag.DATA_LABEL_NORMAL_1, stringToArray('demo_label_new'));
  try {
    await asset.update(query, attrsToUpdate).then(() => {
      console.info(`Succeeded in updating Asset in the group.`);
      result = 'Succeeded in updating Asset in the group';
    }).catch((err: BusinessError) => {
      console.error(`Failed to update Asset in the group. Code is ${err.code}, message is ${err.message}`);
      result = 'Failed to update Asset in the group';
    });
  } catch (err) {
    console.error(`Failed to update Asset in the group. Code is ${err?.code}, message is ${err?.message}`);
    result = 'Failed to update Asset in the group';
  }
  return result;
}
```


## Querying the Plaintext of an Asset in a Group

Query the plaintext of asset **demo_alias** in group **demo_group_id**.

<!-- @[query_group_asset_plaintext](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/query_group_plaintext.ets) -->

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

export async function queryGroupAssetPlaintext(): Promise<string> {
  let result: string = '';
  let query: asset.AssetMap = new Map();
  query.set(asset.Tag.ALIAS, stringToArray('demo_alias')); // Specify the alias of the asset to query.
  query.set(asset.Tag.RETURN_TYPE, asset.ReturnType.ALL); // Return all asset information, including attributes and asset plaintext.
  query.set(asset.Tag.GROUP_ID, stringToArray('demo_group_id'));
  try {
    await asset.query(query).then((res: Array<asset.AssetMap>) => {
      for (let i = 0; i < res.length; i++) {
        // Parse the secret.
        let secret: Uint8Array = res[i].get(asset.Tag.SECRET) as Uint8Array;
        // Convert Uint8Array into the string type.
        let secretStr: string = arrayToString(secret);
      }
      result = 'Succeeded in querying group Asset plaintext';
    }).catch((err: BusinessError) => {
      console.error(`Failed to query Asset plaintext from the group. Code is ${err.code}, message is ${err.message}`);
      result = 'Failed to query Asset plaintext from the group';
    });
  } catch (err) {
    console.error(`Failed to query Asset plaintext from the group. Code is ${err?.code}, message is ${err?.message}`);
    result = 'Failed to query Asset plaintext from the group';
  }
  return result;
}
```


## Querying the Attributes of an Asset in a Group

Query the attributes of asset **demo_alias** in group **demo_group_id**.

<!-- @[query_group_asset_attribute](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/query_group_attr.ets) -->

``` TypeScript
import { asset } from '@kit.AssetStoreKit';
import { util } from '@kit.ArkTS';
import { BusinessError } from '@kit.BasicServicesKit';

function stringToArray(str: string): Uint8Array {
  let textEncoder = new util.TextEncoder();
  return textEncoder.encodeInto(str);
}

export async function queryGroupAssetAttribute(): Promise<string> {
  let result: string = '';
  let query: asset.AssetMap = new Map();
  query.set(asset.Tag.ALIAS, stringToArray('demo_alias')); // Specify the alias of the asset to query.
  query.set(asset.Tag.RETURN_TYPE, asset.ReturnType.ATTRIBUTES); // Return only the attributes of the asset, that is, the result does not include the asset plaintext.
  query.set(asset.Tag.GROUP_ID, stringToArray('demo_group_id'));
  try {
    await asset.query(query).then((res: Array<asset.AssetMap>) => {
      for (let i = 0; i < res.length; i++) {
        // Parse the attributes.
        let accessibility: number = res[i].get(asset.Tag.ACCESSIBILITY) as number;
        console.info(`Succeeded in getting accessibility, which is: ${accessibility}.`);
      }
      result = 'Succeeded in querying group Asset attribute';
    }).catch((err: BusinessError) => {
      console.error(`Failed to query Asset attribute from the group. Code is ${err.code}, message is ${err.message}`);
      result = 'Failed to query Asset attribute from the group';
    });
  } catch (err) {
    console.error(`Failed to query Asset attribute from the group. Code is ${err?.code}, message is ${err?.message}`);
    result = 'Failed to query Asset attribute from the group';
  }
  return result;
}
```
