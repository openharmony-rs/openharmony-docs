# Radio属性/事件

除支持通用属性外，还支持以下属性：除支持通用事件外，还支持以下事件：

**继承/实现关系：** RadioAttribute extends CommonMethod<RadioAttribute>

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## checked

```TypeScript
checked(value: boolean)
```

设置单选框的选中状态。从API version 10开始，该属性支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。从API version 18开始，该属性支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 单选框的选中状态。默认值：false值为true时，单选框被选中。值为false时，单选框不被选中。 |

## checked

```TypeScript
checked(isChecked: Optional<boolean>)
```

设置单选框的选中状态。与[checked](#checked)相比，isChecked参数新增了对undefined类型的支持。该属性支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)、 [!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isChecked | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 单选框的选中状态。当isChecked的值为undefined时取默认值false。值为true时，单选框被选中。值为false 时，单选框不被选中。 |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<RadioConfiguration>)
```

定制Radio内容区的方法。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;[RadioConfiguration](arkts-arkui-radioconfiguration-i.md)&gt; | 是 | 在Radio组件上，定制内容区的方法。modifier：内容修改器，开发者需要自定义class实现 ContentModifier接口。 |

## contentModifier

```TypeScript
contentModifier(modifier: Optional<ContentModifier<RadioConfiguration>>)
```

定制Radio内容区的方法。与 [contentModifier](#contentmodifier)&lt;sup&gt;12+&lt;/sup &gt;相比，modifier参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-optional-t.md)&lt;[ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;[RadioConfiguration](arkts-arkui-radioconfiguration-i.md)&gt;&gt; | 是 | 在Radio组件上，定制内容区的方法。modifier：内容修改器，开发者需要自定义 class实现ContentModifier接口。当modifier的值为undefined时，不使用内容修改器。 |

## onChange

```TypeScript
onChange(callback: (isChecked: boolean) => void)
```

单选框选中状态改变时触发的回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (isChecked: boolean) = & gt; void | 是 | 单选框选中状态改变时触发该回调。值为true时，表示从未选中变为选中。值为false时，表示从选中变为未选中。 |

## onChange

```TypeScript
onChange(callback: Optional<OnRadioChangeCallback>)
```

单选框选中状态改变时触发的回调。与onChange相比，callback参数新增了对 undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;[OnRadioChangeCallback](arkts-arkui-onradiochangecallback-t.md)&gt; | 是 | 单选框选中状态改变时触发该回调。当callback的值为undefined时，不使用回调函数。 |

## radioStyle

```TypeScript
radioStyle(value?: RadioStyle)
```

设置单选框选中状态和非选中状态的样式。从API version 10开始，该接口支持在ArkTS组件中使用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RadioStyle](arkts-arkui-radiostyle-i.md) | 否 | 单选框选中状态和非选中状态的样式。 未设置时，则按照RadioStyle中各参数的默认值配置。 |
