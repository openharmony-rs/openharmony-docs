# TargetElement

```TypeScript
interface TargetElement
```

定义隐私计算的目标元素，包括原始元素数据和可选的哈希算法。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Security.Asset

## 导入模块

```TypeScript
```

## elemData

```TypeScript
elemData: Uint8Array
```

要搜索的目标元素的原始数据。

**类型：** Uint8Array

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.Asset

## hashAlg

```TypeScript
hashAlg?: HashAlg
```

用于散列目标元素的散列算法。如果未指定，则元素数据将与SHA256默认值一起使用。

**类型：** [HashAlg](arkts-dataprotection-privacycomputation-hashalg-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.Asset
