# HuksCryptoExtensionResult

接口返回值的通用类型。

**起始版本：** 22

<!--Device-unnamed-export interface HuksCryptoExtensionResult--><!--Device-unnamed-export interface HuksCryptoExtensionResult-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## 导入模块

```TypeScript
import { HuksCryptoExtensionCertInfo, HuksCryptoExtensionResultCode, HuksCryptoExtensionParams, HuksCryptoExtensionParam, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';
```

## authState

```TypeScript
authState?: number
```

认证状态。

**类型：** number

**起始版本：** 22

<!--Device-HuksCryptoExtensionResult-authState?: int--><!--Device-HuksCryptoExtensionResult-authState?: int-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## certs

```TypeScript
certs?: Array<HuksCryptoExtensionCertInfo>
```

/**证书。

**类型：** Array<HuksCryptoExtensionCertInfo>

**起始版本：** 22

<!--Device-HuksCryptoExtensionResult-certs?: Array<HuksCryptoExtensionCertInfo>--><!--Device-HuksCryptoExtensionResult-certs?: Array<HuksCryptoExtensionCertInfo>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## errInfo

```TypeScript
errInfo?: huksExternalCrypto.HuksExternalErrorInfo
```

返回详细错误信息

**类型：** huksExternalCrypto.HuksExternalErrorInfo

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HuksCryptoExtensionResult-errInfo?: huksExternalCrypto.HuksExternalErrorInfo--><!--Device-HuksCryptoExtensionResult-errInfo?: huksExternalCrypto.HuksExternalErrorInfo-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## handle

```TypeScript
handle?: string
```

资源句柄。

**类型：** string

**起始版本：** 22

<!--Device-HuksCryptoExtensionResult-handle?: string--><!--Device-HuksCryptoExtensionResult-handle?: string-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## outData

```TypeScript
outData?: Uint8Array
```

返回的数据。

**类型：** Uint8Array

**起始版本：** 22

<!--Device-HuksCryptoExtensionResult-outData?: Uint8Array--><!--Device-HuksCryptoExtensionResult-outData?: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## property

```TypeScript
property?: Array<huksExternalCrypto.HuksExternalCryptoParam>
```

返回的属性信息。

**类型：** Array<huksExternalCrypto.HuksExternalCryptoParam>

**起始版本：** 22

<!--Device-HuksCryptoExtensionResult-property?: Array<huksExternalCrypto.HuksExternalCryptoParam>--><!--Device-HuksCryptoExtensionResult-property?: Array<huksExternalCrypto.HuksExternalCryptoParam>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## resourceId

```TypeScript
resourceId?: string
```

返回的资源ID。

26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HuksCryptoExtensionResult-resourceId?: string--><!--Device-HuksCryptoExtensionResult-resourceId?: string-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## resultCode

```TypeScript
resultCode: number
```

返回值的错误码。

**类型：** number

**起始版本：** 22

<!--Device-HuksCryptoExtensionResult-resultCode: int--><!--Device-HuksCryptoExtensionResult-resultCode: int-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## retryCount

```TypeScript
retryCount?: number
```

重试次数。

**类型：** number

**起始版本：** 22

<!--Device-HuksCryptoExtensionResult-retryCount?: int--><!--Device-HuksCryptoExtensionResult-retryCount?: int-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

