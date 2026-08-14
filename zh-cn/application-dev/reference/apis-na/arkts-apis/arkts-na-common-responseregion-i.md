# ResponseRegion

Defines the response region interface.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface ResponseRegion--><!--Device-unnamed-export declare interface ResponseRegion-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: LengthMetrics | string
```

Sets the height of the current touchRect.

**类型：** [LengthMetrics](arkts-na-graphics-lengthmetrics-c.md) \| string

**默认值：** LengthMetrics.percent(1)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ResponseRegion-height?: LengthMetrics | string--><!--Device-ResponseRegion-height?: LengthMetrics | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tool

```TypeScript
tool?: ResponseRegionSupportedTool
```

The event tool type applicable to this response region.

**类型：** [ResponseRegionSupportedTool](../../apis-arkui/arkts-apis/arkts-arkui-responseregionsupportedtool-e.md)

**默认值：** ResponseRegionSupportedTool.ALL

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ResponseRegion-tool?: ResponseRegionSupportedTool--><!--Device-ResponseRegion-tool?: ResponseRegionSupportedTool-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: LengthMetrics | string
```

Sets the width of the current touchRect.

**类型：** [LengthMetrics](arkts-na-graphics-lengthmetrics-c.md) \| string

**默认值：** LengthMetrics.percent(1)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ResponseRegion-width?: LengthMetrics | string--><!--Device-ResponseRegion-width?: LengthMetrics | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: LengthMetrics
```

Horizontal axis coordinate

**类型：** [LengthMetrics](arkts-na-graphics-lengthmetrics-c.md)

**默认值：** LengthMetrics.vp(0)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ResponseRegion-x?: LengthMetrics--><!--Device-ResponseRegion-x?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: LengthMetrics
```

Vertical axis coordinate.

**类型：** [LengthMetrics](arkts-na-graphics-lengthmetrics-c.md)

**默认值：** LengthMetrics.vp(0)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ResponseRegion-y?: LengthMetrics--><!--Device-ResponseRegion-y?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

