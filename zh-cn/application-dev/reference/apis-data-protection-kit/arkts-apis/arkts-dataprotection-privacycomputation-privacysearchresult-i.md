# PrivacySearchResult

```TypeScript
interface PrivacySearchResult
```

定义隐私搜索操作的结果，包含结果的密文。和可选值密文。

**起始版本：** 26.0.1

<!--Device-privacyComputation-interface PrivacySearchResult--><!--Device-privacyComputation-interface PrivacySearchResult-End-->

**系统能力：** SystemCapability.Security.Asset

## 导入模块

```TypeScript
import { privacyComputation } from '@kit.DataProtectionKit';
```

## resultCipherText

```TypeScript
resultCipherText: Uint8Array[]
```

隐私搜索生成的结果密文数组。这些密文对搜索结果进行编码，需要通过getSearchResult进行解密。

**类型：** Uint8Array[]

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-PrivacySearchResult-resultCipherText: Uint8Array[]--><!--Device-PrivacySearchResult-resultCipherText: Uint8Array[]-End-->

**系统能力：** SystemCapability.Security.Asset

## valueCipherText

```TypeScript
valueCipherText?: Uint8Array[]
```

使用PIR协议进行隐私搜索时生成的值密文数组。这些密文包含与匹配元素相关的加密值。

**类型：** Uint8Array[]

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-PrivacySearchResult-valueCipherText?: Uint8Array[]--><!--Device-PrivacySearchResult-valueCipherText?: Uint8Array[]-End-->

**系统能力：** SystemCapability.Security.Asset
