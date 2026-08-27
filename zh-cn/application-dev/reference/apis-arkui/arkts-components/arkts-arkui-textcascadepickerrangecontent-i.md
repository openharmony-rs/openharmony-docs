# TextCascadePickerRangeContent

多列联动数据选择器的数据选项内容。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## children

```TypeScript
children?: TextCascadePickerRangeContent[]
```

联动数据。表示当前数据项的子选项数组，用于构建多列联动数据选择器的层级结构。 数组的每个元素为[TextCascadePickerRangeContent](#textcascadepickerrangecontent)类型，包含text和children属性，支持多 级嵌套。当选择器支持多级联动时传入此参数；不传入时表示该选项没有子级数据。

**类型：** [TextCascadePickerRangeContent](arkts-arkui-textcascadepickerrangecontent-i.md)[]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: string | Resource
```

文本信息。

> **说明：**当文本长度大于列宽时，文本被截断。

**类型：** string \| Resource

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
