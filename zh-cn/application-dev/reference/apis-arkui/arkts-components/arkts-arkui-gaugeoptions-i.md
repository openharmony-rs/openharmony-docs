# GaugeOptions

数据量规图表选项。

**起始版本：** 18

<!--Device-unnamed-interface GaugeOptions--><!--Device-unnamed-interface GaugeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## max

```TypeScript
max?: number
```

当前数据段最大值。

默认值：100

**说明：**

max小于min时使用默认值0和100。

max和min支持负数。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GaugeOptions-max?: number--><!--Device-GaugeOptions-max?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## min

```TypeScript
min?: number
```

当前数据段最小值。

默认值：0

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GaugeOptions-min?: number--><!--Device-GaugeOptions-min?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: number
```

量规图的当前数据值，即图中指针指向位置。用于组件创建时量规图初始值的预置。

默认值：0

**说明：**

value不在min和max范围内时使用min作为默认值。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GaugeOptions-value: number--><!--Device-GaugeOptions-value: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

