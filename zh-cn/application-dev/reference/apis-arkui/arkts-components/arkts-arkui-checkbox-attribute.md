# Checkbox属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件：

**继承/实现关系：** CheckboxAttribute extends [CommonMethod<CheckboxAttribute>]

**起始版本：** 8

<!--Device-unnamed-declare class CheckboxAttribute extends CommonMethod<CheckboxAttribute>--><!--Device-unnamed-declare class CheckboxAttribute extends CommonMethod<CheckboxAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<CheckBoxConfiguration>)
```

定制Checkbox内容区的方法。设置该属性时，会导致其他属性设置失效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CheckboxAttribute-contentModifier(modifier: ContentModifier<CheckBoxConfiguration>): CheckboxAttribute--><!--Device-CheckboxAttribute-contentModifier(modifier: ContentModifier<CheckBoxConfiguration>): CheckboxAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;CheckBoxConfiguration&gt; | 是 | 在Checkbox组件上，定制内容区的方法。<br/>modifier：内容修改器，开发者需要自定义class实现ContentModifier接口。 |

## contentModifier

```TypeScript
contentModifier(modifier: Optional<ContentModifier<CheckBoxConfiguration>>)
```

定制Checkbox内容区的方法。与[contentModifier](CheckboxAttribute#contentModifier(modifier: ContentModifier<CheckBoxConfiguration>))<sup>12+</sup>相比，modifier参数新增了对undefined类型的支持。设置该属性时，会导致其他属性设置失效。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CheckboxAttribute-contentModifier(modifier: Optional<ContentModifier<CheckBoxConfiguration>>): CheckboxAttribute--><!--Device-CheckboxAttribute-contentModifier(modifier: Optional<ContentModifier<CheckBoxConfiguration>>): CheckboxAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-optional-t.md)&lt;ContentModifier&lt;CheckBoxConfiguration&gt;&gt; | 是 | 在Checkbox组件上，定制内容区的方法。<br/>modifier：内容修改器，开发者需要自定义class实现ContentModifier接口。<br/>当modifier的值为undefined时，不使用内容修改器。 |

## mark

```TypeScript
mark(value: MarkStyle)
```

设置多选框内部图标的样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CheckboxAttribute-mark(value: MarkStyle): CheckboxAttribute--><!--Device-CheckboxAttribute-mark(value: MarkStyle): CheckboxAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [MarkStyle](../arkts-apis/arkts-arkui-markstyle-i.md) | 是 | 多选框内部图标样式。 从API version 12开始，设置了indicatorBuilder时，按照indicatorBuilder中的内容显示。<br/>默认值：{<br/>strokeColor : `$r('sys.color.ohos_id_color_foreground_contrary')`,<br/>strokeWidth:`$r('sys.float.ohos_id_checkbox_stroke_width')`,<br/>size: '20vp'<br/>} |

## mark

```TypeScript
mark(style: Optional<MarkStyle>)
```

设置多选框内部图标的样式。与[mark](CheckboxAttribute#mark(value: MarkStyle))<sup>10+</sup>相比，style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CheckboxAttribute-mark(style: Optional<MarkStyle>): CheckboxAttribute--><!--Device-CheckboxAttribute-mark(style: Optional<MarkStyle>): CheckboxAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;MarkStyle&gt; | 是 | 多选框内部图标样式。 设置了indicatorBuilder时，按照indicatorBuilder中的内容显示。<br/>当style的值为undefined时，默认值：{<br/>strokeColor : `$r('sys.color.ohos_id_color_foreground_contrary')`,<br/>strokeWidth:`$r('sys.float.ohos_id_checkbox_stroke_width')`,<br/>size: '20vp'<br/>} |

## onChange

```TypeScript
onChange(callback: OnCheckboxChangeCallback)
```

当选中状态发生变化时，触发该回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CheckboxAttribute-onChange(callback: OnCheckboxChangeCallback): CheckboxAttribute--><!--Device-CheckboxAttribute-onChange(callback: OnCheckboxChangeCallback): CheckboxAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnCheckboxChangeCallback](arkts-arkui-oncheckboxchangecallback-t.md) | 是 | 返回选中的状态。<br>**起始版本：** 18 |

## onChange

```TypeScript
onChange(callback: Optional<OnCheckboxChangeCallback>)
```

当选中状态发生变化时，触发该回调。与[onChange](CheckboxAttribute#onChange(callback: OnCheckboxChangeCallback))相比，callback参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CheckboxAttribute-onChange(callback: Optional<OnCheckboxChangeCallback>): CheckboxAttribute--><!--Device-CheckboxAttribute-onChange(callback: Optional<OnCheckboxChangeCallback>): CheckboxAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;OnCheckboxChangeCallback&gt; | 是 | 返回选中的状态。<br/>当callback的值为undefined时，不使用回调函数。 |

## select

```TypeScript
select(value: boolean)
```

设置多选框选中状态。

从API version 10开始，该属性支持[$$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。

从API version 18开始，该属性支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CheckboxAttribute-select(value: boolean): CheckboxAttribute--><!--Device-CheckboxAttribute-select(value: boolean): CheckboxAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 多选框是否选中。<br/>默认值：false<br/>值为true时，多选框被选中。值为false时，多选框未选中。 |

## select

```TypeScript
select(isSelected: Optional<boolean>)
```

设置多选框选中状态。与[select](CheckboxAttribute#select(value: boolean))相比，isSelected参数新增了对undefined类型的支持。

该属性支持[$$](../../../ui/state-management/arkts-two-way-sync.md)、[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CheckboxAttribute-select(isSelected: Optional<boolean>): CheckboxAttribute--><!--Device-CheckboxAttribute-select(isSelected: Optional<boolean>): CheckboxAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isSelected | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 多选框是否选中。<br/>当isSelected的值为undefined时取默认值false。<br/>值为true时，多选框被选中。值为false时，多选框未选中。 |

## selectedColor

```TypeScript
selectedColor(value: ResourceColor)
```

设置多选框选中状态颜色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CheckboxAttribute-selectedColor(value: ResourceColor): CheckboxAttribute--><!--Device-CheckboxAttribute-selectedColor(value: ResourceColor): CheckboxAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 多选框选中状态颜色。<br/>默认值：$r('sys.color.ohos_id_color_text_primary_activated')<br/>异常值按照默认值处理。 |

## selectedColor

```TypeScript
selectedColor(resColor: Optional<ResourceColor>)
```

设置多选框选中状态颜色。与[selectedColor](CheckboxAttribute#selectedColor(value: ResourceColor))相比，resColor参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CheckboxAttribute-selectedColor(resColor: Optional<ResourceColor>): CheckboxAttribute--><!--Device-CheckboxAttribute-selectedColor(resColor: Optional<ResourceColor>): CheckboxAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-optional-t.md)&lt;ResourceColor&gt; | 是 | 多选框选中状态颜色。<br/>当resColor的值为undefined时取默认值$r('sys.color.ohos_id_color_text_primary_activated')。<br/>异常值按照默认值处理。 |

## shape

```TypeScript
shape(value: CheckBoxShape)
```

设置Checkbox组件形状，包括圆形和圆角方形。如果想要调整当前Checkbox的样式，需使用[contentModifier](CheckboxAttribute#contentModifier(modifier: ContentModifier<CheckBoxConfiguration>))属性自定义Checkbox样式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CheckboxAttribute-shape(value: CheckBoxShape): CheckboxAttribute--><!--Device-CheckboxAttribute-shape(value: CheckBoxShape): CheckboxAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CheckBoxShape](../arkts-apis/arkts-arkui-checkboxshape-e.md) | 是 | Checkbox组件形状，包括圆形和圆角方形。<br/>默认值：CheckBoxShape.CIRCLE |

## shape

```TypeScript
shape(shape: Optional<CheckBoxShape>)
```

设置Checkbox组件形状，包括圆形和圆角方形。与[shape](CheckboxAttribute#shape(value: CheckBoxShape))<sup>11+</sup>相比，shape参数新增了对undefined类型的支持。如果想要调整当前Checkbox的样式，需使用[contentModifier](CheckboxAttribute#contentModifier(modifier: ContentModifier<CheckBoxConfiguration>))属性自定义Checkbox样式。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CheckboxAttribute-shape(shape: Optional<CheckBoxShape>): CheckboxAttribute--><!--Device-CheckboxAttribute-shape(shape: Optional<CheckBoxShape>): CheckboxAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shape | [Optional](arkts-arkui-optional-t.md)&lt;CheckBoxShape&gt; | 是 | Checkbox组件形状，包括圆形和圆角方形。<br/>当shape的值为undefined时，默认值为CheckBoxShape.CIRCLE。 |

## unselectedColor

```TypeScript
unselectedColor(value: ResourceColor)
```

设置多选框非选中状态的边框颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CheckboxAttribute-unselectedColor(value: ResourceColor): CheckboxAttribute--><!--Device-CheckboxAttribute-unselectedColor(value: ResourceColor): CheckboxAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 多选框非选中状态边框颜色。<br/>默认值：$r('sys.color.ohos_id_color_switch_outline_off') |

## unselectedColor

```TypeScript
unselectedColor(resColor: Optional<ResourceColor>)
```

设置多选框非选中状态的边框颜色。与[unselectedColor](CheckboxAttribute#unselectedColor(value: ResourceColor))<sup>10+</sup>相比，resColor参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CheckboxAttribute-unselectedColor(resColor: Optional<ResourceColor>): CheckboxAttribute--><!--Device-CheckboxAttribute-unselectedColor(resColor: Optional<ResourceColor>): CheckboxAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-optional-t.md)&lt;ResourceColor&gt; | 是 | 多选框非选中状态边框颜色。<br/>当resColor的值为undefined时取默认值$r('sys.color.ohos_id_color_switch_outline_off') |

