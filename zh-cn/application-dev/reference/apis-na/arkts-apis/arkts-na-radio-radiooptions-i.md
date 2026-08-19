# RadioOptions

单选框的信息。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface RadioOptions--><!--Device-unnamed-export declare interface RadioOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## group

```TypeScript
group: string
```

当前单选框的所属群组名称，相同group的Radio只能有一个被选中。 **卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RadioOptions-group: string--><!--Device-RadioOptions-group: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## indicatorBuilder

```TypeScript
indicatorBuilder?: CustomBuilder
```

配置单选框的选中样式为自定义组件。自定义组件与Radio组件为中心点对齐显示。indicatorBuilder设置为undefined时，按照RadioIndicatorType.TICK进行显示。 **卡片能力（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** CustomBuilder

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RadioOptions-indicatorBuilder?: CustomBuilder--><!--Device-RadioOptions-indicatorBuilder?: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## indicatorType

```TypeScript
indicatorType?: RadioIndicatorType
```

配置单选框的选中样式。未设置时按照RadioIndicatorType.TICK进行显示。 **卡片能力（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [RadioIndicatorType](arkts-na-radio-radioindicatortype-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RadioOptions-indicatorType?: RadioIndicatorType--><!--Device-RadioOptions-indicatorType?: RadioIndicatorType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: string
```

当前单选框的值。 **卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RadioOptions-value: string--><!--Device-RadioOptions-value: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

