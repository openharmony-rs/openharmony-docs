# LineSpacingStyle

文本行间距对象说明。适用于需要调整段落内各行间距的场景，例如提升文本阅读舒适度、调整文档排版密度等。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(lineSpacing: LengthMetrics, options?: LineSpacingOptions)
```

文本行间距的构造函数。未通过该接口设置时，默认行间距为0.0。LengthMetrics的value值小于0时，取默认值0.0。当与[LineHeightStyle](arkts-arkui-lineheightstyle-c.md)的 lineHeightMultiple同时设置且lineHeightMultiple生效时，该参数不生效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lineSpacing | LengthMetrics | 是 | 文本的行间距。 取值范围：[0, +∞) |
| options | [LineSpacingOptions](arkts-arkui-linespacingoptions-i.md) | 否 | 行间距的配置项。 |

## lineSpacing

```TypeScript
readonly lineSpacing: number
```

文本行间距。取值范围：[0, +∞)单位：[vp](arkts-arkui-length-t.md)

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
readonly options?: LineSpacingOptions
```

行间距配置项。

**类型：** [LineSpacingOptions](arkts-arkui-linespacingoptions-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
