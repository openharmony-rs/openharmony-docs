# 使用SM2密文格式转换(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

当前支持的SM2密文格式为国密标准的ASN.1格式，其中各参数组合顺序为C1C3C2，具体参数含义请参考[转换SM2密文格式](crypto-asym-encrypt-decrypt-spec.md#转换sm2密文格式)。

开发者可指定SM2密文的参数，将其转换成符合国密标准的ASN.1格式密文。反之，也可以从国密标准的ASN.1格式密文中取出具体的SM2密文参数，便于开发者自行组合成其他格式的SM2密文。

**指定密文参数，生成标准ASN.1密文**

1. 构造[SM2CipherTextSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#sm2ciphertextspec12)对象，用于指定SM2密文参数。如果开发者使用的不是国密标准的ASN.1格式密文，需自行提取所需要的参数。

2. 调用[genCipherTextBySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#genciphertextbyspec12)，将SM2CipherTextSpec对象传入，生成符合国密标准的ASN.1格式的SM2密文。

3. 生成的密文可直接使用cryptoFramework进行SM2解密。

<!-- @[sm2_create_asn1_ciphertext](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceSM2/entry/src/main/ets/pages/sm2/CreateASN.1Ciphertext.ets) -->


**从标准ASN.1密文中，获取密文参数**


1. 准备符合国密标准的ASN.1格式的SM2密文。

2. 调用[getCipherTextSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#genciphertextbyspec12)，从标准密文中，获取具体的SM2密文参数。

3. 根据业务需要，自行拼接SM2密文参数，形成其他格式的SM2密文。

<!-- @[sm2_obtain_ciphertext](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceSM2/entry/src/main/ets/pages/sm2/ObtainCiphertext.ets) -->

