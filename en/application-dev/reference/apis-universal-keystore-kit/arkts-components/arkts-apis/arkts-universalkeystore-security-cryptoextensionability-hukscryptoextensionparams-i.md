# HuksCryptoExtensionParams

```TypeScript
export interface HuksCryptoExtensionParams
```

Defines options used in the APIs.

**Since:** 26.0.0

<!--Device-unnamed-export interface HuksCryptoExtensionParams--><!--Device-unnamed-export interface HuksCryptoExtensionParams-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## Modules to Import

```TypeScript
import { CryptoExtensionAbility, HuksCryptoExtensionCertInfo, HuksCryptoExtensionResult, HuksCryptoExtensionResultCode, HuksCryptoExtensionParam, HuksCryptoExtensionParams } from '@kit.UniversalKeystoreKit';
```

## inData

```TypeScript
inData?: Uint8Array
```

The input data of the operation.

**Type:** Uint8Array

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-HuksCryptoExtensionParams-inData?: Uint8Array--><!--Device-HuksCryptoExtensionParams-inData?: Uint8Array-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## properties

```TypeScript
properties: HuksCryptoExtensionParam[]
```

The properties of the operation.

**Type:** [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-HuksCryptoExtensionParams-properties: HuksCryptoExtensionParam[]--><!--Device-HuksCryptoExtensionParams-properties: HuksCryptoExtensionParam[]-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension
