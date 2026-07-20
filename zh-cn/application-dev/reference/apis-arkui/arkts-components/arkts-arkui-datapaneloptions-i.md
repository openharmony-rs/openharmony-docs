# DataPanelOptions

数据面板选项。

**起始版本：** 7

<!--Device-unnamed-declare interface DataPanelOptions--><!--Device-unnamed-declare interface DataPanelOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## max

```TypeScript
max?: number
```

- max大于0时，表示数据的最大值。

- max小于等于0时，max等于value数组各项的和，按比例显示。

默认值：100

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-DataPanelOptions-max?: number--><!--Device-DataPanelOptions-max?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: DataPanelType
```

数据面板的类型（不支持动态修改）。

默认值：DataPanelType.Circle

**类型：** DataPanelType

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-DataPanelOptions-type?: DataPanelType--><!--Device-DataPanelOptions-type?: DataPanelType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## values

```TypeScript
values: number[]
```

数据值列表，最多包含9个数据，大于9个数据则取前9个数据。若数据值小于0则置为0。

**类型：** number[]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-DataPanelOptions-values: number[]--><!--Device-DataPanelOptions-values: number[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

