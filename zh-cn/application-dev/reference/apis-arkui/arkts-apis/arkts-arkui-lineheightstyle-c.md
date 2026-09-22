# LineHeightStyle

```TypeScript
declare class LineHeightStyle
```

文本行高对象说明。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(lineHeight: LengthMetrics)
```

文本行高的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lineHeight | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | 是 | 文本行高设置项。如果LengthMetrics的unit值是PERCENT，当前设置不生效。LengthMetrics的value值大于0时，文本行高设置生效，否则文本行高自适应字体大小。 |

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(lineHeight: LengthMetrics, lineHeightMultiple?: number)
```

文本行高及倍数的构造函数。

> **说明：** 
> 
> - lineHeightMultiple与lineHeight或[LineSpacingStyle](arkts-arkui-linespacingstyle-c.md)同时设置时，仅lineHeightMultiple生效，行高为该行最高字体高度与倍数的乘积。
> 
> - lineHeightMultiple小于0或undefined时不生效，使用lineHeight和[LineSpacingStyle](arkts-arkui-linespacingstyle-c.md)设置行高和行间距。
> 
> - lineHeightMultiple等于0时等效于设置为1。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lineHeight | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | 是 | 文本行高设置项。LengthMetrics的value值大于0时，文本行高设置生效，否则文本行高自适应字体大小。 |
| lineHeightMultiple | number | 否 | 文本行高的倍数值。<br>取值范围：[0, +∞)，支持小数。<br>**说明：** <br>与lineHeight或[LineSpacingStyle](arkts-arkui-linespacingstyle-c.md)同时设置时，仅lineHeightMultiple生效，行高为该行最高字体高度与倍数的乘积；<br>小于0或undefined时不生效；<br>等于0时等效于设置为1。 |

## lineHeight

```TypeScript
readonly lineHeight: number
```

获取属性字符串的文本行高。

单位：[vp](arkts-arkui-length-t.md)

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lineHeightMultiple

```TypeScript
readonly lineHeightMultiple?: number
```

文本行高的倍数值。实际生效的行高为该行最高的字体高度与倍数的乘积。

**说明：** lineHeightMultiple与lineHeight或[LineSpacingStyle](arkts-arkui-linespacingstyle-c.md)同时设置时，仅lineHeightMultiple生效。lineHeightMultiple小于0或undefined时不生效。lineHeightMultiple等于0时等效于设置为1。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
