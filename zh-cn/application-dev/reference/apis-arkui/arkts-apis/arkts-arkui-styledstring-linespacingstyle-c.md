# LineSpacingStyle

文本行间距对象说明。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare class LineSpacingStyle--><!--Device-unnamed-export declare class LineSpacingStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(lineSpacing: LengthMetrics, options?: LineSpacingOptions)
```

文本行间距的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LineSpacingStyle-constructor(lineSpacing: LengthMetrics, options?: LineSpacingOptions)--><!--Device-LineSpacingStyle-constructor(lineSpacing: LengthMetrics, options?: LineSpacingOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lineSpacing | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | 是 | 文本的行间距。<br/>默认值：0.0<br/>取值范围： [0, +∞)<br/>**说明：** LengthMetrics的value值小于0时，取默认值0.0。 |
| options | [LineSpacingOptions](arkts-arkui-textcommon-linespacingoptions-i.md) | 否 | 行间距的配置项。<br/>默认值：{ onlyBetweenLines: false } |

## lineSpacing

```TypeScript
readonly lineSpacing: double
```

文本行间距。 取值范围：[0, +∞) 单位：[vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LineSpacingStyle-readonly lineSpacing: double--><!--Device-LineSpacingStyle-readonly lineSpacing: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
readonly options?: LineSpacingOptions
```

行间距配置项。

**类型：** [LineSpacingOptions](arkts-arkui-textcommon-linespacingoptions-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LineSpacingStyle-readonly options?: LineSpacingOptions--><!--Device-LineSpacingStyle-readonly options?: LineSpacingOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

