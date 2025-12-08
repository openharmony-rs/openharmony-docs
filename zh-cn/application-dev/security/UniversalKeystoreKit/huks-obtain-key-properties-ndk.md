# 获取密钥属性(C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

HUKS提供了接口供业务获取指定密钥的相关属性。在获取指定密钥属性前，需要确保已在HUKS中生成或导入持久化存储的密钥。
>**说明：**
>
> 轻量级设备不支持获取密钥属性功能。

从API 23开始支持[群组密钥](huks-group-key-overview.md)特性。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so)
```
## 开发步骤

1. 构造对应参数。
   - keyAlias：密钥别名，封装成[OH_Huks_Blob](../../reference/apis-universal-keystore-kit/capi-hukstypeapi-oh-huks-blob.md)结构，密钥别名最大长度为128字节。
   - paramSetIn：预留参数，暂不需要处理，传空即可。
   - paramSetOut：用于放置获取到的参数集结果，为[OH_Huks_ParamSet](../../reference/apis-universal-keystore-kit/capi-hukstypeapi-oh-huks-paramset.md)类型对象，需要业务提前申请好内存，需申请足够容纳获取到的密钥属性集的内存大小。

2. 调用接口[OH_Huks_GetKeyItemParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_getkeyitemparamset)，传入上述参数。

3. 返回值为成功码/错误码，获取成功后，从参数集中读取需要的参数。

<!-- @[obtain_the_key_attributes_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/OtherOperations/GetKeyAttributes/entry/src/main/cpp/napi_init.cpp) -->
