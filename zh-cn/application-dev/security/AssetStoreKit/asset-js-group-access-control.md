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

## 删除群组关键资产

在群组中删除别名为demo_alias的关键资产。

<!-- @[remove_group_asset](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/remove_group.ets) -->

## 更新群组关键资产

在群组中更新别名为demo_alias的关键资产，明文更新为demo_pwd_new，附属属性更新为demo_label_new。

<!-- @[update_group_asset](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/update_group.ets) -->

## 查询单条群组关键资产明文

在群组中查询别名为demo_alias的关键资产明文。

<!-- @[query_group_asset_plaintext](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/query_group.ets) -->

## 查询单条群组关键资产属性

在群组中查询别名为demo_alias的关键资产属性。

<!-- @[query_group_asset_attribute](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/query_group.ets) -->
