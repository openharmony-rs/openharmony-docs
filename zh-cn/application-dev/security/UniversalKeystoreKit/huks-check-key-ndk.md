# 查询密钥是否存在(C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

HUKS提供了接口供应用查询指定密钥是否存在。

从API 23开始支持[群组密钥](huks-group-key-overview.md)特性。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so)
```

## 开发步骤

1. 指定密钥别名，密钥别名命名规范参考[密钥生成介绍及算法规格](huks-key-generation-overview.md)。

2. 初始化密钥属性集。用于查询时指定[密钥的属性TAG](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag)（默认传空）。

3. 调用接口[OH_Huks_IsKeyItemExist](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_iskeyitemexist)，查询密钥是否存在。

<!-- @[query_whether_the_key_exists_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/OtherOperations/CheckKeyExists/entry/src/main/cpp/napi_init.cpp) -->