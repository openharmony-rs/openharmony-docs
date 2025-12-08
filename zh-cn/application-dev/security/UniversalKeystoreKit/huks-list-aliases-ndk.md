# 查询密钥别名集(C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

HUKS提供了接口供应用查询密钥别名集。

>**说明：**
>
> <!--RP1-->轻量级设备<!--RP1End-->不支持查询密钥别名集功能。

从API 23开始支持[群组密钥](huks-group-key-overview.md)特性。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so)
```

## 开发步骤

1. 初始化密钥属性集。用于查询指定密钥别名集TAG，TAG仅支持[OH_HUKS_TAG_AUTH_STORAGE_LEVEL](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_authstoragelevel)。

2. 调用接口[OH_Huks_ListAliases](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_listaliases)，查询密钥别名集。

<!-- @[query_key_alias_set_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/OtherOperations/QueryKeyAliasSet/entry/src/main/cpp/napi_init.cpp) -->