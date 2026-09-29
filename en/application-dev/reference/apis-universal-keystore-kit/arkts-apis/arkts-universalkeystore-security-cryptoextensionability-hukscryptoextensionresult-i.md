# HuksCryptoExtensionResult

```TypeScript
export interface HuksCryptoExtensionResult
```

Represents the operation result of crypto extension.

**Since:** 22

<!--Device-unnamed-export interface HuksCryptoExtensionResult--><!--Device-unnamed-export interface HuksCryptoExtensionResult-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## Modules to Import

```TypeScript
import { CryptoExtensionAbility, HuksCryptoExtensionCertInfo, HuksCryptoExtensionResult, HuksCryptoExtensionResultCode, HuksCryptoExtensionParam, HuksCryptoExtensionParams } from '@kit.UniversalKeystoreKit';
```

## authState

```TypeScript
authState?: number
```

Auth state.

**Type:** number

**Since:** 22

<!--Device-HuksCryptoExtensionResult-authState?: int--><!--Device-HuksCryptoExtensionResult-authState?: int-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## certs

```TypeScript
certs?: Array<HuksCryptoExtensionCertInfo>
```

The cert array.

**Type:** Array&lt;[HuksCryptoExtensionCertInfo](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensioncertinfo-i.md)&gt;

**Since:** 22

<!--Device-HuksCryptoExtensionResult-certs?: Array<HuksCryptoExtensionCertInfo>--><!--Device-HuksCryptoExtensionResult-certs?: Array<HuksCryptoExtensionCertInfo>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## errInfo

```TypeScript
errInfo?: huksExternalCrypto.HuksExternalErrorInfo
```

The detailed error information returned.

**Type:** [huksExternalCrypto.HuksExternalErrorInfo](arkts-universalkeystore-huksexternalcrypto-huksexternalerrorinfo-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-HuksCryptoExtensionResult-errInfo?: huksExternalCrypto.HuksExternalErrorInfo--><!--Device-HuksCryptoExtensionResult-errInfo?: huksExternalCrypto.HuksExternalErrorInfo-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## handle

```TypeScript
handle?: string
```

The provider resource handle.

**Type:** string

**Since:** 22

<!--Device-HuksCryptoExtensionResult-handle?: string--><!--Device-HuksCryptoExtensionResult-handle?: string-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## outData

```TypeScript
outData?: Uint8Array
```

Returned data.

**Type:** Uint8Array

**Since:** 22

<!--Device-HuksCryptoExtensionResult-outData?: Uint8Array--><!--Device-HuksCryptoExtensionResult-outData?: Uint8Array-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## property

```TypeScript
property?: Array<huksExternalCrypto.HuksExternalCryptoParam>
```

Returned property info.

**Type:** Array&lt;[huksExternalCrypto.HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt;

**Since:** 22

<!--Device-HuksCryptoExtensionResult-property?: Array<huksExternalCrypto.HuksExternalCryptoParam>--><!--Device-HuksCryptoExtensionResult-property?: Array<huksExternalCrypto.HuksExternalCryptoParam>-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## resourceId

```TypeScript
resourceId?: string
```

The returned resource ID.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-HuksCryptoExtensionResult-resourceId?: string--><!--Device-HuksCryptoExtensionResult-resourceId?: string-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## resultCode

```TypeScript
resultCode: number
```

Returned code.

**Type:** number

**Since:** 22

<!--Device-HuksCryptoExtensionResult-resultCode: int--><!--Device-HuksCryptoExtensionResult-resultCode: int-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## retryCount

```TypeScript
retryCount?: number
```

The remaining retry count when the PIN is incorrect.

**Type:** number

**Since:** 22

<!--Device-HuksCryptoExtensionResult-retryCount?: int--><!--Device-HuksCryptoExtensionResult-retryCount?: int-End-->

**System capability:** SystemCapability.Security.Huks.CryptoExtension
