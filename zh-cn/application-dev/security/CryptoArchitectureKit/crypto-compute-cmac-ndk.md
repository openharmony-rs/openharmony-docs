# 消息认证码计算CMAC(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

CMAC通过使用分组密码（如AES）和一个密钥来生成认证码，确保消息在传输过程中未被篡改。

## 开发步骤

在调用update接口传入数据时，可以[一次性传入](#cmac一次性传入)，也可以把数据人工[分段传入](#cmac分段传入)。对于同一段数据而言，是否分段，计算结果没有差异。对于数据量较大的数据，开发者可以根据实际需求选择是否分段传入。

下面分别提供两种方式的示例代码。

### CMAC（一次性传入）

1. 调用[OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create)、[OH_CryptoSymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate)生成密钥算法为AES128的对称密钥（symKey）。

2. 调用[OH_CryptoMac_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_create)，指定字符串参数'CMAC'，创建MAC算法为CMAC的MAC生成器。

3. 调用[OH_CryptoMac_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_setparam)，指定参数CRYPTO_MAC_CIPHER_NAME_STR，设置分组密码算法名称。

4. 调用[OH_CryptoMac_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_init)，指定共享对称密钥（symKey），初始化MAC对象。

5. 调用[OH_CryptoMac_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_update)，传入自定义消息，进行消息认证码计算。

6. 调用[OH_CryptoMac_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_final)，获取MAC计算结果。

7. 调用[OH_CryptoMac_GetLength](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_getlength)，获取MAC消息认证码的长度，单位为字节。

<!-- @[message_auth_cmac_single_time](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageAuthenticationCode/entry/src/main/cpp/types/project/cmac/singleTime.cpp) -->


### CMAC（分段传入）

与一次性传入的步骤基本相同，区别在于多次调用[OH_CryptoMac_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_update)来处理分段数据。

<!-- @[message_auth_cmac_segmentation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageAuthenticationCode/entry/src/main/cpp/types/project/cmac/segmentation.cpp) -->

