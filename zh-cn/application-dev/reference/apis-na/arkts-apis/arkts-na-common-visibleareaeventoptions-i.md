# VisibleAreaEventOptions

Defines the options about VisibleAreaEvent.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface VisibleAreaEventOptions--><!--Device-unnamed-export declare interface VisibleAreaEventOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## expectedUpdateInterval

```TypeScript
expectedUpdateInterval?: int
```

The value of expectedUpdateInterval indicates desired update period(ms).

**类型：** int

**默认值：** 1000

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VisibleAreaEventOptions-expectedUpdateInterval?: int--><!--Device-VisibleAreaEventOptions-expectedUpdateInterval?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## measureFromViewport

```TypeScript
measureFromViewport?: boolean
```

When this parameter is set to true, the parts of the component that exceed the parent component's area will also be included in the visible area calculation. However, this only applies if the parent component does not explicitly set the clip property to true. If the parent component sets clip to true, regardless of the value of this parameter, the parts that exceed the parent component's area will still be treated as invisible in the visible area calculation.

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VisibleAreaEventOptions-measureFromViewport?: boolean--><!--Device-VisibleAreaEventOptions-measureFromViewport?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ratios

```TypeScript
ratios: Array<double>
```

Each number in ratios indicates the value of visibility ratio. Each number in the Array value range in [0, 1].

**类型：** Array&lt;double&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VisibleAreaEventOptions-ratios: Array<double>--><!--Device-VisibleAreaEventOptions-ratios: Array<double>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

