# DataPanelConfiguration

开发者需要自定义class实现ContentModifier接口。继承自CommonConfiguration。

**继承/实现关系：** DataPanelConfiguration extends CommonConfiguration<DataPanelConfiguration>

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface DataPanelConfiguration--><!--Device-unnamed-export declare interface DataPanelConfiguration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxValue

```TypeScript
maxValue: double
```

DataPanel显示的最大值。 默认值：100。 **说明：** 如果小于或等于0，maxValue将被设为values数组中所有项的总和，并按比例显示。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataPanelConfiguration-maxValue: double--><!--Device-DataPanelConfiguration-maxValue: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## values

```TypeScript
values: double[]
```

数据值列表，最多包含9个数据，大于9个数据则取前9个数据。若数据值小于0则置为0。

**类型：** double[]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataPanelConfiguration-values: double[]--><!--Device-DataPanelConfiguration-values: double[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

