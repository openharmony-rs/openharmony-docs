# Progress属性/事件

```TypeScript
declare class ProgressAttribute<Type extends keyof ProgressStyleMap = keyof ProgressStyleMap,
  Style extends ProgressStyleMap[Type] = ProgressStyleMap[Type]> extends CommonMethod<ProgressAttribute<Type>>
```

除支持[通用属性](arkts-arkui-common-comp.md#common)外，还支持以下属性：

> **说明：** 
> 
> 该组件重写了通用属性[backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor)，直接添加在Progress组件上，设置进度条的底色。如需设
> 置整个Progress组件的背景色，需要在外层容器上添加backgroundColor，并用该容器包裹Progress组件。

**继承/实现关系：** ProgressAttribute extends CommonMethod<ProgressAttribute<Type>>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color(value: ResourceColor | LinearGradient)
```

设置进度条前景色。

从API version 10开始支持利用LinearGradient设置Ring样式的渐变色。Ring类型不建议设置透明度，如需设置透明度，建议使用[DataPanel](arkts-arkui-datapanel-comp.md#data_panel)。

从API version 23开始支持利用LinearGradient设置Linear样式和Capsule样式的渐变色。API version 22及之前版本使用该方式设置时，会以默认主题色显示。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; LinearGradient | 是 | 进度条前景色。<br>从API version 10开始支持利用LinearGradient设置Ring样式的渐变色，从API version 23开始支持利用LinearGradient设置Linear样式和Capsule样式的渐变色。<br>默认值：<br>- Capsule：<br>   API version 9及以下：'#ff007dff'<br>   API version 10：'#33006cde'<br>   API version 11及以上：'#33007dff'<br>- Ring：<br>   API version 9及以下：'#ff007dff'<br>   API version 10及以上：起始端：'#ff86c1ff'，结束端：'#ff254ff7'<br>- 其他样式：'#ff007dff' |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<ProgressConfiguration>)
```

定制progress内容区的方法。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[ProgressConfiguration](arkts-arkui-progress-comp-progressconfiguration-i.md)&gt; | 是 | The contentModifier of progress. |

## privacySensitive

```TypeScript
privacySensitive(isPrivacySensitiveMode: Optional<boolean>)
```

设置隐私敏感。

> **说明：** 
> 
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isPrivacySensitiveMode | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | 是 | 设置隐私敏感，隐私模式下进度清零，文字将被遮罩。true：打开隐私敏感；false：关闭隐私敏感。<br> 默认值：false <br>**说明：** <br>设置null表示不敏感。<!--Del--> <br>需要在卡片中使用Progress，并用[FormComponent](arkts-arkui-formcomponent-comp-sys.md#form_component系统接口)组件设置[隐私遮罩](arkts-arkui-common-comp.md#common)属性，显示卡片时才有隐私遮罩效果。<!-- DelEnd--> |

## style

```TypeScript
style(value: Style)
```

设置组件的样式。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Style | 是 | 组件的样式。Style继承于[ProgressStyleMap](arkts-arkui-progress-comp-progressstylemap-i.md)。<br>**说明：** 不同的[ProgressType](arkts-arkui-progress-comp-progresstype-e.md)需分别对应相应的[style](#style)属性设置，详细映射关系参考[ProgressStyleMap](arkts-arkui-progress-comp-progressstylemap-i.md)。<br>- [CapsuleStyleOptions](arkts-arkui-progress-comp-capsulestyleoptions-i.md)：设置Capsule的样式。<br>- [RingStyleOptions](arkts-arkui-progress-comp-ringstyleoptions-i.md)：设置Ring的样式。<br>- [LinearStyleOptions](arkts-arkui-progress-comp-linearstyleoptions-i.md)：设置Linear的样式。<br>- [ScaleRingStyleOptions](arkts-arkui-progress-comp-scaleringstyleoptions-i.md)：设置ScaleRing的样式。<br>- [EclipseStyleOptions](arkts-arkui-progress-comp-eclipsestyleoptions-i.md)：设置Eclipse的样式。<br>- [ProgressStyleOptions](arkts-arkui-progress-comp-progressstyleoptions-i.md)：仅可设置各类型进度条的strokeWidth、scaleCount、scaleWidth，仅对支持这些样式设置的进度条生效。 |

## value

```TypeScript
value(value: number)
```

设置当前进度值。设置小于0的数值时置为0，设置大于total的数值时置为total。设置非法值时按默认值处理。当Ring样式的status属性设置为ProgressStatus.LOADING时，设置进度值不生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 当前进度值。<br>默认值：0 <br>取值范围：[0, total]，设置小于0的数值时置为0，设置大于total的数值时置为total，设置非法值时按默认值处理。<br>**说明：** 当Ring类型进度条的status设置为ProgressStatus.LOADING时，设置进度值不生效。 |
