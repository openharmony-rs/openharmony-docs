# PrivacyProtocol

```TypeScript
interface PrivacyProtocol
```

定义隐私协议配置，包括数据集大小、协议类型等。用于隐私保护计算。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Security.Asset

## 导入模块

```TypeScript
```

## dataSetSize

```TypeScript
dataSetSize: DataSetSize
```

隐私协议的数据集大小。确定比较次数单个结果密文可以包含。结果密文总数生成的是由element.size/dataSetSize决定的。选择合适的数据集大小基于隐私搜索中元素的数量和每个元素的可接受大小结果密文。

**类型：** [DataSetSize](arkts-dataprotection-privacycomputation-datasetsize-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.Asset

## protocolType

```TypeScript
protocolType: ProtocolType
```

隐私计算的协议类型。决定隐私保护计算方法（PSI或PIR）。

**类型：** [ProtocolType](arkts-dataprotection-privacycomputation-protocoltype-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.Asset
