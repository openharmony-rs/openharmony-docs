# DataPanelConfiguration

开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。

**继承/实现关系：** DataPanelConfiguration extends [CommonConfiguration<DataPanelConfiguration>](CommonConfiguration<DataPanelConfiguration>)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxValue

```TypeScript
maxValue: number
```

DataPanel显示的最大值。

默认值：100。

**说明：**

如果小于或等于0，maxValue将被设为values数组中所有项的总和，并按比例显示。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## values

```TypeScript
values: number[]
```

当前DataPanel的数据值。

数组长度范围是[0, 9]。

**说明：**

如果数组长度大于9，则取前9项。

**类型：** number[]

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

