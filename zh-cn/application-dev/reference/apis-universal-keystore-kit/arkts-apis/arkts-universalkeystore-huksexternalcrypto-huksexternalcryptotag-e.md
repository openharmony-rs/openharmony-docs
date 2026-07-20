# HuksExternalCryptoTag

表示调用参数的Tag。

**起始版本：** 22

<!--Device-huksExternalCrypto-export enum HuksExternalCryptoTag--><!--Device-huksExternalCrypto-export enum HuksExternalCryptoTag-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_EXT_CRYPTO_TAG_UKEY_PIN

```TypeScript
HUKS_EXT_CRYPTO_TAG_UKEY_PIN = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200001
```

表示PIN码的TAG。

**起始版本：** 22

<!--Device-HuksExternalCryptoTag-HUKS_EXT_CRYPTO_TAG_UKEY_PIN = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200001--><!--Device-HuksExternalCryptoTag-HUKS_EXT_CRYPTO_TAG_UKEY_PIN = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200001-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_EXT_CRYPTO_TAG_ABILITY_NAME

```TypeScript
HUKS_EXT_CRYPTO_TAG_ABILITY_NAME = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200002
```

表示[CryptoExtensionAbility](arkts-security-cryptoextensionability.md)的名称。

**起始版本：** 22

<!--Device-HuksExternalCryptoTag-HUKS_EXT_CRYPTO_TAG_ABILITY_NAME = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200002--><!--Device-HuksExternalCryptoTag-HUKS_EXT_CRYPTO_TAG_ABILITY_NAME = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200002-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_EXT_CRYPTO_TAG_EXTRA_DATA

```TypeScript
HUKS_EXT_CRYPTO_TAG_EXTRA_DATA = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200003
```

外部数据，在通用查询场景，表示返回的数据。

**起始版本：** 22

<!--Device-HuksExternalCryptoTag-HUKS_EXT_CRYPTO_TAG_EXTRA_DATA = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200003--><!--Device-HuksExternalCryptoTag-HUKS_EXT_CRYPTO_TAG_EXTRA_DATA = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200003-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_EXT_CRYPTO_TAG_UID

```TypeScript
HUKS_EXT_CRYPTO_TAG_UID = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_INT | 200004
```

表示调用方的uid。

**起始版本：** 22

<!--Device-HuksExternalCryptoTag-HUKS_EXT_CRYPTO_TAG_UID = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_INT | 200004--><!--Device-HuksExternalCryptoTag-HUKS_EXT_CRYPTO_TAG_UID = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_INT | 200004-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_EXT_CRYPTO_TAG_PURPOSE

```TypeScript
HUKS_EXT_CRYPTO_TAG_PURPOSE = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_INT | 200005
```

表示证书链对应密钥的使用类型，具体类型详见[CertificatePurpose定义](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-certificatemanager-certificatepurpose-e.md)。

**起始版本：** 22

<!--Device-HuksExternalCryptoTag-HUKS_EXT_CRYPTO_TAG_PURPOSE = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_INT | 200005--><!--Device-HuksExternalCryptoTag-HUKS_EXT_CRYPTO_TAG_PURPOSE = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_INT | 200005-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO

```TypeScript
HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200007
```

表示获取资源ID所需的信息，格式和内容由厂商自定义。

26.0.0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HuksExternalCryptoTag-HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200007--><!--Device-HuksExternalCryptoTag-HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200007-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_EXT_CRYPTO_TAG_ABILITY_INFO

```TypeScript
HUKS_EXT_CRYPTO_TAG_ABILITY_INFO = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200008
```

表示密钥管理扩展自定义PIN码弹窗相关Ability列表信息，在注册密钥管理扩展时，同步注册，详见[provider注册示例](docroot://security/UniversalKeystoreKit/huks-extension-registration-and-unregistration-arkts.md)。注册了自定义弹窗，则在PIN码认证时允许拉起自定义弹窗，进行PIN码认证等操作。

HUKS_EXT_CRYPTO_TAG_ABILITY_NAME中的JSON列表由多个JSON对象组成，每个JSON对象包含两个字段：AbilityName和index。字段应遵循以下要求：

1.AbilityName：长度范围为1~128字节。

2.index：其值为resourceId，最大长度为512字节。允许单个CryptoExtension下该字段为空，为空时传输空字符串，该字段不允许重复。在搜索时优先匹配index对应的UIExtensionAbility，当不存在时返回index为空的UIExtensionAbility。

26.0.0

**模型约束**：此接口仅可在Stage模型下使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HuksExternalCryptoTag-HUKS_EXT_CRYPTO_TAG_ABILITY_INFO = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200008--><!--Device-HuksExternalCryptoTag-HUKS_EXT_CRYPTO_TAG_ABILITY_INFO = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200008-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME

```TypeScript
HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200009
```

表示CryptoExtensionAbility所属的HAP Bundle名称。

26.0.0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HuksExternalCryptoTag-HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200009--><!--Device-HuksExternalCryptoTag-HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200009-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

