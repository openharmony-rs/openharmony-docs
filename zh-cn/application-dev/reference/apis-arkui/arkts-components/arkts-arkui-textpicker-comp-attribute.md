# TextPicker属性/事件

```TypeScript
declare class TextPickerAttribute extends CommonMethod<TextPickerAttribute>
```

除支持[通用属性](arkts-arkui-common-comp.md#common)外，还支持以下属性：

除支持[通用事件](arkts-arkui-common-comp.md#common)外，还支持以下事件：

**继承/实现关系：** TextPickerAttribute extends CommonMethod<TextPickerAttribute>

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## canLoop

```TypeScript
canLoop(value: boolean)
```

设置是否可循环滚动。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否可循环滚动。<br>- true：可循环。<br>- false：不可循环。<br>默认值：true |

<a id="canloop-1"></a>

## canLoop

```TypeScript
canLoop(isLoop: Optional<boolean>)
```

设置是否可循环滚动。与[canLoop&lt;sup&gt;10+&lt;/sup&gt;](#canloop)相比，isLoop参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isLoop | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | 是 | 是否可循环滚动。<br>- true：可循环。<br>- false：不可循环。<br>默认值：true <br>当isLoop的值为undefined时，使用默认值。 |

## defaultPickerItemHeight

```TypeScript
defaultPickerItemHeight(value: number | string)
```

设置选择项的高度。

**起始版本：** 8

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number &#124; string | 是 | 选择项的高度。<br>取值范围：<br>number类型：[0, +∞)，单位为vp。<br>string类型：仅支持number类型取值的字符串形式，例如"56"。<br>默认值：选中项56vp，非选中项36vp。<br>**说明：** <br>设置该参数后，选中项与非选中项的高度均为所设置的值。<br>当value的值为负数时，使用默认值。 |

<a id="defaultpickeritemheight-1"></a>

## defaultPickerItemHeight

```TypeScript
defaultPickerItemHeight(height: Optional<number | string>)
```

设置选择项的高度。与[defaultPickerItemHeight](#defaultpickeritemheight)相比，height参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number &#124; string&gt; | 是 | 选择项的高度。<br>取值范围：<br>number类型：[0, +∞)，单位为vp。<br>string类型：仅支持number类型取值的字符串形式，例如"56"。<br>默认值：选中项56vp，非选中项36vp。<br>**说明：** <br>1. 设置该参数后，选中项与非选中项的高度均为所设置的值。<br>2. 当height的值为undefined时，维持上次取值。 |

## defaultTextStyle

```TypeScript
defaultTextStyle(style: TextPickerTextStyle)
```

设置关闭滑动过程中文本样式变化的动效时，各个选项的文本样式。仅当[disableTextStyleAnimation](#disabletextstyleanimation)为true时生效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md) | 是 | 设置关闭滑动过程中文本样式变化的动效时，各个选项的文本样式。<br>默认值：与[Text](arkts-arkui-text-comp.md#text)组件默认值相同。 |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>)
```

设置表冠灵敏度。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sensitivity | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md)&gt; | 是 | 表冠响应灵敏度。<br>默认值：CrownSensitivity.MEDIUM，响应速度适中。不同灵敏度值影响表冠滚动速度与选择项切换速度的对应关系，具体各枚举值的效果请参考[CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md)。 |

## disableTextStyleAnimation

```TypeScript
disableTextStyleAnimation(disabled: boolean)
```

设置是否关闭滑动过程中文本样式变化的动效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disabled | boolean | 是 | 是否关闭滑动过程中文本样式变化的动效。<br>- true：关闭文本样式变化动效。<br>- false：不关闭文本样式变化动效。<br>默认值：false <br>**说明：** <br>设置为true时，滑动过程中无字号、字重、字体颜色等变化动效，且文本均显示为[defaultTextStyle] [defaultTextStyle](#defaulttextstyle)属性设置的样式。如未设置[defaultTextStyle] [defaultTextStyle](#defaulttextstyle)，则显示为[Text](arkts-arkui-text-comp.md#text)组件默认样式。设置为false时，使用系统默认的滑动文本样式变化动效。 |

## disappearTextStyle

```TypeScript
disappearTextStyle(value: PickerTextStyle)
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本颜色、字号、字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) | 是 | 边缘项的文本颜色、字号、字体粗细。<br>默认值：<br>{<br>color: '#ff182431', <br>font: {<br>size: '14fp', <br>weight: FontWeight.Regular <br>} <br>} <br>**说明：** 未调用该方法设置样式时，使用默认值。 |

<a id="disappeartextstyle-1"></a>

## disappearTextStyle

```TypeScript
disappearTextStyle(style: Optional<PickerTextStyle>)
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本颜色、字号、字体粗细。与[disappearTextStyle&lt;sup&gt;10+&lt;/sup&gt;](#disappeartextstyle)相比，style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)&gt; | 是 | 边缘项的文本颜色、字号、字体粗细。<br>默认值：<br>{<br>color: '#ff182431', <br>font: {<br>size: '14fp', <br>weight: FontWeight.Regular <br>} <br>} <br>当style的值为undefined时，使用默认值。 |

<a id="disappeartextstyle-2"></a>

## disappearTextStyle

```TypeScript
disappearTextStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>)
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本颜色、字号、字体粗细、最大字号、最小字号、超长文本截断方式。与[disappearTextStyle&lt;sup&gt;18+&lt;/sup&gt;](#disappeartextstyle-1)相比，style参数新增了对[TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md)类型的支持。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) &#124; [TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md)&gt; | 是 | 边缘项的文本颜色、字号、字体粗细、最大字号、最小字号、超长文本截断方式。<br>默认值：<br>{<br>color: '#ff182431', <br>font: {<br>size: '14fp', <br>weight: FontWeight.Regular <br>}, <br>minFontSize: 0, <br>maxFontSize: 0, <br>overflow: TextOverflow.Clip <br>} <br>当style的值为undefined时，使用默认值。 |

## divider

```TypeScript
divider(value: DividerOptions | null)
```

设置分割线样式，不设置该属性则按“默认值”展示分割线。

[DividerOptions](arkts-arkui-textpicker-comp-divideroptions-i.md)中startMargin + endMargin 超过组件宽度后，startMargin和endMargin会被置0。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [DividerOptions](arkts-arkui-textpicker-comp-divideroptions-i.md) &#124; null | 是 |  |

<a id="divider-1"></a>

## divider

```TypeScript
divider(textDivider: Optional<DividerOptions | null>)
```

设置分割线样式，不设置该属性则按“默认值”展示分割线。与[divider&lt;sup&gt;12+&lt;/sup&gt;](#divider)相比，textDivider参数新增了对undefined类型的支持。

[DividerOptions](arkts-arkui-textpicker-comp-divideroptions-i.md)中startMargin + endMargin 超过组件宽度后，startMargin和endMargin会被置0。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| textDivider | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[DividerOptions](arkts-arkui-textpicker-comp-divideroptions-i.md) &#124; null&gt; | 是 | 默认值：<br>{<br>strokeWidth: '2px', <br>startMargin: 0, <br>endMargin: 0, <br>color: '#33000000'<br>} <br>1. 当textDivider的值为undefined时，使用默认值。<br>2. 当textDivider设置为有效的[DividerOptions](arkts-arkui-textpicker-comp-divideroptions-i.md)时，按设置的样式显示分割线。<br>3. 当textDivider设置为null时，不显示分割线。 |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enable: Optional<boolean>)
```

设置是否开启触控反馈。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | 是 | 设置是否开启触控反馈。<br>- true：开启触控反馈。<br>- false：不开启触控反馈。<br>默认值：true <br>设置为true后，其生效情况取决于系统的硬件是否支持。若硬件不支持触控反馈功能，开启该功能不会产生触控反馈效果，也不会抛出异常。 |

## gradientHeight

```TypeScript
gradientHeight(value: Dimension)
```

设置渐隐效果的高度。若未设置该属性，则显示默认渐隐效果。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 是 | 内容区上下边缘的渐隐高度。<br>默认值：36vp <br>取值范围：[0, +∞)，支持百分比。<br>**说明：** <br>1. value设置为百分比时，100%为TextPicker高度的一半。<br>2. value设置为0时不显示渐隐效果。<br>3. value设置为数字且超过TextPicker高度的一半时，使用默认值。<br>4. 当value的值为负数时，使用默认值。 |

<a id="gradientheight-1"></a>

## gradientHeight

```TypeScript
gradientHeight(height: Optional<Dimension>)
```

设置渐隐效果的高度。若未设置该属性，则显示默认渐隐效果。与[gradientHeight&lt;sup&gt;12+&lt;/sup&gt;](#gradientheight)相比，height参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[Dimension](../arkts-apis/arkts-arkui-dimension-t.md)&gt; | 是 | 内容区上下边缘的渐隐高度。<br>默认值：36vp <br>取值范围：[0, +∞)，支持百分比。<br>**说明：** <br>1. height设置为百分比时，100%为TextPicker高度的一半。<br>2. height设置为0时不显示渐隐效果。<br>3. height设置为数字且超过TextPicker高度的一半时，使用默认值。<br>4. 当height的值为undefined或负数时，使用默认值。 |

## onAccept

```TypeScript
onAccept(callback: (value: string, index: number) => void)
```

点击弹窗中的“确定”按钮时触发该回调。该事件仅在[文本滑动选择器弹窗](arkts-arkui-textpicker-comp.md#text_picker)中生效。

> **说明：** 
> 
> 从API version 8开始支持，从API version 10开始废弃。此接口已完全移除，无替代接口。

**起始版本：** 8

**废弃版本：** 10

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (value: string, index: number) =&gt; void | 是 |  |

## onCancel

```TypeScript
onCancel(callback: () => void)
```

点击弹窗中的“取消”按钮时触发该回调。该事件仅在[文本滑动选择器弹窗](arkts-arkui-textpicker-comp.md#text_picker)中生效。

> **说明：** 
> 
> 从API version 8开始支持，从API version 10开始废弃。此接口已完全移除，无替代接口。

**起始版本：** 8

**废弃版本：** 10

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 |  |

## onChange

```TypeScript
onChange(callback: (value: string[], index: number[]) => void)
```

滑动TextPicker文本内容后，选项归位至选中项位置时，触发该回调。当用户滑动选择器导致选中项变化时触发，不能通过修改双向绑定的状态变量（如selected）来触发。当显示文本或图片加文本列表时，value值为选中项中的文本值，当显示图片列表时，value值为空。

回调会在滑动动画结束后触发，如果需要快速获取索引值变化，建议使用[onEnterSelectedArea](#onenterselectedarea)接口。

**起始版本：** 8

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (value: string[], index: number[]) =&gt; void | 是 |  |

<a id="onchange-1"></a>

## onChange

```TypeScript
onChange(callback: Optional<OnTextPickerChangeCallback>)
```

滑动TextPicker文本内容后，选项归位至选中项位置时，触发该回调。当用户滑动选择器导致选中项变化时触发，不能通过修改双向绑定的状态变量（如selected）来触发。当显示文本或图片加文本列表时，value值为选中项中的文本值，当显示图片列表时，value值为空。与[onChange](#onchange)相比，callback参数新增了对undefined类型的支持。

回调会在滑动动画结束后触发，如果需要快速获取索引值变化，建议使用[onEnterSelectedArea]{@linkTextPickerAttribute#onEnterSelectedArea}接口。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnTextPickerChangeCallback](arkts-arkui-textpicker-comp-ontextpickerchangecallback-t.md)&gt; | 是 | 滑动选中TextPicker文本内容后，触发的回调。<br>当callback的值为undefined时，不使用回调函数。 |

## onEnterSelectedArea

```TypeScript
onEnterSelectedArea(callback: TextPickerEnterSelectedAreaCallback)
```

滑动TextPicker过程中，选项进入分割线区域内（当前列的滑动距离超过选中项高度的一半）时，触发该回调。

> **说明：** 
> 
> - 与[onChange](#onchange)事件的差别在于，该事件的触发时机早于[onChange](#onchange)事件。onEnterSelectedArea在滑动过程中选项进入选中区域时触发，适合实时获取索引值变化，适用于需要快速响应用户滑动的场景；onChange在滑动结束且选中项归位后触发，适合获取最终确认的选中值，适用于需要获取用户最终选择的场景。
> 
> - 与[onScrollStop](#onscrollstop)事件的差别在于，onEnterSelectedArea关注的是选项进入选中区域的逻辑状态，onScrollStop关注的是滚动行为完全停止。需要更早响应索引变化时使用onEnterSelectedArea，需要确认滚动完全停止时使用[onScrollStop](#onscrollstop)。
> 
> - 在多列联动场景中，不建议使用该回调。该回调标识的是滑动过程中选项进入分割线区域内的节点；跟随变化的选项并不涉及滑动，因此回调返回值中仅当前滑动列的值会正常变化，其余未滑动列的值保持不变。
> 
> - 该接口不支持在[attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [TextPickerEnterSelectedAreaCallback](arkts-arkui-textpicker-comp-textpickerenterselectedareacallback-t.md) | 是 | 滑动TextPicker过程中，选项进入分割线区域时触发的回调。 |

## onScrollStop

```TypeScript
onScrollStop(callback: TextPickerScrollStopCallback)
```

文本选择器的选项列滑动停止时触发该事件。

手指拖动选项列触发的滑动，手指离开屏幕且滑动停止时会触发该事件。

> **说明：** 
> 
> - 与[onEnterSelectedArea](#onenterselectedarea)事件的差别在于，onScrollStop关注的是滚动行为完全停止，onEnterSelectedArea关注的是选项进入选中区域的逻辑状态。onEnterSelectedArea能更早响应索引变化，适合实时反馈场景，建议使用[onEnterSelectedArea](#onenterselectedarea)；若需确认滚动行为完全停止，则使用onScrollStop。
> 
> - 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [TextPickerScrollStopCallback](arkts-arkui-textpicker-comp-textpickerscrollstopcallback-t.md) | 是 | 文本选择器的选项列滑动停止时触发该事件。 |

<a id="onscrollstop-1"></a>

## onScrollStop

```TypeScript
onScrollStop(callback: Optional<TextPickerScrollStopCallback>)
```

文本选择器的选项列滑动停止时触发该事件。与[onScrollStop&lt;sup&gt;14+&lt;/sup&gt;](#onscrollstop)相比，callback参数新增了对undefined类型的支持。

手指拖动选项列触发的滑动，手指离开屏幕且滑动停止时会触发该事件。

> **说明：** 
> 
> - 与[onEnterSelectedArea](#onenterselectedarea)事件的差别在于，onScrollStop关注的是滚动行为完全停止，onEnterSelectedArea关注的是选项进入选中区域的逻辑状态。onEnterSelectedArea能更早响应索引变化，适合实时反馈场景，建议使用[onEnterSelectedArea](#onenterselectedarea)；若需确认滚动行为完全停止，则使用onScrollStop。
> 
> - 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TextPickerScrollStopCallback](arkts-arkui-textpicker-comp-textpickerscrollstopcallback-t.md)&gt; | 是 | 文本选择器的选项列滑动停止时触发该事件。<br>当callback的值为undefined时，不使用回调函数。 |

## selectedBackgroundStyle

```TypeScript
selectedBackgroundStyle(style: Optional<PickerBackgroundStyle>)
```

设置选中项的背景样式。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerBackgroundStyle](arkts-arkui-textpicker-comp-pickerbackgroundstyle-i.md)&gt; | 是 | 选中项背景的颜色和边框圆角半径，多列模式时会同时设置所有列的选中项背景的颜色和圆角半径。<br>默认值：<br>{<br>color: $r('sys.color.comp_background_tertiary'), <br>borderRadius: $r('sys.float.corner_radius_level12') <br>} |

## selectedIndex

```TypeScript
selectedIndex(value: number[])
```

设置选中项在数据选择列表中的索引值，优先级高于[TextPickerOptions](arkts-arkui-textpicker-comp-textpickeroptions-i.md)中的"value"属性。单列数据选择器使用number类型。多列数据选择器使用number[]类型。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number[] | 是 | 选中项在数据选择列表中的索引值，索引从0开始。<br>默认值：0 <br>当value的值为负数或者超过数据选择列表的最大索引值时，使用默认值。<br> |

<a id="selectedindex-1"></a>

## selectedIndex

```TypeScript
selectedIndex(index: Optional<number[]>)
```

设置选中项在数据选择列表中的索引值，优先级高于[TextPickerOptions](arkts-arkui-textpicker-comp-textpickeroptions-i.md)中的"value"属性。单列数据选择器使用number类型，多列数据选择器使用number[]类型。与[selectedIndex&lt;sup&gt;10+&lt;/sup&gt;] [selectedIndex](#selectedindex)相比，index参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number[]&gt; | 是 | 选中项在数据选择列表中的索引值，索引从0开始。<br>默认值：0 <br>当index的值为undefined时，使用[TextPickerOptions](arkts-arkui-textpicker-comp-textpickeroptions-i.md)中的selected值。<br>当index的值为负数或者超过数据选择列表的最大索引值时，使用默认值。<br> |

## selectedTextStyle

```TypeScript
selectedTextStyle(value: PickerTextStyle)
```

设置选中项的文本颜色、字号、字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) | 是 | 选中项的文本颜色、字号、字体粗细。<br>默认值：<br>{<br>color: '#ff007dff', <br>font: {<br>size: '20fp', <br>weight: FontWeight.Medium <br>} <br>} <br>**说明：** 未调用该方法设置样式时，使用默认值。 |

<a id="selectedtextstyle-1"></a>

## selectedTextStyle

```TypeScript
selectedTextStyle(style: Optional<PickerTextStyle>)
```

设置选中项的文本颜色、字号、字体粗细。与[selectedTextStyle&lt;sup&gt;10+&lt;/sup&gt;](#selectedtextstyle)相比，style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)&gt; | 是 | 选中项的文本颜色、字号、字体粗细。<br>默认值：<br>{<br>color: '#ff007dff', <br>font: {<br>size: '20fp', <br>weight: FontWeight.Medium <br>} <br>} <br>当style的值为undefined时，使用默认值。 |

<a id="selectedtextstyle-2"></a>

## selectedTextStyle

```TypeScript
selectedTextStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>)
```

设置选中项的文本颜色、字号、字体粗细、最大字号、最小字号、超长文本截断方式。与[selectedTextStyle&lt;sup&gt;18+&lt;/sup&gt;](#selectedtextstyle-1)相比，style参数新增了对[TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md)类型的支持。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) &#124; [TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md)&gt; | 是 | 选中项的文本颜色、字号、字体粗细、最大字号、最小字号、超长文本截断方式。<br>默认值：<br>{<br>color: '#ff007dff', <br>font: {<br>size: '20fp', <br>weight: FontWeight.Medium <br>}, <br>minFontSize: 0, <br>maxFontSize: 0, <br>overflow: TextOverflow.Clip <br>} <br>当style的值为undefined时，使用默认值。 |

## textStyle

```TypeScript
textStyle(value: PickerTextStyle)
```

设置待选项（以选中项为基准向上或向下的第一项）的文本颜色、字号、字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) | 是 | 待选项的文本颜色、字号、字体粗细。<br>默认值：<br>{<br>color: '#ff182431', <br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular <br>} <br>} <br>**说明：** 未调用该方法设置样式时，使用默认值。 |

<a id="textstyle-1"></a>

## textStyle

```TypeScript
textStyle(style: Optional<PickerTextStyle>)
```

设置待选项（以选中项为基准向上或向下的第一项）的文本颜色、字号、字体粗细。与[textStyle&lt;sup&gt;10+&lt;/sup&gt;](#textstyle)相比，style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)&gt; | 是 | 待选项的文本颜色、字号、字体粗细。<br>默认值：<br>{<br>color: '#ff182431', <br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular <br>} <br>} <br>当style的值为undefined时，使用默认值。 |

<a id="textstyle-2"></a>

## textStyle

```TypeScript
textStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>)
```

设置待选项（以选中项为基准向上或向下的第一项）的文本颜色、字号、字体粗细、最大字号、最小字号、超长文本截断方式。与[textStyle&lt;sup&gt;18+&lt;/sup&gt;](#textstyle-1)相比，style参数新增了对[TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md)类型的支持。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) &#124; [TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md)&gt; | 是 | 待选项的文本颜色、字号、字体粗细、最大字号、最小字号、超长文本截断方式。<br>默认值：<br>{<br>color: '#ff182431', <br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular <br>}, <br>minFontSize: 0, <br>maxFontSize: 0, <br>overflow: TextOverflow.Clip <br>} <br>当style的值为undefined时，使用默认值。 |
