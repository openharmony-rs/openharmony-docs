# CheckboxOptions

多选框的信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface CheckboxOptions--><!--Device-unnamed-export declare interface CheckboxOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## group

```TypeScript
group?: string
```

用于指定多选框所属群组的名称（即所属CheckboxGroup的名称）。 默认值：undefined，默认状态下配合CheckboxGroupOptions属性group信息为undefined的节点使用。 **说明：** 未配合使用CheckboxGroup组件时，此值无用。 **卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CheckboxOptions-group?: string--><!--Device-CheckboxOptions-group?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## indicatorBuilder

```TypeScript
indicatorBuilder?: CustomBuilder
```

配置多选框的选中样式为自定义组件。自定义组件与Checkbox组件为中心点对齐显示。indicatorBuilder设置为undefined/null时，默认为indicatorBuilder未设置状态。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** CustomBuilder

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CheckboxOptions-indicatorBuilder?: CustomBuilder--><!--Device-CheckboxOptions-indicatorBuilder?: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name?: string
```

指定多选框名称。 默认值：undefined，取值为undefined无效果。 **卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CheckboxOptions-name?: string--><!--Device-CheckboxOptions-name?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

