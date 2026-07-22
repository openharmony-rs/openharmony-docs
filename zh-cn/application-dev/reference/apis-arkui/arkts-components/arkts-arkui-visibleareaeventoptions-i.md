# VisibleAreaEventOptions

关于区域变化相关的参数。

**起始版本：** 12

<!--Device-unnamed-declare interface VisibleAreaEventOptions--><!--Device-unnamed-declare interface VisibleAreaEventOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## expectedUpdateInterval

```TypeScript
expectedUpdateInterval?: number
```

定义了开发者期望的计算间隔，单位为ms。当该字段小于100或为NaN时，默认取值为100；当该字段大于2^31-1时，默认取值为2^31-1。

默认值：1000

**类型：** number

**默认值：** 1000

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-VisibleAreaEventOptions-expectedUpdateInterval?: number--><!--Device-VisibleAreaEventOptions-expectedUpdateInterval?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## measureFromViewport

```TypeScript
measureFromViewport?: boolean
```

设置可见区域计算模式。

当measureFromViewport设置为true时，系统在计算该组件的可见区域时，会考虑父组件的[clip](arkts-arkui-commonmethod-c.md#clip) 属性设置。如果父组件的[clip](arkts-arkui-commonmethod-c.md#clip)为false，则认为其内的子组件可以超出其区域进行显示，因此超出父组件的区域也将被视为可见区域纳入计算；如果父组件的[clip](arkts-arkui-commonmethod-c.md#clip)设置为true，则组件超出父组件的区域会被裁剪，无法显示，因此会被视为不可见区域进行计算。而当measureFromViewport设置为false时，则不考虑[clip](arkts-arkui-commonmethod-c.md#clip)的影响，直接将组件超出父组件的部分视为不可见区域。

默认值：false

measureFromViewport设置为true时，祖先节点设置[scale](arkts-arkui-commonmethod-c.md#scale)属性，组件可见比例会被正确计算。

**类型：** boolean

**默认值：** false

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-VisibleAreaEventOptions-measureFromViewport?: boolean--><!--Device-VisibleAreaEventOptions-measureFromViewport?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ratios

```TypeScript
ratios: Array<number>
```

阈值数组。其中，每个阈值代表组件可见面积（即组件在屏幕显示区的面积，只计算父组件内的面积，超出父组件部分不会计算）与组件自身面积的比值。每个阈值的取值范围为[0.0, 1.0]，如果开发者设置的阈值小于0.0，则实际取值为0.0；如果设置的阈值大于1.0，则实际取值为1.0。

**类型：** Array&lt;number&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-VisibleAreaEventOptions-ratios: Array<number>--><!--Device-VisibleAreaEventOptions-ratios: Array<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

