# LineSpacingStyle

文本行间距对象说明。

**起始版本：** 26.0.0

<!--Device-unnamed-declare class LineSpacingStyle--><!--Device-unnamed-declare class LineSpacingStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor"></a>
## constructor

```TypeScript
constructor(lineSpacing: LengthMetrics, options?: LineSpacingOptions)
```

文本行间距的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LineSpacingStyle-constructor(lineSpacing: LengthMetrics, options?: LineSpacingOptions)--><!--Device-LineSpacingStyle-constructor(lineSpacing: LengthMetrics, options?: LineSpacingOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lineSpacing | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | 是 | 文本的行间距。<br/>默认值：0.0<br/>取值范围：[0, +∞) <br/>**说明：** LengthMetrics的value值小于0时，取默认值0.0。 |
| options | [LineSpacingOptions](arkts-arkui-linespacingoptions-i.md) | 否 | 行间距的配置项。<br/>默认值：{ onlyBetweenLines: false } |

## lineSpacing

```TypeScript
readonly lineSpacing: number
```

文本行间距。

取值范围：[0, +∞)

单位：[vp](docroot://reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LineSpacingStyle-readonly lineSpacing: number--><!--Device-LineSpacingStyle-readonly lineSpacing: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
readonly options?: LineSpacingOptions
```

行间距配置项。

**类型：** LineSpacingOptions

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LineSpacingStyle-readonly options?: LineSpacingOptions--><!--Device-LineSpacingStyle-readonly options?: LineSpacingOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

