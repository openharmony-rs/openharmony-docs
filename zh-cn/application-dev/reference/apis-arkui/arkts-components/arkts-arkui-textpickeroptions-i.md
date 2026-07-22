# TextPickerOptions

文本选择器的参数说明。

**起始版本：** 8

<!--Device-unnamed-declare interface TextPickerOptions--><!--Device-unnamed-declare interface TextPickerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## columnWidths

```TypeScript
columnWidths?: LengthMetrics[]
```

设置每一列的列宽。

默认值：每一列的列宽相等，为组件宽度除以列数。

**说明**：

1. 当文本长度大于列宽时，文本被截断。2. 当设置为异常值时，使用默认值。3. 支持设置为Undefined和Null，不支持Undefined[]和Null[]。

**类型：** LengthMetrics[]

**默认值：** Each column has equal width, calculated by dividing the total component width by the number of columns.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerOptions-columnWidths?: LengthMetrics[]--><!--Device-TextPickerOptions-columnWidths?: LengthMetrics[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## range

```TypeScript
range: string[] | string[][] | Resource | TextPickerRangeContent[] | TextCascadePickerRangeContent[]
```

选择器的数据选择列表。不可设置为空数组，若设置为空数组，则不显示；若动态变化为空数组，则保持当前正常值显示。

**说明**：

1. 单列数据选择器使用string[]，[Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)，[TextPickerRangeContent](arkts-arkui-textpickerrangecontent-i.md)[]类型。2. 多列非联动数据选择器使用string[][]类型。3. 多列联动数据选择器使用[TextCascadePickerRangeContent](arkts-arkui-textcascadepickerrangecontent-i.md)[]类型。4. Resource类型只支持[strarray.json](../../../quick-start/resource-categories-and-access.md#资源组目录)。5. range的类型及列数不可以动态修改。

**类型：** string[] \| string[][] \| Resource \| TextPickerRangeContent[] \| TextCascadePickerRangeContent[]

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerOptions-range: string[] | string[][] | Resource | TextPickerRangeContent[] | TextCascadePickerRangeContent[]--><!--Device-TextPickerOptions-range: string[] | string[][] | Resource | TextPickerRangeContent[] | TextCascadePickerRangeContent[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: number | number[]
```

设置选中项在数据选择列表中的索引值，索引从0开始。

默认值：0

**说明**：

1. 单列数据选择器使用number类型。2. 多列数据选择器使用number[]类型。3. 从API version 10开始，该参数支持[$$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。

**类型：** number \| number[]

**默认值：** 0

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerOptions-selected?: number | number[]--><!--Device-TextPickerOptions-selected?: number | number[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: ResourceStr | ResourceStr[]
```

设置选中项的值，优先级低于selected。

默认值：数据选择列表中第一个元素的值。

**说明**：

1. 从API version 10开始，该参数支持[$$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。2. 从API version 20开始，支持[Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)类型。3. 只有显示文本列表时该值有效。显示图片或图文混排的列表时，该值无效。4. 单列数据选择器使用[ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)类型。5. 多列数据选择器使用[ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)[]类型。

**类型：** ResourceStr \| ResourceStr[]

**默认值：** value of the first item [since 8 - 9]

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerOptions-value?: ResourceStr | ResourceStr[]--><!--Device-TextPickerOptions-value?: ResourceStr | ResourceStr[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

