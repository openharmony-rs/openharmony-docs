# Progress属性/事件

除支持[通用属性](arkts-arkui-commonmethod-c.md)外，还支持以下属性。支持[通用事件](arkts-arkui-commonmethod-c.md)。

**继承/实现关系：** ProgressAttribute extends CommonMethod<ProgressAttribute<Type>>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## color

```TypeScript
color(value: ResourceColor | LinearGradient)
```

设置进度条前景色。从API version 10开始支持利用LinearGradient设置Ring样式的渐变色。Ring类型不建议设置透明度，如需设置透明度，建议使用 DataPanel。从API version 23开始支持利用LinearGradient设置Linear样式和Capsule样式的渐变色。API version 22及之前版本使用该方式设置时，会以默认主题色显示。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) \| LinearGradient | 是 | 进度条前景色。 从API version 10开始支持利用LinearGradient设置Ring样式的渐变色，从API version 23开始支持利用LinearGradient设置Linear样式和Capsule样式的渐变 色。 默认值：    - Capsule：       API version 9及以下：'#ff007dff'   API version 10：'#33006cde'   API version 11及以上：'#33007dff'   - Ring：       API version 9及以下：'#ff007dff'   API version 10及以上：起始端：'#ff86c1ff'，结束端：'#ff254ff7'   - 其他样式：'#ff007dff' |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<ProgressConfiguration>)
```

定制progress内容区的方法。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;[ProgressConfiguration](arkts-arkui-progressconfiguration-i.md)&gt; | 是 | The contentModifier of progress. |

## privacySensitive

```TypeScript
privacySensitive(isPrivacySensitiveMode: Optional<boolean>)
```

设置隐私敏感。

> **说明：**
> 
> 从API version 20开始，该接口支持在attributeModifier中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isPrivacySensitiveMode | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 设置隐私敏感，隐私模式下进度清零，文字将被遮罩。true：打开隐私敏感；false：关闭隐私敏感。 默认值：false    **说明：** 设置null表示不敏感。<!--Del--> 需要在卡片中使用Progress，并用FormComponent组件设置[隐私遮罩](arkts-arkui-commonmethod-c.md#obscured)属性，显示卡片时才有 隐私遮罩效果。<!--DelEnd--> |

## style

```TypeScript
style(value: Style)
```

设置组件的样式。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Style | 是 | 组件的样式。    **说明：** 不同的type需分别对应相应的style属性设置，详细映射关系参考 [ProgressStyleMap](arkts-arkui-progressstylemap-i.md)。 - CapsuleStyleOptions：设置Capsule的样式。 - RingStyleOptions：设置Ring的样式。 - LinearStyleOptions：设置Linear的样式。 - ScaleRingStyleOptions：设置ScaleRing的样式。 - EclipseStyleOptions：设置Eclipse的样式。 - ProgressStyleOptions：仅可设置各类型进度条的strokeWidth、scaleCount、scaleWidth，仅对支持这些样式设置的进度条生效。 |

## value

```TypeScript
value(value: number)
```

设置当前进度值。设置小于0的数值时置为0，设置大于total的数值时置为total。设置非法值时按默认值处理。当Ring样式的status属性设置为ProgressStatus.LOADING时，设置进度值不生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 当前进度值。 默认值：0 取值范围：[0, total]，设置小于0的数值时置为0，设置大于total的数值时置为total，设置非法值时按默认值处理。    **说明：** 当Ring类型进度条的status设置为ProgressStatus.LOADING时，设置进度值不生效。 |
