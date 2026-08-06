# LineSpacingStyle

文本行间距对象说明。适用于需要调整段落内各行间距的场景，例如提升文本阅读舒适度、调整文档排版密度等。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

<!--Device-unnamed-declare class LineSpacingStyle--><!--Device-unnamed-declare class LineSpacingStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(lineSpacing: LengthMetrics, options?: LineSpacingOptions)
```

文本行间距的构造函数。未通过该接口设置时，默认行间距为0.0。LengthMetrics的value值小于0时，取默认值0.0。当与[LineHeightStyle]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的 lineHeightMultiple同时设置且lineHeightMultiple生效时，该参数不生效。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LineSpacingStyle-constructor(lineSpacing: LengthMetrics, options?: LineSpacingOptions)--><!--Device-LineSpacingStyle-constructor(lineSpacing: LengthMetrics, options?: LineSpacingOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lineSpacing | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 文本的行间距。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值范围：[0, +∞) |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 行间距的配置项。 |

## lineSpacing

```TypeScript
readonly lineSpacing: number
```

文本行间距。 取值范围：\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_

**类型：** number

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LineSpacingStyle-readonly options?: LineSpacingOptions--><!--Device-LineSpacingStyle-readonly options?: LineSpacingOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

