# HuksExternalCryptoTag

Enumerates the tags used to invoke parameters.

**Since:** 22

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_EXT_CRYPTO_TAG_UKEY_PIN

```TypeScript
HUKS_EXT_CRYPTO_TAG_UKEY_PIN = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200001
```

Tag of the PIN.

**Since:** 22

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_EXT_CRYPTO_TAG_ABILITY_NAME

```TypeScript
HUKS_EXT_CRYPTO_TAG_ABILITY_NAME = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200002
```

Name of [CryptoExtensionAbility](arkts-universalkeystore-security-cryptoextensionability-cryptoextensionability-c.md).

**Since:** 22

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_EXT_CRYPTO_TAG_EXTRA_DATA

```TypeScript
HUKS_EXT_CRYPTO_TAG_EXTRA_DATA = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200003
```

External data, which indicates the return data in the common query scenario.

**Since:** 22

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_EXT_CRYPTO_TAG_UID

```TypeScript
HUKS_EXT_CRYPTO_TAG_UID = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_INT | 200004
```

UID of the caller.

**Since:** 22

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_EXT_CRYPTO_TAG_PURPOSE

```TypeScript
HUKS_EXT_CRYPTO_TAG_PURPOSE = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_INT | 200005
```

Usage type of the key corresponding to the certificate chain. For details, see [CertificatePurpose](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-certificatemanager-certificatepurpose-e.md).

**Since:** 22

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO

```TypeScript
HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200007
```

Specify the information required to obtain the resource ID. The format and content are defined by the provider.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_EXT_CRYPTO_TAG_ABILITY_INFO

```TypeScript
HUKS_EXT_CRYPTO_TAG_ABILITY_INFO = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200008
```

Specifies the ability configuration for the custom PIN dialog.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME

```TypeScript
HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME = HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 200009
```

Specifies the hap bundle name of the crypto extension ability.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension
