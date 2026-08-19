# KemEncapResult

KEM封装结果。

**起始版本：** 26.0.0

<!--Device-cryptoFramework-interface KemEncapResult--><!--Device-cryptoFramework-interface KemEncapResult-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## sharedSecret

```TypeScript
sharedSecret: Uint8Array
```

KEM的共享密钥。

**类型：** Uint8Array

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-KemEncapResult-sharedSecret: Uint8Array--><!--Device-KemEncapResult-sharedSecret: Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

## wrappedKey

```TypeScript
wrappedKey: Uint8Array
```

KEM封装的密钥，即KEM的密文。

**类型：** Uint8Array

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-KemEncapResult-wrappedKey: Uint8Array--><!--Device-KemEncapResult-wrappedKey: Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

