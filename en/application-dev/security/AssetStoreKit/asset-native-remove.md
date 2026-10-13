# Removing Assets (C/C++)

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @JeremyXu-->
<!--Designer: @skye_you-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=4406a1fcebfd3a8963726b8dfa66bed58dd98b9c translatedAt=2026-10-09T01:25:46.137Z pushedAt=2026-10-09T11:41:01.045Z -->

## Available APIs

You can use [OH_Asset_Remove](../../reference/apis-asset-store-kit/capi-asset-api-h.md#oh_asset_remove) to remove an asset.

The following table describes the asset attributes.

> **NOTE**
>
> In the following table, the attributes **ASSET_TAG_ALIAS** and those starting with **ASSET_TAG_DATA_LABEL** are custom asset attributes reserved for services. These attributes are not encrypted. Therefore, do not put sensitive personal data in these attributes.

| Attribute Name (Asset_Tag)           | Attribute Content (Asset_Value)                                      | Mandatory| Description                                            |
| ------------------------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------ |
| ASSET_TAG_ALIAS                 | Type: uint8[]<br>Length: 1-256 bytes                              | No    | Asset alias, which uniquely identifies an asset.           |
| ASSET_TAG_ACCESSIBILITY         | Type: uint32_t<br>Value range: see [Asset_Accessibility](../../reference/apis-asset-store-kit/capi-asset-type-h.md#asset_accessibility).| No    | Access control based on the lock screen status.                                    |
| ASSET_TAG_REQUIRE_PASSWORD_SET  | Type: bool                                                  | No    | Whether the asset is accessible only when a lock screen password is set. The value **true** means the asset is accessible only when a lock screen password is set. The value **false** means that the asset can be accessed regardless of whether a lock screen password is set.    |
| ASSET_TAG_AUTH_TYPE             | Type: uint32_t<br>Value range: see [Asset_AuthType](../../reference/apis-asset-store-kit/capi-asset-type-h.md#asset_authtype).| No    | Type of user authentication required for accessing the asset.                  |
| ASSET_TAG_SYNC_TYPE             | Type: uint32_t<br>Value range: see [Asset_SyncType](../../reference/apis-asset-store-kit/capi-asset-type-h.md#asset_synctype).| No    | Type of sync supported by the asset.                          |
| ASSET_TAG_IS_PERSISTENT         | Type: bool                                                  | No    | Whether to retain the asset when the application is uninstalled. The value **true** means to retain the asset even after the application is uninstalled. The value **false** means the opposite.             |
| ASSET_TAG_DATA_LABEL_CRITICAL_1 | The type is uint8[], with a length of 1 to 2048 bytes. | Optional | Attached information of the asset. The content is defined by the service and has integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1 to 512 bytes. |
| ASSET_TAG_DATA_LABEL_CRITICAL_2 | The type is uint8[], with a length of 1 to 2048 bytes. | Optional | Attached information of the asset. The content is defined by the service and has integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1 to 512 bytes. |
| ASSET_TAG_DATA_LABEL_CRITICAL_3 | The type is uint8[], with a length of 1 to 2048 bytes. | Optional | Attached information of the asset. The content is defined by the service and has integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1 to 512 bytes. |
| ASSET_TAG_DATA_LABEL_CRITICAL_4 | The type is uint8[], with a length of 1 to 2048 bytes. | Optional | Attached information of the asset. The content is defined by the service and has integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1 to 512 bytes. |
| ASSET_TAG_DATA_LABEL_NORMAL_1 | The type is uint8[], with a length of 1 to 2048 bytes. | Optional | Attached information of the asset. The content is defined by the service and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1 to 512 bytes. |
| ASSET_TAG_DATA_LABEL_NORMAL_2 | The type is uint8[], with a length of 1 to 2048 bytes. | Optional | Attached information of the asset. The content is defined by the service and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1 to 512 bytes. |
| ASSET_TAG_DATA_LABEL_NORMAL_3 | The type is uint8[], with a length of 1 to 2048 bytes. | Optional | Attached information of the asset. The content is defined by the service and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1 to 512 bytes. |
| ASSET_TAG_DATA_LABEL_NORMAL_4 | The type is uint8[], with a length of 1 to 2048 bytes. | Optional | Attached information of the asset. The content is defined by the service and has no integrity protection.<br/>**Note:** In API version 12 and earlier versions, the length is 1 to 512 bytes. |
| ASSET_TAG_DATA_LABEL_NORMAL_LOCAL_1<sup>12+</sup> | Type: uint8[]<br>Length: 1-2048 bytes| No| Local information attached to the asset. The value is assigned by the service without integrity protection and will not be synced.|
| ASSET_TAG_DATA_LABEL_NORMAL_LOCAL_2<sup>12+</sup> | Type: uint8[]<br>Length: 1-2048 bytes| No| Local information attached to the asset. The value is assigned by the service without integrity protection and will not be synced.|
| ASSET_TAG_DATA_LABEL_NORMAL_LOCAL_3<sup>12+</sup> | Type: uint8[]<br>Length: 1-2048 bytes| No| Local information attached to the asset. The value is assigned by the service without integrity protection and will not be synced.|
| ASSET_TAG_DATA_LABEL_NORMAL_LOCAL_4<sup>12+</sup> | Type: uint8[]<br>Length: 1-2048 bytes| No| Local information attached to the asset. The value is assigned by the service without integrity protection and will not be synced.|
| ASSET_TAG_REQUIRE_ATTR_ENCRYPTED<sup>14+</sup> | Type: bool| No| Whether to remove the encrypted data of service customized supplementary information. The value **true** means to remove the encrypted data of service customized supplementary information; the value **false** means to remove the non-encrypted data of service customized supplementary information. Default value: **false**.|
| ASSET_TAG_GROUP_ID<sup>18+</sup> | Type: Uint8[]<br>Length: 7-127 bytes| No| Group to which the asset to be removed belongs. By default, only assets that do not belong to any group are deleted.|

## Example

> **NOTE**
>
> Before removing an asset, ensure that the asset exists. For details about how to add an asset, see [Adding an Asset](./asset-native-add.md). Otherwise, the **NOT_FOUND** error (24000002) is reported.

Remove asset **demo_alias**.

For details about how to remove an asset in a group, see [Removing an Asset from a Group](asset-native-group-access-control.md#removing-an-asset-from-a-group).

1. Link the dynamic libraries in the CMake script.
   ```txt
   target_link_libraries(entry PUBLIC libasset_ndk.z.so)
   ```

2. Include header files.
   <!-- @[include](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreNdk/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   #include "napi/native_api.h"
   #include <string.h>
   #include "asset/asset_api.h"
   ```

3. Remove an asset.
   <!-- @[remove_asset](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreNdk/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   static napi_value RemoveAsset(napi_env env, napi_callback_info info)
   {
       const char *aliasStr = "demo_alias";
       
       Asset_Blob alias = {(uint32_t)(strlen(aliasStr)), (uint8_t *)aliasStr};
       Asset_Attr attr[] = {
           {.tag = ASSET_TAG_ALIAS, .value.blob = alias}, // You can specify the asset alias to remove a single asset. To remove all assets, leave the alias unspecified.
       };
   
       int32_t removeResult = OH_Asset_Remove(attr, sizeof(attr) / sizeof(attr[0]));
       napi_value ret;
       napi_create_int32(env, removeResult, &ret);
       return ret;
   }
   ```
