# 签名/验签介绍及算法规格

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

Ukey PIN码认证之后，应用可以通过resouceId操作对应密钥执行签名操作。该能力通过HUKS提供的三段式接口实现，应用指定相应的算法参数即可(包括算法类型，目的，填充，摘要等)。

> **说明：**
>
> 1. 通过[HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag)指定是外部密钥管理扩展中管理的密钥。
> 2. 三段式操作执行相关的签名操作过程中，keyAlias参数需指定为resourceId。
> 3. 三段式的finish操作会释放资源，中间异常需要通过abort释放资源。

## 规格

具体规格与外部硬件密钥管理扩展实现相关，不同厂家实现有差异。

| 算法/摘要算法/填充模式 | 备注 | API级别 | 是否必选规格 |
| -------- | -------- | -------- | -------- |
| RSA/SHA256/PKCS1 | 签名是ASN1格式。 | 22+ | 是 |
| RSA/SHA384/PKCS1 | 签名是ASN1格式。 | 22+ | 是 |
| RSA/SHA512/PKCS1 | 签名是ASN1格式。 | 22+ | 是 |
| RSA/SHA256/PSS | 签名是ASN1格式。 | 22+ | 是 |
| RSA/SHA384/PSS | 签名是ASN1格式。 | 22+ | 是 |
| RSA/SHA512/PSS | 签名是ASN1格式。 | 22+ | 是 |
| ECC/SHA256 | 签名是ASN1格式。 | 22+ | 是 |
| ECC/SHA384 | 签名是ASN1格式。 | 22+ | 是 |
| ECC/SHA512 | 签名是ASN1格式。 | 22+ | 是 |