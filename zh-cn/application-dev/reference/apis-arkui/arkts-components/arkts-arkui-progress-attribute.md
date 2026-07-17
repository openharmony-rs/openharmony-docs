# Progress属性/事件

除支持[通用属性](../../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md)外，还支持以下属性。

支持[通用事件](../../../../reference/apis-arkui/arkui-ts/ts-component-general-events.md)。

**继承/实现关系：** ProgressAttribute extends [CommonMethod<ProgressAttribute<Type>>](CommonMethod<ProgressAttribute<Type>>)

**起始版本：** 7

<!--Device-unnamed-declare class ProgressAttribute<Type extends keyof ProgressStyleMap = keyof ProgressStyleMap,  Style extends ProgressStyleMap[Type] = ProgressStyleMap[Type]> extends CommonMethod<ProgressAttribute<Type>>--><!--Device-unnamed-declare class ProgressAttribute<Type extends keyof ProgressStyleMap = keyof ProgressStyleMap,  Style extends ProgressStyleMap[Type] = ProgressStyleMap[Type]> extends CommonMethod<ProgressAttribute<Type>>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color(value: ResourceColor | LinearGradient)
```

设置进度条前景色。

从API version 10开始支持利用[LinearGradient](arkts-arkui-common-lineargradient-i.md)设置Ring样式的渐变色。Ring类型不建议设置透明度，如需设置透明度，建议使用[DataPanel](arkts-arkui-datapanel.md)。

从API version 23开始支持利用[LinearGradient](arkts-arkui-common-lineargradient-i.md)设置Linear样式和Capsule样式的渐变色。API version 22及之前版本利用LinearGradient设置Linear样式和Capsule样式的渐变色时，会以默认主题色显示。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ProgressAttribute-color(value: ResourceColor | LinearGradient): ProgressAttribute<Type>--><!--Device-ProgressAttribute-color(value: ResourceColor | LinearGradient): ProgressAttribute<Type>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ResourceColor \| LinearGradient | 是 | 进度条前景色。<br/>默认值：<br/>- Capsule：<br/>   API version 9及以下：'#ff007dff'<br/>   API version 10：'#33006cde'<br/>   API version 11及以上：'#33007dff'<br/>- Ring：<br/>   API version 9及以下：'#ff007dff'<br/>   API version 10及以上：起始端：'#ff86c1ff'，结束端：'#ff254ff7'<br/>- 其他样式：'#ff007dff' |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<ProgressConfiguration>)
```

定制progress内容区的方法。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressAttribute-contentModifier(modifier: ContentModifier<ProgressConfiguration>): ProgressAttribute<Type>--><!--Device-ProgressAttribute-contentModifier(modifier: ContentModifier<ProgressConfiguration>): ProgressAttribute<Type>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-common-contentmodifier-i.md)<ProgressConfiguration> | 是 | The contentModifier of progress. |

## privacySensitive

```TypeScript
privacySensitive(isPrivacySensitiveMode: Optional<boolean>)
```

设置隐私敏感。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ProgressAttribute-privacySensitive(isPrivacySensitiveMode: Optional<boolean>): ProgressAttribute<Type>--><!--Device-ProgressAttribute-privacySensitive(isPrivacySensitiveMode: Optional<boolean>): ProgressAttribute<Type>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isPrivacySensitiveMode | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 设置隐私敏感，隐私模式下进度清零，文字将被遮罩。true：打开隐私敏感；false：关闭隐私敏感。<br/>。<br>默认值：false。 |

## style

```TypeScript
style(value: Style)
```

设置组件的样式。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ProgressAttribute-style(value: Style): ProgressAttribute<Type>--><!--Device-ProgressAttribute-style(value: Style): ProgressAttribute<Type>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Style | 是 | 组件的样式。<br/>- CapsuleStyleOptions：设置Capsule的样式。<br/>- RingStyleOptions：设置Ring的样式。<br/>-LinearStyleOptions：设置Linear的样式。<br/>- ScaleRingStyleOptions：设置ScaleRing的样式。<br/>- EclipseStyleOptions：设置Eclipse的样式。<br/>- ProgressStyleOptions：仅可设置各类型进度条的strokeWidth、scaleCount、scaleWidth，仅对支持这些样式设置的进度条生效。 |

## value

```TypeScript
value(value: number)
```

设置当前进度值。设置小于0的数值时置为0，设置大于total的数值时置为total。非法数值不生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ProgressAttribute-value(value: number): ProgressAttribute<Type>--><!--Device-ProgressAttribute-value(value: number): ProgressAttribute<Type>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 当前进度值。<br/> 默认值：0 |

