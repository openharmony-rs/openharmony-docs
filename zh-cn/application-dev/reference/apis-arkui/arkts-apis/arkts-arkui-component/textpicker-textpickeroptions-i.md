# TextPickerOptions

文本选择器的参数说明。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface TextPickerOptions--><!--Device-unnamed-export declare interface TextPickerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## columnWidths

```TypeScript
columnWidths?: LengthMetrics[]
```

设置每一列的列宽。 默认值：每一列的列宽相等，为组件宽度除以列数。 **说明**： 1. 当文本长度大于列宽时，文本被截断。 2. 当设置为异常值时，使用默认值。 3. 支持设置为Undefined和Null，不支持Undefined[]和Null[]。

**类型：** LengthMetrics[]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextPickerOptions-columnWidths?: LengthMetrics[]--><!--Device-TextPickerOptions-columnWidths?: LengthMetrics[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## range

```TypeScript
range: string[] | string[][] | Resource | TextPickerRangeContent[] | TextCascadePickerRangeContent[]
```

选择器的数据选择列表。不可设置为空数组，若设置为空数组，则不显示；若动态变化为空数组，则保持当前正常值显示。 **说明**： 1. 单列数据选择器使用string[]，[Resource]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_， [TextPickerRangeContent]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_[]类型。 2. 多列非联动数据选择器使用string[][]类型。 3. 多列联动数据选择器使用[TextCascadePickerRangeContent]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_[]类型。 4. Resource类型只支持\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 5. range的类型及列数不可以动态修改。

**类型：** string[] \| string[][] \| Resource \| TextPickerRangeContent[] \| TextCascadePickerRangeContent[]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextPickerOptions-range: string[] | string[][] | Resource | TextPickerRangeContent[] | TextCascadePickerRangeContent[]--><!--Device-TextPickerOptions-range: string[] | string[][] | Resource | TextPickerRangeContent[] | TextCascadePickerRangeContent[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: int | int[] | Bindable<int> | Bindable<int[]>
```

设置选中项在数据选择列表中的索引值，索引从0开始。 默认值：0 **说明**： 1. 单列数据选择器使用int类型。 2. 多列数据选择器使用int[]类型。 3. 从API version 23开始，该参数支持\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_双向绑定变量。

**类型：** int \| int[] \| Bindable&lt;int&gt; \| Bindable&lt;int[]&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextPickerOptions-selected?: int | int[] | Bindable<int> | Bindable<int[]>--><!--Device-TextPickerOptions-selected?: int | int[] | Bindable<int> | Bindable<int[]>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: BindableResourceStr | BindableResourceStrArray
```

设置选中项的值，优先级低于selected。 默认值：数据选择列表中第一个元素的值。 **说明**： 1. 从API version 23开始，该参数支持\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_双向绑定变量。 2. 只有显示文本列表时该值有效。显示图片或图文混排的列表时，该值无效。 3. 单列数据选择器使用[ResourceStr]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_类型。 4. 多列数据选择器使用[ResourceStr]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_[]类型。

**类型：** BindableResourceStr \| BindableResourceStrArray

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextPickerOptions-value?: BindableResourceStr | BindableResourceStrArray--><!--Device-TextPickerOptions-value?: BindableResourceStr | BindableResourceStrArray-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

