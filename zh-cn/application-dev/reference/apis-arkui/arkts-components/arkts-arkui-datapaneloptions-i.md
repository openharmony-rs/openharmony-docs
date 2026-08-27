# DataPanelOptions

数据面板选项。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## max

```TypeScript
max?: number
```

- max大于0时，表示数据的最大值。  
- max小于等于0时，max等于values数据值列表各项的和，按比例显示。  
不传入时默认值：100。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: DataPanelType
```

数据面板的类型（不支持动态修改）。可选值：DataPanelType.Line（线性数据面板，适合在有限空间内展示多段数据对比）、DataPanelType.Circle（环形数据面板，适合直观展示数据占比关系）。不传入时默认值为DataPanelType.Circle。

**类型：** [DataPanelType](arkts-arkui-datapaneltype-e.md)

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## values

```TypeScript
values: number[]
```

数据值列表，数组长度范围[0, 9]，大于9个数据则取前9个数据。若数据值小于0则置为0。

**类型：** number[]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
