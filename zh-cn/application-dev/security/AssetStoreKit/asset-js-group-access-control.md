# 管理群组关键资产(ArkTS)

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @JeremyXu-->
<!--Designer: @skye_you-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

以下为管理群组关键资产使用示例，请先查看开发指导：

- [新增关键资产(ArkTS)](asset-js-add.md)
- [删除关键资产(ArkTS)](asset-js-remove.md)
- [更新关键资产(ArkTS)](asset-js-update.md)
- [查询关键资产(ArkTS)](asset-js-query.md)

## 前置条件

在应用配置文件app.json5中，配置群组ID，如：demo_group_id。群组支持配置多个群组ID。

```json5
{
  "app": {
    // 其他配置项此处省略。
    "assetAccessGroups": [
      "demo_group_id",
      // "another_group_id",
      // ...
    ]
  }
}
```

## 新增群组关键资产

在群组中新增密码为demo_pwd、别名为demo_alias、附属信息为demo_label的关键资产。

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


## 删除群组关键资产

在群组中删除别名为demo_alias的关键资产。

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
  query.set(asset.Tag.ALIAS, stringToArray('demo_alias')); // 此处指定别名删除单条群组关键资产，也可不指定别名删除多条群组关键资产。
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


## 更新群组关键资产

在群组中更新别名为demo_alias的关键资产，明文更新为demo_pwd_new，附属属性更新为demo_label_new。

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


## 查询单条群组关键资产明文

在群组中查询别名为demo_alias的关键资产明文。

<!-- @[query_group_asset_plaintext](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/query_group_plaintext.ets) -->

## 查询单条群组关键资产属性

在群组中查询别名为demo_alias的关键资产属性。

<!-- @[query_group_asset_attribute](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/query_group_attr.ets) -->