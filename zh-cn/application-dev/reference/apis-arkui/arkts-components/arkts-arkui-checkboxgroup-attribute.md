# CheckboxGroup属性/事件

除支持通用属性外，还支持以下属性：除支持通用事件外，还支持以下事件：

**继承/实现关系：** CheckboxGroupAttribute extends CommonMethod<CheckboxGroupAttribute>

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## checkboxShape

```TypeScript
checkboxShape(value: CheckBoxShape)
```

设置CheckboxGroup组件形状，包括圆形和圆角方形。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CheckBoxShape](../arkts-apis/arkts-arkui-checkboxshape-e.md) | 是 | 设置CheckboxGroup组件形状，包括圆形和圆角方形。默认值：CheckBoxShape.CIRCLE    **说明：**CheckboxGroup组件将按照设置的形状显示。CheckboxGroup内所有未单独设置shape类型的Checkbox，其形状将与CheckboxGroup保持一致。CheckboxGroup内 已单独设置shape类型的Checkbox，其形状将优先于CheckboxGroup的设置，按照自身设置显示。 |

## checkboxShape

```TypeScript
checkboxShape(shape: Optional<CheckBoxShape>)
```

设置CheckboxGroup组件形状，包括圆形和圆角方形。与[checkboxShape](#checkboxshape)&lt;sup&gt;12+&lt;/sup&gt;相比，shape参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shape | [Optional](arkts-arkui-optional-t.md)&lt;[CheckBoxShape](../arkts-apis/arkts-arkui-checkboxshape-e.md)&gt; | 是 | 设置CheckboxGroup组件形状，包括圆形和圆角方形。当shape的值为undefined时，默认值为 CheckBoxShape.CIRCLE。   **说明：**CheckboxGroup组件将按照设置的形状显示。CheckboxGroup内所有未单独设置shape类型的Checkbox，其形状 将与CheckboxGroup保持一致。CheckboxGroup内已单独设置shape类型的Checkbox，其形状将优先于CheckboxGroup的设置，按照自身设置显示。 |

## contentModifier

```TypeScript
contentModifier(modifier: Optional<ContentModifier<CheckBoxGroupConfiguration>>)
```

定制CheckboxGroup内容区的方法。设置该属性时，其他属性设置会失效。

> **说明：**
> 
> 该接口不支持在attributeModifier中调用。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-optional-t.md)&lt;[ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;[CheckBoxGroupConfiguration](arkts-arkui-checkboxgroupconfiguration-i.md)&gt;&gt; | 是 | 在CheckboxGroup组件上，定制内容区的方法。modifier：内容修改器，开发者需要自定义类以实现ContentModifier接口。当modifier的值为undefined时，不使用内容修改器。 |

## mark

```TypeScript
mark(value: MarkStyle)
```

设置多选框内部图标样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [MarkStyle](../arkts-apis/arkts-arkui-markstyle-i.md) | 是 | 多选框内部图标样式。异常值按照默认值处理。 |

## mark

```TypeScript
mark(style: Optional<MarkStyle>)
```

设置多选框内部图标样式。与[mark](#mark)&lt;sup&gt;10+&lt;/sup&gt;相比，style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;[MarkStyle](../arkts-apis/arkts-arkui-markstyle-i.md)&gt; | 是 | 多选框内部图标样式。当style的值为undefined时，维持上次取值。 |

## onChange

```TypeScript
onChange(callback: OnCheckboxGroupChangeCallback)
```

CheckboxGroup的选中状态或群组内的Checkbox的选中状态发生变化时，触发回调。在与带有缓存功能的组件（如List）配合使用时，需注意未创建的Checkbox的选中状态对回调结果的影响。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnCheckboxGroupChangeCallback](arkts-arkui-oncheckboxgroupchangecallback-t.md) | 是 | 多选框群组的信息。<br>**起始版本：** 18 |

## onChange

```TypeScript
onChange(callback: Optional<OnCheckboxGroupChangeCallback>)
```

CheckboxGroup的选中状态或群组内的Checkbox的选中状态发生变化时，触发回调。与 [onChange](#onchange)相比，callback参数新增了对 undefined类型的支持。在与带有缓存功能的组件（如List）配合使用时，需注意未创建的Checkbox的选中状态对回调结果的影响。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;[OnCheckboxGroupChangeCallback](arkts-arkui-oncheckboxgroupchangecallback-t.md)&gt; | 是 | 多选框群组的信息。当callback的值为undefined时，不使用回调函数。 |

## selectAll

```TypeScript
selectAll(value: boolean)
```

设置是否全选。若同组的Checkbox显式设置了select属性，则Checkbox的优先级高。在与带有缓存功能的组件（如List）配合使用时，未创建的Checkbox选中状态需由开发者控制。从API version 10开始，该属性支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。从API version 18开始，该属性支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否全选。默认值：false值为true时，多选框群组将全部被选中；值为false时，多选框群组将全部取消选中。 |

## selectAll

```TypeScript
selectAll(isAllSelected: Optional<boolean>)
```

设置是否全选。若同组的Checkbox显式设置了select属性，则Checkbox的优先级高。与 [selectAll](#selectall)相比，isAllSelected参数新增了对undefined类型的支持。在与带有缓存功能的组件（如List）配合使用时，未创建的Checkbox选中状态需由开发者控制。该属性支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)、 [!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isAllSelected | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否全选。当isAllSelected的值为undefined时取默认值false。值为true时，多选框群组将全部被选 中；值为false时，多选框群组将全部取消选中。 |

## selectedColor

```TypeScript
selectedColor(value: ResourceColor)
```

设置被选中或部分选中状态的颜色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 被选中或部分选中状态的颜色。默认值：\\$r('sys.color.ohos_id_color_text_primary_activated')异常 值按照默认值处理。 |

## selectedColor

```TypeScript
selectedColor(resColor: Optional<ResourceColor>)
```

设置被选中或部分选中状态的颜色。与[selectedColor](#selectedcolor)相比，resColor参数新增了对 undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | 是 | 被选中或部分选中状态的颜色。当resColor的值为undefined时，默认值：\\$r('sys.color.ohos_id_color_text_primary_activated')异常值按照默认值处理。 |

## unselectedColor

```TypeScript
unselectedColor(value: ResourceColor)
```

设置非选中状态边框颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 非选中状态边框颜色。默认值：\\$r('sys.color.ohos_id_color_switch_outline_off')。 |

## unselectedColor

```TypeScript
unselectedColor(resColor: Optional<ResourceColor>)
```

设置非选中状态边框颜色。与[unselectedColor](#unselectedcolor)&lt;sup&gt;10+&lt;/sup&gt;相比， resColor参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | 是 | 非选中状态边框颜色。当resColor的值为undefined时，默认值：\\$r('sys.color.ohos_id_color_switch_outline_off')。 |
