# LineHeightStyle

文本行高对象说明。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class LineHeightStyle--><!--Device-unnamed-export declare class LineHeightStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(lineHeight: LengthMetrics)
```

文本行高的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LineHeightStyle-constructor(lineHeight: LengthMetrics)--><!--Device-LineHeightStyle-constructor(lineHeight: LengthMetrics)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lineHeight | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | 是 | 文本行高设置项。LengthMetrics的value值大于0时，文本行高设置生效，否则文本行高自适应字体大小。 |

## constructor

```TypeScript
constructor(lineHeight: LengthMetrics, lineHeightMultiple: double)
```

文本行高及倍数的构造函数。 > **说明：** > > - lineHeightMultiple与lineHeight或 > [LineSpacingStyle](../../../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#linespacingstyle)同时设置 > 时，仅lineHeightMultiple生效，行高为该行最高字体高度与倍数的乘积。 > > - lineHeightMultiple小于0或undefined时不生效，使用lineHeight和 > [LineSpacingStyle](../../../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#linespacingstyle)设置行高和 > 行间距。 > > - lineHeightMultiple等于0时等效于设置为1。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LineHeightStyle-constructor(lineHeight: LengthMetrics, lineHeightMultiple: double)--><!--Device-LineHeightStyle-constructor(lineHeight: LengthMetrics, lineHeightMultiple: double)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lineHeight | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | 是 | 文本行高设置项。LengthMetrics的value值大于0时，文本行高设置生效，否则文本行高自适应字体大小。 |
| lineHeightMultiple | double | 是 | 文本行高的倍数值。&lt;br/&gt;取值范围：[0, +∞)，支持小数。 |

## lineHeight

```TypeScript
readonly lineHeight: double
```

获取属性字符串的文本行高。 单位：[vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LineHeightStyle-readonly lineHeight: double--><!--Device-LineHeightStyle-readonly lineHeight: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lineHeightMultiple

```TypeScript
readonly lineHeightMultiple?: double
```

文本行高的倍数值。实际生效的行高为该行最高的字体高度与倍数的乘积。

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LineHeightStyle-readonly lineHeightMultiple?: double--><!--Device-LineHeightStyle-readonly lineHeightMultiple?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

