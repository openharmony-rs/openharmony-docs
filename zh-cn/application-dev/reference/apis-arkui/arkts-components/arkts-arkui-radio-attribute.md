# Radio属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件：

**继承/实现关系：** RadioAttribute extends [CommonMethod<RadioAttribute>](CommonMethod<RadioAttribute>)

**起始版本：** 8

<!--Device-unnamed-declare class RadioAttribute extends CommonMethod<RadioAttribute>--><!--Device-unnamed-declare class RadioAttribute extends CommonMethod<RadioAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="checked"></a>
## checked

```TypeScript
checked(value: boolean)
```

设置单选框的选中状态。

从API version 10开始，该属性支持[$$](docroot://ui/state-management/arkts-two-way-sync.md)双向绑定变量。

从API version 18开始，该属性支持[!!](docroot://ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RadioAttribute-checked(value: boolean): RadioAttribute--><!--Device-RadioAttribute-checked(value: boolean): RadioAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 单选框的选中状态。<br/>默认值：false<br/>值为true时，单选框被选中。值为false时，单选框不被选中。 |

<a id="checked-1"></a>
## checked

```TypeScript
checked(isChecked: Optional<boolean>)
```

设置单选框的选中状态。与[checked](RadioAttribute#checked(value: boolean))相比，isChecked参数新增了对undefined类型的支持。

该属性支持[$$](docroot://ui/state-management/arkts-two-way-sync.md)、[!!](docroot://ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-RadioAttribute-checked(isChecked: Optional<boolean>): RadioAttribute--><!--Device-RadioAttribute-checked(isChecked: Optional<boolean>): RadioAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isChecked | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 单选框的选中状态。<br/>当isChecked的值为undefined时取默认值false。<br/>值为true时，单选框被选中。值为false时，单选框不被选中。 |

<a id="contentmodifier"></a>
## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<RadioConfiguration>)
```

定制Radio内容区的方法。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RadioAttribute-contentModifier(modifier: ContentModifier<RadioConfiguration>): RadioAttribute--><!--Device-RadioAttribute-contentModifier(modifier: ContentModifier<RadioConfiguration>): RadioAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;RadioConfiguration&gt; | 是 | 在Radio组件上，定制内容区的方法。<br/>modifier：内容修改器，开发者需要自定义class实现ContentModifier接口。 |

<a id="contentmodifier-1"></a>
## contentModifier

```TypeScript
contentModifier(modifier: Optional<ContentModifier<RadioConfiguration>>)
```

定制Radio内容区的方法。与[contentModifier](RadioAttribute#contentModifier(modifier: ContentModifier<RadioConfiguration>))<sup>12+</sup  
>相比，modifier参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-RadioAttribute-contentModifier(modifier: Optional<ContentModifier<RadioConfiguration>>): RadioAttribute--><!--Device-RadioAttribute-contentModifier(modifier: Optional<ContentModifier<RadioConfiguration>>): RadioAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-optional-t.md)&lt;ContentModifier&lt;RadioConfiguration&gt;&gt; | 是 | 在Radio组件上，定制内容区的方法。<br/>modifier：内容修改器，开发者需要自定义class实现ContentModifier接口。<br/>当modifier的值为undefined时，不使用内容修改器。 |

<a id="onchange"></a>
## onChange

```TypeScript
onChange(callback: (isChecked: boolean) => void)
```

单选框选中状态改变时触发的回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RadioAttribute-onChange(callback: (isChecked: boolean) => void): RadioAttribute--><!--Device-RadioAttribute-onChange(callback: (isChecked: boolean) => void): RadioAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (isChecked: boolean) =&gt; void | 是 | 单选框选中状态改变时触发该回调。<br/>值为true时，表示从未选中变为选中。值为false时，表示从选中变为未选中。 |

<a id="onchange-1"></a>
## onChange

```TypeScript
onChange(callback: Optional<OnRadioChangeCallback>)
```

单选框选中状态改变时触发的回调。与[onChange](RadioAttribute#onChange(callback: (isChecked: boolean) => void))相比，callback参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-RadioAttribute-onChange(callback: Optional<OnRadioChangeCallback>): RadioAttribute--><!--Device-RadioAttribute-onChange(callback: Optional<OnRadioChangeCallback>): RadioAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;OnRadioChangeCallback&gt; | 是 | 单选框选中状态改变时触发该回调。<br/>当callback的值为undefined时，不使用回调函数。 |

<a id="radiostyle"></a>
## radioStyle

```TypeScript
radioStyle(value?: RadioStyle)
```

设置单选框选中状态和非选中状态的样式。

从API version 10开始，该接口支持在ArkTS组件中使用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RadioAttribute-radioStyle(value?: RadioStyle): RadioAttribute--><!--Device-RadioAttribute-radioStyle(value?: RadioStyle): RadioAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RadioStyle](arkts-arkui-radiostyle-i.md) | 否 | 单选框选中状态和非选中状态的样式。 <br/> 未设置时，则按照RadioStyle中各参数的默认值配置。 |

