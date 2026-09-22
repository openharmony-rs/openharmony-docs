# SearchResult

```TypeScript
interface SearchResult
```

定义解密后的最终搜索结果，指示是否找到匹配项以及与匹配元素关联的可选附加值。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Security.Asset

## 导入模块

```TypeScript
```

## attachedValues

```TypeScript
attachedValues?: Uint8Array[]
```

与匹配元素关联的附加值。此字段仅在以下情况下可用：使用PIR协议并找到匹配项；否则未定义。

**类型：** Uint8Array[]

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.Asset

## matchedResult

```TypeScript
matchedResult: boolean
```

指示是否在数据集中找到隐私目标。True表示找到了匹配项；false表示不匹配。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.Asset
