# Element

```TypeScript
interface Element
```

定义隐私搜索使用的数据集元素。每个元素包含一个用于匹配的键。可选的哈希算法，以及用于PIR协议检索的可选值。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Security.Asset

## 导入模块

```TypeScript
```

## elemKey

```TypeScript
elemKey: Uint8Array
```

数据集元素的键，用于与隐私目标进行匹配。

**类型：** Uint8Array

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.Asset

## elemValue

```TypeScript
elemValue?: Uint8Array
```

与元素键关联的值。该字段在PIR协议中使用。当找到匹配项时，检索附加的值。如果未指定，则元素只支持键匹配，不支持值检索。

**类型：** Uint8Array

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.Asset

## hashAlg

```TypeScript
hashAlg?: HashAlg
```

用于散列元素键的散列算法。如果未指定，则元素键将与SHA256默认值一起使用。

**类型：** [HashAlg](arkts-dataprotection-privacycomputation-hashalg-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.Asset
