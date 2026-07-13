# HuksCryptoExtensionResult

接口返回值的通用类型。

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## authState

```TypeScript
authState?: number
```

认证状态。

**类型：** number

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## certs

```TypeScript
certs?: Array<HuksCryptoExtensionCertInfo>
```

/**
证书。

**类型：** Array<HuksCryptoExtensionCertInfo>

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## errInfo

```TypeScript
errInfo?: huksExternalCrypto.HuksExternalErrorInfo
```

返回详细错误信息

**类型：** huksExternalCrypto.HuksExternalErrorInfo

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## handle

```TypeScript
handle?: string
```

资源句柄。

**类型：** string

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## outData

```TypeScript
outData?: Uint8Array
```

返回的数据。

**类型：** Uint8Array

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## property

```TypeScript
property?: Array<huksExternalCrypto.HuksExternalCryptoParam>
```

返回的属性信息。

**类型：** Array<huksExternalCrypto.HuksExternalCryptoParam>

**起始版本：** 22

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

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## resultCode

```TypeScript
resultCode: number
```

返回值的错误码。

**类型：** number

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## retryCount

```TypeScript
retryCount?: number
```

重试次数。

**类型：** number

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

