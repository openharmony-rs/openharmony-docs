# HuksCryptoExtensionParam

定义调用接口的param类型。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface HuksCryptoExtensionParam--><!--Device-unnamed-export interface HuksCryptoExtensionParam-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## 导入模块

```TypeScript
import { HuksCryptoExtensionCertInfo, HuksCryptoExtensionResultCode, HuksCryptoExtensionParams, HuksCryptoExtensionParam, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';
```

## tag

```TypeScript
tag: huksExternalCrypto.HuksExternalCryptoTag | huks.HuksTag | number
```

参数标签，用于区分参数。

**类型：** huksExternalCrypto.HuksExternalCryptoTag | huks.HuksTag | number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HuksCryptoExtensionParam-tag: huksExternalCrypto.HuksExternalCryptoTag | huks.HuksTag | number--><!--Device-HuksCryptoExtensionParam-tag: huksExternalCrypto.HuksExternalCryptoTag | huks.HuksTag | number-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## value

```TypeScript
value: boolean | number | bigint | Uint8Array
```

标签的值。

**类型：** boolean | number | bigint | Uint8Array

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HuksCryptoExtensionParam-value: boolean | int | bigint | Uint8Array--><!--Device-HuksCryptoExtensionParam-value: boolean | int | bigint | Uint8Array-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

