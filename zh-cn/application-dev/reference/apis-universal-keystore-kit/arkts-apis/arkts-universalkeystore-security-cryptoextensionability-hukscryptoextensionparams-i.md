# HuksCryptoExtensionParams

定义API中使用的选项。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## 导入模块

```TypeScript
import { CryptoExtensionAbility, HuksCryptoExtensionCertInfo, HuksCryptoExtensionResult, HuksCryptoExtensionResultCode, HuksCryptoExtensionParam, HuksCryptoExtensionParams } from '@kit.UniversalKeystoreKit';
```

## inData

```TypeScript
inData?: Uint8Array
```

操作的输入数据。

**类型：** Uint8Array

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## properties

```TypeScript
properties: HuksCryptoExtensionParam[]
```

操作的属性。

**类型：** [HuksCryptoExtensionParam](arkts-universalkeystore-security-cryptoextensionability-hukscryptoextensionparam-i.md)[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension
