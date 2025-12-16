# Managing Assets in a Group (C/C++)

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @JeremyXu-->
<!--Designer: @skye_you-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

Before managing assets in a group, ensure that you are familiar with the following operations:

- [Adding an Asset (C/C++)](asset-native-add.md)
- [Removing Assets (C/C++)](asset-native-remove.md)
- [Updating an Asset (C/C++)](asset-native-update.md)
- [Querying Assets (C/C++)](asset-native-query.md)

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

Include header files.

<!-- @[include](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreNdk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
#include "napi/native_api.h"
#include <string.h>
#include "asset/asset_api.h"
```


## Adding an Asset to a Group

Add an asset to the group, with the password **demo_pwd**, alias **demo_alias**, and additional attribute **demo_label**.

<!-- @[add_group_asset](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreNdk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value AddGroupAsset(napi_env env, napi_callback_info info)
{
    const char *secretStr = "demo_pwd";
    const char *aliasStr = "demo_alias";
    const char *labelStr = "demo_label";
    const char *groupIdStr = "demo_group_id";

    Asset_Blob secret = {(uint32_t)(strlen(secretStr)), (uint8_t *)secretStr};
    Asset_Blob alias = {(uint32_t)(strlen(aliasStr)), (uint8_t *)aliasStr};
    Asset_Blob label = {(uint32_t)(strlen(labelStr)), (uint8_t *)labelStr};
    Asset_Blob group_id = { (uint32_t)(strlen(groupIdStr)), (uint8_t *)groupIdStr};
    Asset_Attr attr[] = {
        {.tag = ASSET_TAG_SECRET, .value.blob = secret},
        {.tag = ASSET_TAG_ALIAS, .value.blob = alias},
        {.tag = ASSET_TAG_DATA_LABEL_NORMAL_1, .value.blob = label},
        {.tag = ASSET_TAG_GROUP_ID, .value.blob = group_id},
    };

    int32_t addResult = OH_Asset_Add(attr, sizeof(attr) / sizeof(attr[0]));
    napi_value ret;
    napi_create_int32(env, addResult, &ret);
    return ret;
}
```


## Removing an Asset from a Group

Remove asset **demo_alias** from group **demo_group_id**.

<!-- @[remove_group_asset](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreNdk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value RemoveGroupAsset(napi_env env, napi_callback_info info)
{
    const char *aliasStr = "demo_alias";
    const char *groupIdStr = "demo_group_id";

    Asset_Blob alias = {(uint32_t)(strlen(aliasStr)), (uint8_t *)aliasStr};
    Asset_Blob group_id = {(uint32_t)(strlen(groupIdStr)), (uint8_t *)groupIdStr};
    Asset_Attr attr[] = {
        {.tag = ASSET_TAG_ALIAS, .value.blob = alias}, // Specify the asset alias to remove a single asset. To remove all assets, leave the alias unspecified.
        {.tag = ASSET_TAG_GROUP_ID, .value.blob = group_id},
    };

    int32_t removeResult = OH_Asset_Remove(attr, sizeof(attr) / sizeof(attr[0]));
    napi_value ret;
    napi_create_int32(env, removeResult, &ret);
    return ret;
}
```


## Updating an Asset in a Group

Update asset **demo_alias** in group **demo_group_id** as follows: change the asset plaintext to **demo_pwd_new** and the additional attribute to **demo_label_new**.

<!-- @[update_group_asset](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreNdk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value UpdateGroupAsset(napi_env env, napi_callback_info info)
{
    const char *aliasStr = "demo_alias";
    const char *secretStr = "demo_pwd_new";
    const char *labelStr = "demo_label_new";
    const char *groupIdStr = "demo_group_id";

    Asset_Blob alias = {(uint32_t)(strlen(aliasStr)), (uint8_t *)aliasStr};
    Asset_Blob new_secret = {(uint32_t)(strlen(secretStr)), (uint8_t *)secretStr};
    Asset_Blob new_label = {(uint32_t)(strlen(labelStr)), (uint8_t *)labelStr};
    Asset_Blob group_id = {(uint32_t)(strlen(groupIdStr)), (uint8_t *)groupIdStr};
    Asset_Attr query[] = {
        {.tag = ASSET_TAG_ALIAS, .value.blob = alias},
        {.tag = ASSET_TAG_GROUP_ID, .value.blob = group_id},
    };
    Asset_Attr attributesToUpdate[] = {
        {.tag = ASSET_TAG_SECRET, .value.blob = new_secret},
        {.tag = ASSET_TAG_DATA_LABEL_NORMAL_1, .value.blob = new_label},
    };

    int32_t updateResult = OH_Asset_Update(query, sizeof(query) / sizeof(query[0]), attributesToUpdate,
                                           sizeof(attributesToUpdate) / sizeof(attributesToUpdate[0]));
    napi_value ret;
    napi_create_int32(env, updateResult, &ret);
    return ret;
}
```


## Querying the Plaintext of an Asset in a Group

Query the plaintext of asset **demo_alias** in group **demo_group_id**.

<!-- @[query_group_single_plaintext](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreNdk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value QueryGroupAssetPlaintext(napi_env env, napi_callback_info info)
{
    const char *aliasStr = "demo_alias";
    const char *groupIdStr = "demo_group_id";
    
    Asset_Blob alias = { (uint32_t)(strlen(aliasStr)), (uint8_t *)aliasStr };
    Asset_Blob group_id = { (uint32_t)(strlen(groupIdStr)), (uint8_t *)groupIdStr };
    Asset_Attr attr[] = {
        {.tag = ASSET_TAG_ALIAS, .value.blob = alias}, // Specify the alias of the asset to query.
        {.tag = ASSET_TAG_RETURN_TYPE, .value.u32 = ASSET_RETURN_ALL}, // Return all asset information, including the attributes and asset plaintext, in the group.
        {.tag = ASSET_TAG_GROUP_ID, .value.blob = group_id},
    };

    Asset_ResultSet resultSet = {0};
    int32_t queryResult = OH_Asset_Query(attr, sizeof(attr) / sizeof(attr[0]), &resultSet);
    if (queryResult == ASSET_SUCCESS) {
        // Parse resultSet.
        for (uint32_t i = 0; i < resultSet.count; i++) {
            // Parse the secret attribute. The data corresponds to secret->blob.data, and the size corresponds to secret->blob.size.
            Asset_Attr *secret = OH_Asset_ParseAttr(resultSet.results + i, ASSET_TAG_SECRET);
        }
    }
    OH_Asset_FreeResultSet(&resultSet);
    
    napi_value ret;
    napi_create_int32(env, queryResult, &ret);
    return ret;
}
```


## Querying the Attributes of an Asset in a Group

Query attributes of asset **demo_alias**.

<!-- @[query_group_single_attribute](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreNdk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value QueryGroupAssetAttribute(napi_env env, napi_callback_info info)
{
    const char *aliasStr = "demo_alias";
    const char *groupIdStr = "demo_group_id";
    
    Asset_Blob alias = {(uint32_t)(strlen(aliasStr)), (uint8_t *)aliasStr};
    Asset_Blob group_id = {(uint32_t)(strlen(groupIdStr)), (uint8_t *)groupIdStr};
    Asset_Attr attr[] = {
        {.tag = ASSET_TAG_ALIAS, .value.blob = alias}, // Specify the alias of the asset to query.
        {.tag = ASSET_TAG_RETURN_TYPE, .value.u32 = ASSET_RETURN_ATTRIBUTES}, // Return only the asset attributes of the asset in the group, that is, the result does not include the asset plaintext.
        {.tag = ASSET_TAG_GROUP_ID, .value.blob = group_id},
    };

    Asset_ResultSet resultSet = {0};
    int32_t queryResult = OH_Asset_Query(attr, sizeof(attr) / sizeof(attr[0]), &resultSet);
    if (queryResult == ASSET_SUCCESS) {
        // Parse the result
        for (uint32_t i = 0; i < resultSet.count; i++) {
            // Parse the data label. The data corresponds to label->blob.data, and the size corresponds to label->blob.size.
            Asset_Attr *label = OH_Asset_ParseAttr(resultSet.results + i, ASSET_TAG_DATA_LABEL_NORMAL_1);
        }
    }
    OH_Asset_FreeResultSet(&resultSet);
    
    napi_value ret;
    napi_create_int32(env, queryResult, &ret);
    return ret;
}
```
