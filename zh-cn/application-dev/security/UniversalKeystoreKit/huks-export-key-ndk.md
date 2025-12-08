# 密钥导出(C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

业务需要获取持久化存储的非对称密钥的公钥时使用，当前支持ECC/RSA/ED25519/X25519/SM2的公钥导出。

>**说明：**
>
> <!--RP1-->轻量级设备<!--RP1End-->仅支持RSA公钥导出。

从API 23开始支持[群组密钥](huks-group-key-overview.md)特性。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so)
```

## 开发步骤

1. 构造对应参数。
   - keyAlias：密钥别名，封装成[OH_Huks_Blob](../../reference/apis-universal-keystore-kit/capi-hukstypeapi-oh-huks-blob.md)结构，密钥别名最大长度为128字节。
   - paramSetIn：预留参数，暂不需要处理，传空即可。
   - key：用于放置导出的公钥，为[OH_Huks_Blob](../../reference/apis-universal-keystore-kit/capi-hukstypeapi-oh-huks-blob.md)类型对象，需要业务提前申请好内存，需申请足够容纳获取到的密钥属性集的内存大小。

2. 调用接口[OH_Huks_GetKeyItemParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_getkeyitemparamset)，传入上述参数。

3. 返回值为成功码/错误码，导出公钥以标准的X.509规范的DER格式封装在参数key中，具体请参考[公钥材料格式](huks-concepts.md#公钥材料格式)。

<!-- @[get_persistent_storage_asymmetric_public_keys_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/OtherOperations/KeyExport/entry/src/main/cpp/napi_init.cpp) -->