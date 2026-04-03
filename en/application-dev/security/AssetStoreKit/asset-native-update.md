# Update an Asset (C/C++)

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @JeremyXu-->
<!--Designer: @skye_you-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

## Available APIs

You can use [OH_Asset_Update](../../reference/apis-asset-store-kit/capi-asset-api-h.md#oh_asset_update) to update an asset.

The following table describes the attributes for updating an asset.

>**NOTE**
>
>In the following table, the attributes **ASSET_TAG_ALIAS** and those starting with **ASSET_TAG_DATA_LABEL** are custom asset attributes reserved for services. These attributes are not encrypted. Therefore, do not put sensitive personal data in these attributes.

- Attributes in **query**:

  | Attribute Name (Asset_Tag)           | Attribute Content (Asset_Value)                                      | Mandatory| Description                                            |
  | ------------------------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------ |
  | ASSET_TAG_ALIAS                 | Type: uint8[]<br>Length: 1-256 bytes                              | Yes    | Asset alias, which uniquely identifies an asset.           |
  | ASSET_TAG_ACCESSIBILITY         | Type: uint32_t<br>Value range: see [Asset_Accessibility](../../reference/apis-asset-store-kit/capi-asset-type-h.md#asset_accessibility).| No    | Access control based on the lock screen status.                                    |
  | ASSET_TAG_REQUIRE_PASSWORD_SET  | Type: bool                                                  | No    | Whether the asset is accessible only when a lock screen password is set. The value **true** means the asset is accessible only when a lock screen password is set. The value **false** means that the asset can be accessed regardless of whether a lock screen password is set.    |
  | ASSET_TAG_AUTH_TYPE             | Type: uint32_t<br>Value range: see [Asset_AuthType](../../reference/apis-asset-store-kit/capi-asset-type-h.md#asset_authtype).| No    | Type of user authentication required for accessing the asset.                  |
  | ASSET_TAG_SYNC_TYPE             | Type: uint32_t<br>Value range: see [Asset_SyncType](../../reference/apis-asset-store-kit/capi-asset-type-h.md#asset_synctype).| No    | Type of sync supported by the asset.                          |
  | ASSET_TAG_IS_PERSISTENT         | Type: bool                                                  | No    | Whether to retain the asset when the application is uninstalled. The value **true** means to retain the asset even after the application is uninstalled. The value **false** means the opposite.              |
  | ASSET_TAG_DATA_LABEL_CRITICAL_1 | Type: uint8[]<br>Length: 1-2048 bytes                          | No    | Asset attribute information customized by the service with integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | ASSET_TAG_DATA_LABEL_CRITICAL_2 | Type: uint8[]<br>Length: 1-2048 bytes                          | No    | Asset attribute information customized by the service with integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | ASSET_TAG_DATA_LABEL_CRITICAL_3 | Type: uint8[]<br>Length: 1-2048 bytes                          | No    | Asset attribute information customized by the service with integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | ASSET_TAG_DATA_LABEL_CRITICAL_4 | Type: uint8[]<br>Length: 1-2048 bytes                          | No    | Asset attribute information customized by the service with integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | ASSET_TAG_DATA_LABEL_NORMAL_1   | Type: uint8[]<br>Length: 1-2048 bytes                          | No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | ASSET_TAG_DATA_LABEL_NORMAL_2   | Type: uint8[]<br>Length: 1-2048 bytes                          | No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | ASSET_TAG_DATA_LABEL_NORMAL_3   | Type: uint8[]<br>Length: 1-2048 bytes                          | No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | ASSET_TAG_DATA_LABEL_NORMAL_4   | Type: uint8[]<br>Length: 1-2048 bytes                          | No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | ASSET_TAG_DATA_LABEL_NORMAL_LOCAL_1<sup>12+</sup> | Type: uint8[]<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
  | ASSET_TAG_DATA_LABEL_NORMAL_LOCAL_2<sup>12+</sup> | Type: uint8[]<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
  | ASSET_TAG_DATA_LABEL_NORMAL_LOCAL_3<sup>12+</sup> | Type: uint8[]<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
  | ASSET_TAG_DATA_LABEL_NORMAL_LOCAL_4<sup>12+</sup> | Type: uint8[]<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
  | ASSET_TAG_REQUIRE_ATTR_ENCRYPTED<sup>14+</sup> | Type: bool| No| Whether to update the encrypted data of service customized supplementary information. The value **true** means to update the encrypted data of service customized supplementary information; the value **false** means to update the non-encrypted data of service customized supplementary information. Default value: **false**.|
  | ASSET_TAG_GROUP_ID<sup>18+</sup> | Type: Uint8[]<br>Length: 7-127 bytes| No| Group to which the asset to be updated belongs. By default, this parameter is not specified.|

- Attributes in **attributesToUpdate**:

  | Attribute Name (Asset_Tag)| Attribute Content (Asset_Value)         | Mandatory| Description                                            |
  | ------------------- | ------------------------------- | -------- | ------------------------------------------------ |
  | ASSET_TAG_SECRET    | Type: uint8[]<br>Length: 1-1024 bytes| No    | New asset in plaintext.                                    |
  | ASSET_TAG_DATA_LABEL_NORMAL_1 | Type: uint8[]<br>Length: 1-2048 bytes| No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | ASSET_TAG_DATA_LABEL_NORMAL_2 | Type: uint8[]<br>Length: 1-2048 bytes| No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | ASSET_TAG_DATA_LABEL_NORMAL_3 | Type: uint8[]<br>Length: 1-2048 bytes| No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | ASSET_TAG_DATA_LABEL_NORMAL_4 | Type: uint8[]<br>Length: 1-2048 bytes| No    | Asset attribute information customized by the service without integrity protection.<br>**NOTE**: The data length is 1 to 512 bytes before API version 12.|
  | ASSET_TAG_DATA_LABEL_NORMAL_LOCAL_1<sup>12+</sup> | Type: uint8[]<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
  | ASSET_TAG_DATA_LABEL_NORMAL_LOCAL_2<sup>12+</sup> | Type: uint8[]<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
  | ASSET_TAG_DATA_LABEL_NORMAL_LOCAL_3<sup>12+</sup> | Type: uint8[]<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|
  | ASSET_TAG_DATA_LABEL_NORMAL_LOCAL_4<sup>12+</sup> | Type: uint8[]<br>Length: 1-2048 bytes| No| Local attribute information about the asset. The value is assigned by the service without integrity protection and will not be synced.|

## Example

> **NOTE**
>
> Before updating an asset, ensure that the asset exists. For details about how to add an asset, see [Adding an Asset](./asset-native-add.md). Otherwise, the **NOT_FOUND** error (24000002) is reported.

Update asset **demo_alias** as follows: change the asset plaintext to **demo_pwd_new** and additional attribute to **demo_label_new**.

For details about how to update an asset in a group, see [Updating an asset in a Group](asset-native-group-access-control.md#updating-an-asset-in-a-group).

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

3. Update an asset.
   <!-- @[update_asset](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreNdk/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_value UpdateAsset(napi_env env, napi_callback_info info)
   {
       const char *aliasStr = "demo_alias";
       const char *secretStr = "demo_pwd_new";
       const char *labelStr = "demo_label_new";
   
       Asset_Blob alias = {(uint32_t)(strlen(aliasStr)), (uint8_t *)aliasStr};
       Asset_Blob new_secret = {(uint32_t)(strlen(secretStr)), (uint8_t *)secretStr};
       Asset_Blob new_label = {(uint32_t)(strlen(labelStr)), (uint8_t *)labelStr};
       Asset_Attr query[] = {{.tag = ASSET_TAG_ALIAS, .value.blob = alias }};
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
