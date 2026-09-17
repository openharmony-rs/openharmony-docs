# HuksCryptoExtensionParam

Defines the type of the param used for calling the API.

**Since:** 26.0.0

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## Modules to Import

```TypeScript
import { CryptoExtensionAbility, HuksCryptoExtensionCertInfo, HuksCryptoExtensionResult, HuksCryptoExtensionResultCode, HuksCryptoExtensionParam, HuksCryptoExtensionParams } from '@kit.UniversalKeystoreKit';
```

## tag

```TypeScript
tag: huksExternalCrypto.HuksExternalCryptoTag | huks.HuksTag | number
```

Parameter tag, which is used to distinguish parameters.

**Type:** [huksExternalCrypto.HuksExternalCryptoTag](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotag-e.md) &#124; [huks.HuksTag](arkts-universalkeystore-huks-hukstag-e.md) &#124; number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## value

```TypeScript
value: boolean | number | bigint | Uint8Array
```

Value of the tag.

**Type:** boolean &#124; number &#124; bigint &#124; Uint8Array

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension
