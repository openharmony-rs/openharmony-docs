# BaselineOffsetStyle

文本基线偏移量对象说明。

**起始版本：** 12

<!--Device-unnamed-declare class BaselineOffsetStyle--><!--Device-unnamed-declare class BaselineOffsetStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: LengthMetrics)
```

文本基线偏移的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BaselineOffsetStyle-constructor(value: LengthMetrics)--><!--Device-BaselineOffsetStyle-constructor(value: LengthMetrics)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | 是 | 文本基线偏移量设置项。如果LengthMetrics的unit值是PERCENT，该设置不生效。 |

## baselineOffset

```TypeScript
readonly baselineOffset: number
```

获取属性字符串的文本基线偏移量。

单位：[vp](../../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BaselineOffsetStyle-readonly baselineOffset: number--><!--Device-BaselineOffsetStyle-readonly baselineOffset: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

