# LetterSpacingStyle

文本字符间距对象说明。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class LetterSpacingStyle--><!--Device-unnamed-export declare class LetterSpacingStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: LengthMetrics)
```

文本字符间距的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LetterSpacingStyle-constructor(value: LengthMetrics)--><!--Device-LetterSpacingStyle-constructor(value: LengthMetrics)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | 是 | 文本字符间距设置项。如果LengthMetrics的unit值是PERCENT，该设置不生效。 |

## letterSpacing

```TypeScript
readonly letterSpacing: double
```

获取属性字符串的文本字符间距。 单位：[vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LetterSpacingStyle-readonly letterSpacing: double--><!--Device-LetterSpacingStyle-readonly letterSpacing: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

