# TextPicker属性/事件

除支持[通用属性](./common)外，还支持以下属性：

除支持[通用事件](./common)外，还支持以下事件：

**继承/实现关系：** TextPickerAttribute extends [CommonMethod<TextPickerAttribute>](CommonMethod<TextPickerAttribute>)

**起始版本：** 8

<!--Device-unnamed-declare class TextPickerAttribute extends CommonMethod<TextPickerAttribute>--><!--Device-unnamed-declare class TextPickerAttribute extends CommonMethod<TextPickerAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## canLoop

```TypeScript
canLoop(value: boolean)
```

设置是否可循环滚动。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-canLoop(value: boolean): TextPickerAttribute--><!--Device-TextPickerAttribute-canLoop(value: boolean): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否可循环滚动。<br/>- true：可循环。<br/>- false：不可循环。<br/>默认值：true |

## canLoop

```TypeScript
canLoop(isLoop: Optional<boolean>)
```

设置是否可循环滚动。与[canLoop<sup>10+</sup>](TextPickerAttribute#canLoop(value: boolean))相比，isLoop参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-canLoop(isLoop: Optional<boolean>): TextPickerAttribute--><!--Device-TextPickerAttribute-canLoop(isLoop: Optional<boolean>): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isLoop | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 是否可循环滚动。<br/>- true：可循环。<br/>- false：不可循环。<br/>默认值：true<br/>当isLoop的值为undefined时，使用默认值。 |

## defaultPickerItemHeight

```TypeScript
defaultPickerItemHeight(value: number | string)
```

设置选择项的高度。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-defaultPickerItemHeight(value: number | string): TextPickerAttribute--><!--Device-TextPickerAttribute-defaultPickerItemHeight(value: number | string): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 | 选择项的高度。<br />取值范围：<br />number类型：[0, +∞)，单位为vp。<br />string类型：仅支持number类型取值的字符串形式，例如"56"。<br />默认值：选中项56vp，非选中项36vp。<br />**说明：**<br />设置该参数后，选中项与非选中项的高度均为所设置的值。 |

## defaultPickerItemHeight

```TypeScript
defaultPickerItemHeight(height: Optional<number | string>)
```

设置选择项的高度。与[defaultPickerItemHeight](TextPickerAttribute#defaultPickerItemHeight(value: number | string))相比，height参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-defaultPickerItemHeight(height: Optional<number | string>): TextPickerAttribute--><!--Device-TextPickerAttribute-defaultPickerItemHeight(height: Optional<number | string>): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | [Optional](arkts-arkui-optional-t.md)<number \| string> | 是 | 选择项的高度。<br />取值范围：<br />number类型：[0, +∞)，单位为vp。<br />string类型：仅支持number类型取值的字符串形式，例如"56"。<br />默认值：选中项56vp，非选中项36vp。<br />**说明：**<br />1. 设置该参数后，选中项与非选中项的高度均为所设置的值。<br/>2. 当height的值为undefined时，维持上次取值。 |

## defaultTextStyle

```TypeScript
defaultTextStyle(style: TextPickerTextStyle)
```

设置关闭滑动过程中文本样式变化的动效时，各个选项的文本样式。仅当[disableTextStyleAnimation](TextPickerAttribute#disableTextStyleAnimation)为true时生效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-defaultTextStyle(style: TextPickerTextStyle): TextPickerAttribute--><!--Device-TextPickerAttribute-defaultTextStyle(style: TextPickerTextStyle): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [TextPickerTextStyle](arkts-arkui-text-picker-textpickertextstyle-i.md) | 是 | 设置关闭滑动过程中文本样式变化的动效时，各个选项的文本样式。<br/>默认值：与[Text](./text)组件默认值相同。 |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>)
```

设置表冠灵敏度。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): TextPickerAttribute--><!--Device-TextPickerAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sensitivity | [Optional](arkts-arkui-optional-t.md)<CrownSensitivity> | 是 | 表冠响应灵敏度。<br/>默认值：CrownSensitivity.MEDIUM，响应速度适中。 |

## disableTextStyleAnimation

```TypeScript
disableTextStyleAnimation(disabled: boolean)
```

设置是否关闭滑动过程中文本样式变化的动效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-disableTextStyleAnimation(disabled: boolean): TextPickerAttribute--><!--Device-TextPickerAttribute-disableTextStyleAnimation(disabled: boolean): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disabled | boolean | 是 | 是否关闭滑动过程中文本样式变化的动效。<br/>- true：关闭文本样式变化动效。<br/>- false：不关闭文本样式变化动效。<br/>默认值：false<br/>**说明：**<br/>设置为true时，滑动过程中无字号、字重、字体颜色等变化动效，且文本均显示为[defaultTextStyle](TextPickerAttribute#defaultTextStyle)属性设置的样式。如未设置[defaultTextStyle](TextPickerAttribute#defaultTextStyle)，则显示为[Text](./text)组件默认样式。 |

## disappearTextStyle

```TypeScript
disappearTextStyle(value: PickerTextStyle)
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本颜色、字号、字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-disappearTextStyle(value: PickerTextStyle): TextPickerAttribute--><!--Device-TextPickerAttribute-disappearTextStyle(value: PickerTextStyle): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-common-pickertextstyle-i.md) | 是 | 边缘项的文本颜色、字号、字体粗细。<br/>默认值：<br/>{<br/>color: '#ff182431',<br/>font: {<br/>size: '14fp', <br/>weight: FontWeight.Regular<br/>}<br/>} |

## disappearTextStyle

```TypeScript
disappearTextStyle(style: Optional<PickerTextStyle>)
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本颜色、字号、字体粗细。与[disappearTextStyle<sup>10+</sup>](TextPickerAttribute#disappearTextStyle(value: PickerTextStyle))相比，style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-disappearTextStyle(style: Optional<PickerTextStyle>): TextPickerAttribute--><!--Device-TextPickerAttribute-disappearTextStyle(style: Optional<PickerTextStyle>): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)<PickerTextStyle> | 是 | 边缘项的文本颜色、字号、字体粗细。<br/>默认值：<br/>{<br/>color:'#ff182431',<br/>font: {<br/>size: '14fp', <br/>weight: FontWeight.Regular<br/>}<br/>}<br/>当style的值为undefined时，使用默认值。 |

## disappearTextStyle

```TypeScript
disappearTextStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>)
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本颜色、字号、字体粗细、最大字号、最小字号、超长文本截断方式。与[disappearTextStyle](TextPickerAttribute#disappearTextStyle(style: Optional<PickerTextStyle>))<sup>18+</sup>相比，style参数新增了对[TextPickerTextStyle](arkts-arkui-text-picker-textpickertextstyle-i.md)类型的支持。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-disappearTextStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>): TextPickerAttribute--><!--Device-TextPickerAttribute-disappearTextStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)<PickerTextStyle \| TextPickerTextStyle> | 是 | 边缘项的文本颜色、字号、字体粗细、最大字号、最小字号、超长文本截断方式。<br/>默认值：<br/>{<br/>color: '#ff182431',<br/>font: {<br/>size: '14fp', <br/>weight:FontWeight.Regular<br/>},<br/>minFontSize: 0,<br/>maxFontSize: 0,<br/>overflow: TextOverflow.Clip<br/>}<br/>当style的值为undefined时，使用默认值。 |

## divider

```TypeScript
divider(value: DividerOptions | null)
```

设置分割线样式，不设置该属性则按“默认值”展示分割线。

[DividerOptions](arkts-arkui-text-picker-divideroptions-i.md)中startMargin + endMargin 超过组件宽度后，startMargin和endMargin会被置0。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-divider(value: DividerOptions | null): TextPickerAttribute--><!--Device-TextPickerAttribute-divider(value: DividerOptions | null): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | DividerOptions \| null | 是 |  |

## divider

```TypeScript
divider(textDivider: Optional<DividerOptions | null>)
```

设置分割线样式，不设置该属性则按“默认值”展示分割线。与[divider<sup>12+</sup>](TextPickerAttribute#divider(value: DividerOptions | null))相比，textDivider参数新增了对undefined类型的支持。

[DividerOptions](arkts-arkui-text-picker-divideroptions-i.md)中startMargin + endMargin 超过组件宽度后，startMargin和endMargin会被置0。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-divider(textDivider: Optional<DividerOptions | null>): TextPickerAttribute--><!--Device-TextPickerAttribute-divider(textDivider: Optional<DividerOptions | null>): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| textDivider | [Optional](arkts-arkui-optional-t.md)<DividerOptions \| null> | 是 | 默认值：<br/>{<br/>strokeWidth: '2px', <br/>startMargin: 0,<br/>endMargin: 0, <br/>color: '#33000000'<br/>}<br/>1. 当textDivider的值为undefined时，使用默认值。<br/>2. 当textDivider设置为有效的[DividerOptions](arkts-arkui-text-picker-divideroptions-i.md)时，按设置的样式显示分割线。<br/>3. 当textDivider设置为null时，不显示分割线。 |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enable: Optional<boolean>)
```

设置是否开启触控反馈。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-enableHapticFeedback(enable: Optional<boolean>): TextPickerAttribute--><!--Device-TextPickerAttribute-enableHapticFeedback(enable: Optional<boolean>): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 设置是否开启触控反馈。<br/>- true：开启触控反馈。<br/>- false：不开启触控反馈。<br/>默认值：true<br/>设置为true后，其生效情况取决于系统的硬件是否支持。 |

## gradientHeight

```TypeScript
gradientHeight(value: Dimension)
```

设置渐隐效果的高度。若未设置该属性，则显示默认渐隐效果。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-gradientHeight(value: Dimension): TextPickerAttribute--><!--Device-TextPickerAttribute-gradientHeight(value: Dimension): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 是 | 内容区上下边缘的渐隐高度。<br/>默认值：36vp<br/>取值范围：[0, +∞)，支持百分比。<br/>**说明：**<br/>1. value设置为百分比时，100%为TextPicker高度的一半。<br/>2. value设置为0时不显示渐隐效果。<br/>3. value设置为数字且超过TextPicker高度的一半时，使用默认值。<br/>4. 当value的值为负数时，使用默认值。 |

## gradientHeight

```TypeScript
gradientHeight(height: Optional<Dimension>)
```

设置渐隐效果的高度。若未设置该属性，则显示默认渐隐效果。与[gradientHeight<sup>12+</sup>](TextPickerAttribute#gradientHeight(value: Dimension))相比，height参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-gradientHeight(height: Optional<Dimension>): TextPickerAttribute--><!--Device-TextPickerAttribute-gradientHeight(height: Optional<Dimension>): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | [Optional](arkts-arkui-optional-t.md)<Dimension> | 是 | 内容区上下边缘的渐隐高度。<br/>默认值：36vp<br/>取值范围：[0, +∞)，支持百分比。<br/>**说明：**<br/>1. height设置为百分比时，100%为TextPicker高度的一半。<br/>2. height设置为0时不显示渐隐效果。<br/>3. height设置为数字且超过TextPicker高度的一半时，使用默认值。<br/>4. 当height的值为undefined或负数时，使用默认值。 |

## onAccept

```TypeScript
onAccept(callback: (value: string, index: number) => void)
```

点击弹窗中的“确定”按钮时触发该回调。该事件仅在[文本滑动选择器弹窗](./text_picker)中生效。

从API version 8开始支持，从API version 10开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 10

<!--Device-TextPickerAttribute-onAccept(callback: (value: string, index: number) => void): TextPickerAttribute--><!--Device-TextPickerAttribute-onAccept(callback: (value: string, index: number) => void): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (value: string, index: number) => void | 是 |  |

## onCancel

```TypeScript
onCancel(callback: () => void)
```

点击弹窗中的“取消”按钮时触发该回调。该事件仅在[文本滑动选择器弹窗](./text_picker)中生效。

从API version 8开始支持，从API version 10开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 10

<!--Device-TextPickerAttribute-onCancel(callback: () => void): TextPickerAttribute--><!--Device-TextPickerAttribute-onCancel(callback: () => void): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () => void | 是 |  |

## onChange

```TypeScript
onChange(callback: (value: string | string[], index: number | number[]) => void)
```

滑动TextPicker文本内容后，选项归位至选中项位置时，触发该回调。不能通过双向绑定的状态变量触发。当显示文本或图片加文本列表时，value值为选中项中的文本值，当显示图片列表时，value值为空。

回调会在滑动动画结束后触发，如果需要快速获取索引值变化，建议使用[onEnterSelectedArea](TextPickerAttribute#onEnterSelectedArea)接口。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-onChange(callback: (value: string | string[], index: number | number[]) => void): TextPickerAttribute--><!--Device-TextPickerAttribute-onChange(callback: (value: string | string[], index: number | number[]) => void): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (value: string \| string[], index: number \| number[]) => void | 是 |  |

## onChange

```TypeScript
onChange(callback: Optional<OnTextPickerChangeCallback>)
```

滑动TextPicker文本内容后，选项归位至选中项位置时，触发该回调。不能通过双向绑定的状态变量触发。当显示文本或图片加文本列表时，value值为选中项中的文本值，当显示图片列表时，value值为空。与[onChange](TextPickerAttribute#onChange(callback: (value: string | string[],index: number | number[]) => void))相比，callback参数新增了对undefined类型的支持。

回调会在滑动动画结束后触发，如果需要快速获取索引值变化，建议使用[onEnterSelectedArea](TextPickerAttribute#onEnterSelectedArea)接口。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-onChange(callback: Optional<OnTextPickerChangeCallback>): TextPickerAttribute--><!--Device-TextPickerAttribute-onChange(callback: Optional<OnTextPickerChangeCallback>): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)<OnTextPickerChangeCallback> | 是 | 滑动选中TextPicker文本内容后，触发的回调。<br/>当callback的值为undefined时，不使用回调函数。 |

## onEnterSelectedArea

```TypeScript
onEnterSelectedArea(callback: TextPickerEnterSelectedAreaCallback)
```

滑动TextPicker过程中，选项进入分割线区域内（当前列的滑动距离超过选中项高度的一半）时，触发该回调。

> **说明：**  
>  
> - 与[onChange]  
> {@link TextPickerAttribute#onChange(callback:(value: string | string[], index: number | number[]) => void)}事件  
> 的差别在于，该事件的触发时机早于[onChange]  
> {@link TextPickerAttribute#onChange(callback:(value: string | string[], index: number | number[]) => void)}事件。  
>  
> - 在多列联动场景中，不建议使用该回调，由于该回调标识的是滑动过程中选项进入分割线区域内的节点，而跟随变化的选项并不涉及滑动，  
> 因此，回调的返回值中，仅当前滑动列的值会正常变化，其余未滑动列的值保持不变。  
>  
> - 该接口不支持在[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-onEnterSelectedArea(callback: TextPickerEnterSelectedAreaCallback): TextPickerAttribute--><!--Device-TextPickerAttribute-onEnterSelectedArea(callback: TextPickerEnterSelectedAreaCallback): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [TextPickerEnterSelectedAreaCallback](arkts-arkui-textpickerenterselectedareacallback-t.md) | 是 | 滑动TextPicker过程中，选项进入分割线区域时触发的回调。 |

## onScrollStop

```TypeScript
onScrollStop(callback: TextPickerScrollStopCallback)
```

文本选择器的选项列滑动停止时触发该事件。

手指拖动选项列触发的滑动，手指离开屏幕且滑动停止时会触发该事件。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-onScrollStop(callback: TextPickerScrollStopCallback): TextPickerAttribute--><!--Device-TextPickerAttribute-onScrollStop(callback: TextPickerScrollStopCallback): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [TextPickerScrollStopCallback](arkts-arkui-textpickerscrollstopcallback-t.md) | 是 | 文本选择器的选项列滑动停止时触发该事件。 |

## onScrollStop

```TypeScript
onScrollStop(callback: Optional<TextPickerScrollStopCallback>)
```

文本选择器的选项列滑动停止时触发该事件。与[onScrollStop<sup>14+</sup>](TextPickerAttribute#onScrollStop(callback: TextPickerScrollStopCallback))相比，callback参数新增了对undefined类型的支持。

手指拖动选项列触发的滑动，手指离开屏幕且滑动停止时会触发该事件。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-onScrollStop(callback: Optional<TextPickerScrollStopCallback>): TextPickerAttribute--><!--Device-TextPickerAttribute-onScrollStop(callback: Optional<TextPickerScrollStopCallback>): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)<TextPickerScrollStopCallback> | 是 | 文本选择器的选项列滑动停止时触发该事件。<br/>当callback的值为undefined时，不使用回调函数。 |

## selectedBackgroundStyle

```TypeScript
selectedBackgroundStyle(style: Optional<PickerBackgroundStyle>)
```

设置选中项的背景样式。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-selectedBackgroundStyle(style: Optional<PickerBackgroundStyle>): TextPickerAttribute--><!--Device-TextPickerAttribute-selectedBackgroundStyle(style: Optional<PickerBackgroundStyle>): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)<PickerBackgroundStyle> | 是 | 选中项背景的颜色和边框圆角半径，多列模式时会同时设置所有列的选中项背景的颜色和圆角半径。<br/>默认值：<br/>{ <br/>color: $r('sys.color.comp_background_tertiary'),<br/>borderRadius: $r('sys.float.corner_radius_level12')<br/>} |

## selectedIndex

```TypeScript
selectedIndex(value: number | number[])
```

设置选中项在数据选择列表中的索引值，优先级高于[TextPickerOptions](arkts-arkui-text-picker-textpickeroptions-i.md)中的"value"属性。单列数据选择器使用number类型。多列数据选择器使用number[]类型。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-selectedIndex(value: number | number[]): TextPickerAttribute--><!--Device-TextPickerAttribute-selectedIndex(value: number | number[]): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| number[] | 是 | 选中项在数据选择列表中的索引值，索引从0开始。<br/>默认值：0<br/>当value的值为负数或者超过数据选择列表的最大索引值时，使用默认值。 |

## selectedIndex

```TypeScript
selectedIndex(index: Optional<number | number[]>)
```

设置选中项在数据选择列表中的索引值，优先级高于[TextPickerOptions](arkts-arkui-text-picker-textpickeroptions-i.md)中的"value"属性。单列数据选择器使用number类型，多列数据选择器使用number[]类型。与[selectedIndex<sup>10+</sup>](TextPickerAttribute#selectedIndex(value: number | number[]))相比，index参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-selectedIndex(index: Optional<number | number[]>): TextPickerAttribute--><!--Device-TextPickerAttribute-selectedIndex(index: Optional<number | number[]>): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | [Optional](arkts-arkui-optional-t.md)<number \| number[]> | 是 | 选中项在数据选择列表中的索引值，索引从0开始。<br/>默认值：0<br/>当index的值为undefined时，使用[TextPickerOptions](arkts-arkui-text-picker-textpickeroptions-i.md)中的selected值。<br/>当index的值为负数或者超过数据选择列表的最大索引值时，使用默认值。<br/> |

## selectedTextStyle

```TypeScript
selectedTextStyle(value: PickerTextStyle)
```

设置选中项的文本颜色、字号、字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-selectedTextStyle(value: PickerTextStyle): TextPickerAttribute--><!--Device-TextPickerAttribute-selectedTextStyle(value: PickerTextStyle): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-common-pickertextstyle-i.md) | 是 | 选中项的文本颜色、字号、字体粗细。<br/>默认值：<br/>{<br/>color: '#ff007dff',<br/>font: {<br/>size: '20fp', <br/>weight: FontWeight.Medium<br/>}<br/>} |

## selectedTextStyle

```TypeScript
selectedTextStyle(style: Optional<PickerTextStyle>)
```

设置选中项的文本颜色、字号、字体粗细。与[selectedTextStyle<sup>10+</sup>](TextPickerAttribute#selectedTextStyle(value: PickerTextStyle))相比，style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-selectedTextStyle(style: Optional<PickerTextStyle>): TextPickerAttribute--><!--Device-TextPickerAttribute-selectedTextStyle(style: Optional<PickerTextStyle>): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)<PickerTextStyle> | 是 | 选中项的文本颜色、字号、字体粗细。<br/>默认值：<br/>{<br/>color:'#ff007dff',<br/>font: {<br/>size: '20fp', <br/>weight: FontWeight.Medium<br/>}<br/>}<br/>当style的值为undefined时，使用默认值。 |

## selectedTextStyle

```TypeScript
selectedTextStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>)
```

设置选中项的文本颜色、字号、字体粗细、最大字号、最小字号、超长文本截断方式。与[selectedTextStyle](TextPickerAttribute#selectedTextStyle(style: Optional<PickerTextStyle>))<sup>18+</sup>相比，style参数新增了对[TextPickerTextStyle](arkts-arkui-text-picker-textpickertextstyle-i.md)类型的支持。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-selectedTextStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>): TextPickerAttribute--><!--Device-TextPickerAttribute-selectedTextStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)<PickerTextStyle \| TextPickerTextStyle> | 是 | 选中项的文本颜色、字号、字体粗细、最大字号、最小字号、超长文本截断方式。<br/>默认值：<br/>{<br/>color: '#ff007dff',<br/>font: {<br/>size: '20fp', <br/>weight:FontWeight.Medium<br/>},<br/>minFontSize: 0,<br/>maxFontSize: 0,<br/>overflow: TextOverflow.Clip<br/>}<br/>当style的值为undefined时，使用默认值。 |

## textStyle

```TypeScript
textStyle(value: PickerTextStyle)
```

设置待选项（以选中项为基准向上或向下的第一项）的文本颜色、字号、字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-textStyle(value: PickerTextStyle): TextPickerAttribute--><!--Device-TextPickerAttribute-textStyle(value: PickerTextStyle): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-common-pickertextstyle-i.md) | 是 | 待选项的文本颜色、字号、字体粗细。<br/>默认值：<br/>{<br/>color: '#ff182431',<br/>font: {<br/>size: '16fp', <br/>weight: FontWeight.Regular<br/>}<br/>} |

## textStyle

```TypeScript
textStyle(style: Optional<PickerTextStyle>)
```

设置待选项（以选中项为基准向上或向下的第一项）的文本颜色、字号、字体粗细。与[textStyle<sup>10+</sup>](TextPickerAttribute#textStyle(value: PickerTextStyle))相比，style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-textStyle(style: Optional<PickerTextStyle>): TextPickerAttribute--><!--Device-TextPickerAttribute-textStyle(style: Optional<PickerTextStyle>): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)<PickerTextStyle> | 是 | 待选项的文本颜色、字号、字体粗细。<br/>默认值：<br/>{<br/>color:'#ff182431',<br/>font: {<br/>size: '16fp', <br/>weight: FontWeight.Regular<br/>}<br/>}<br/>当style的值为undefined时，使用默认值。 |

## textStyle

```TypeScript
textStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>)
```

设置待选项（以选中项为基准向上或向下的第一项）的文本颜色、字号、字体粗细、最大字号、最小字号、超长文本截断方式。与[textStyle](TextPickerAttribute#textStyle(style: Optional<PickerTextStyle>))<sup>18+</sup>相比，style参数新增了对[TextPickerTextStyle](arkts-arkui-text-picker-textpickertextstyle-i.md)类型的支持。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerAttribute-textStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>): TextPickerAttribute--><!--Device-TextPickerAttribute-textStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)<PickerTextStyle \| TextPickerTextStyle> | 是 | 待选项的文本颜色、字号、字体粗细、最大字号、最小字号、超长文本截断方式。<br/>默认值：<br/>{<br/>color: '#ff182431',<br/>font: {<br/>size: '16fp', <br/>weight:FontWeight.Regular<br/>},<br/>minFontSize: 0,<br/>maxFontSize: 0,<br/>overflow: TextOverflow.Clip<br/>}<br/>当style的值为undefined时，使用默认值。 |

