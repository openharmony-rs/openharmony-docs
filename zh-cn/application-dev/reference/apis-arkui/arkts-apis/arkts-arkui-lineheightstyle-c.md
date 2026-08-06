# LineHeightStyle

文本行高对象说明。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare class LineHeightStyle--><!--Device-unnamed-declare class LineHeightStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(lineHeight: LengthMetrics)
```

文本行高的构造函数。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LineHeightStyle-constructor(lineHeight: LengthMetrics)--><!--Device-LineHeightStyle-constructor(lineHeight: LengthMetrics)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lineHeight | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 文本行高设置项。如果LengthMetrics的unit值是PERCENT，当前设置不生效。LengthMetrics的value值大于0时，文本行高设置生效，否则文本行高自适应字体大小。 |

## constructor

```TypeScript
constructor(lineHeight: LengthMetrics, lineHeightMultiple?: number)
```

文本行高及倍数的构造函数。 > **说明：** > > - lineHeightMultiple与lineHeight或[LineSpacingStyle]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_同时设置时，仅lineHeightMultiple生效，行高为该行最高字体高度 > 与倍数的乘积。 > > - lineHeightMultiple小于0或undefined时不生效，使用lineHeight和[LineSpacingStyle]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_设置行高和行间距。 > > - lineHeightMultiple等于0时等效于设置为1。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LineHeightStyle-constructor(lineHeight: LengthMetrics, lineHeightMultiple?: number)--><!--Device-LineHeightStyle-constructor(lineHeight: LengthMetrics, lineHeightMultiple?: number)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lineHeight | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 文本行高设置项。LengthMetrics的value值大于0时，文本行高设置生效，否则文本行高自适应字体大小。 |
| lineHeightMultiple | number | 否 | 文本行高的倍数值。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值范围：[0, +∞)，支持小数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**说明：**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_与lineHeight或[LineSpacingStyle]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_同时设置时，仅lineHeightMultiple生效，行高为该行最高字体高度与倍数的乘积；\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_小于0或undefined时不生效；\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_等于0时等效于设置为1。 |

## lineHeight

```TypeScript
readonly lineHeight: number
```

获取属性字符串的文本行高。 单位：\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LineHeightStyle-readonly lineHeight: number--><!--Device-LineHeightStyle-readonly lineHeight: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lineHeightMultiple

```TypeScript
readonly lineHeightMultiple?: number
```

文本行高的倍数值。实际生效的行高为该行最高的字体高度与倍数的乘积。 **说明：** lineHeightMultiple与lineHeight或[LineSpacingStyle]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_同时设置时，仅lineHeightMultiple生效。 lineHeightMultiple小于0或undefined时不生效。lineHeightMultiple等于0时等效于设置为1。

**类型：** number

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LineHeightStyle-readonly lineHeightMultiple?: number--><!--Device-LineHeightStyle-readonly lineHeightMultiple?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

