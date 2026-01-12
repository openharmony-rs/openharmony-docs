# 使用SM2密文格式转换(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

当前支持的SM2密文格式为国密标准的ASN.1格式，其中各参数组合顺序为C1C3C2，具体参数含义请参考[转换SM2密文格式](crypto-asym-encrypt-decrypt-spec.md#转换sm2密文格式)。

开发者可指定SM2密文的参数，将其转换成符合国密标准的ASN.1格式密文。反之，也可以从国密标准的ASN.1格式密文中取出具体的SM2密文参数，便于开发者自行组合成其他格式的SM2密文。

**指定密文参数，生成标准ASN.1密文**

1. 调用[OH_CryptoSm2CiphertextSpec_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptosm2ciphertextspec_create)，创建空的SM2密文规格对象。

2. 调用[OH_CryptoSm2CiphertextSpec_SetItem](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptosm2ciphertextspec_setitem)，设置密文的各个参数（C1.x、C1.y、C2、C3）。

3. 调用[OH_CryptoSm2CiphertextSpec_Encode](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptosm2ciphertextspec_encode)，生成ASN.1格式的密文（当前密文转换仅支持SM3，实现中只校验hash长度是否为32字节）。

4. 使用完毕后，调用[OH_CryptoSm2CiphertextSpec_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptosm2ciphertextspec_destroy)销毁SM2密文规格对象。

<!-- @[create_asn1_ciphertext](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceCpp/entry/src/main/cpp/types/project/sm2/CreateASN1Ciphertext.cpp) -->


**从标准ASN.1密文中获取密文参数**

1. 调用[OH_CryptoSm2CiphertextSpec_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptosm2ciphertextspec_create)，从ASN.1格式密文创建SM2密文规格对象。

2. 调用[OH_CryptoSm2CiphertextSpec_GetItem](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptosm2ciphertextspec_getitem)，获取密文中的各个参数（C1.x、C1.y、C2、C3）。

3. 使用完毕后，调用[OH_CryptoSm2CiphertextSpec_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptosm2ciphertextspec_destroy)销毁SM2密文规格对象。

<!-- @[obtain_cipher_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceCpp/entry/src/main/cpp/types/project/sm2/ObtainCiphertext.cpp) -->

