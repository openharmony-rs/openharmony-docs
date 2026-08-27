# TextPicker属性/事件

除支持通用属性外，还支持以下属性：除支持通用事件外，还支持以下事件：

**继承/实现关系：** TextPickerAttribute extends CommonMethod<TextPickerAttribute>

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## canLoop

```TypeScript
canLoop(value: boolean)
```

设置是否可循环滚动。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否可循环滚动。    - true：可循环。    - false：不可循环。    默认值：true |

## canLoop

```TypeScript
canLoop(isLoop: Optional<boolean>)
```

设置是否可循环滚动。与[canLoop&lt;sup&gt;10+&lt;/sup&gt;](#canloop)相比， isLoop参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isLoop | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否可循环滚动。    - true：可循环。    - false：不可循环。    默认值：true 当isLoop的值为undefined时，使用默认值。 |

## defaultPickerItemHeight

```TypeScript
defaultPickerItemHeight(value: number | string)
```

设置选择项的高度。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 | 选择项的高度。 取值范围： number类型：[0, +∞)，单位为vp。 string类型：仅支持number类型取值的字符串形式，例如"56"。 默认值：选中项56vp，非选中项36vp。    **说明：** 设置该参数后，选中项与非选中项的高度均为所设置的值。 当value的值为负数时，使用默认值。 |

## defaultPickerItemHeight

```TypeScript
defaultPickerItemHeight(height: Optional<number | string>)
```

设置选择项的高度。 与[defaultPickerItemHeight](#defaultpickeritemheight)相比， height参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | [Optional](arkts-arkui-optional-t.md)&lt;number \| string & gt; | 是 | 选择项的高度。 取值范围： number类型：[0, +∞)，单位为vp。 string类型：仅支持number类型取值的字符串形式，例如"56"。 默认值：选中项56vp，非选中项36vp。    **说明：** 1. 设置该参数后，选中项与非选中项的高度均为所设置的值。  2. 当height的值为undefined时，维持上次取值。 |

## defaultTextStyle

```TypeScript
defaultTextStyle(style: TextPickerTextStyle)
```

设置关闭滑动过程中文本样式变化的动效时，各个选项的文本样式。 仅当[disableTextStyleAnimation](#disabletextstyleanimation)为true时生效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [TextPickerTextStyle](arkts-arkui-textpickertextstyle-i.md) | 是 | 设置关闭滑动过程中文本样式变化的动效时，各个选项的文本样式。 默认值：与Text组件默认值相同。 |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>)
```

设置表冠灵敏度。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sensitivity | [Optional](arkts-arkui-optional-t.md)&lt;[CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md)&gt; | 是 | 表冠响应灵敏度。 默认值：CrownSensitivity.MEDIUM，响应速度适中。不同灵敏度值影响表冠滚动速度与选择项切换速度的对应关系， 具体各枚举值的效果请参考[CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md)。 |

## disableTextStyleAnimation

```TypeScript
disableTextStyleAnimation(disabled: boolean)
```

设置是否关闭滑动过程中文本样式变化的动效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disabled | boolean | 是 | 是否关闭滑动过程中文本样式变化的动效。    - true：关闭文本样式变化动效。    - false：不关闭文本样式变化动效。    默认值：false    **说明：** 设置为true时，滑动过程中无字号、字重、字体颜色等变化动效，且文本均显示为[defaultTextStyle] [defaultTextStyle](#defaulttextstyle)属性设置的样式。如未设置[defaultTextStyle] [defaultTextStyle](#defaulttextstyle)，则显示为Text组件默认样式。设置为false时，使用系统默认的滑动文本 样式变化动效。 |

## disappearTextStyle

```TypeScript
disappearTextStyle(value: PickerTextStyle)
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本颜色、字号、字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-pickertextstyle-i.md) | 是 | 边缘项的文本颜色、字号、字体粗细。 默认值： {color: '#ff182431', font: {size: '14fp', weight: FontWeight.Regular } }    **说明：**未调用该方法设置样式时，使用默认值。 |

## disappearTextStyle

```TypeScript
disappearTextStyle(style: Optional<PickerTextStyle>)
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本颜色、字号、字体粗细。与 [disappearTextStyle&lt;sup&gt;10+&lt;/sup&gt;](#disappeartextstyle)相比，style 参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-pickertextstyle-i.md)&gt; | 是 | 边缘项的文本颜色、字号、字体粗细。 默认值： {color: '#ff182431', font: {size: '14fp', weight: FontWeight.Regular } } 当style的值为undefined时，使用默认值。 |

## disappearTextStyle

```TypeScript
disappearTextStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>)
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本颜色、字号、字体粗细、最大字号、最小字号、超长文本截断方式。与 [disappearTextStyle&lt;sup&gt;18+&lt;/sup&gt;](#disappeartextstyle) 相比，style参数新增了对[TextPickerTextStyle](arkts-arkui-textpickertextstyle-i.md)类型的支持。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-pickertextstyle-i.md) \| [TextPickerTextStyle](arkts-arkui-textpickertextstyle-i.md)&gt; | 是 | 边缘项的文本颜色、字号、字体粗细、最大字号、最小字号、超长 文本截断方式。 默认值： {color: '#ff182431', font: {size: '14fp', weight: FontWeight.Regular }, minFontSize: 0, maxFontSize: 0, overflow: TextOverflow.Clip } 当style的值为undefined时，使用默认值。 |

## divider

```TypeScript
divider(value: DividerOptions | null)
```

设置分割线样式，不设置该属性则按“默认值”展示分割线。  
[DividerOptions](arkts-arkui-divideroptions-i.md)中startMargin + endMargin 超过组件宽度后，startMargin和endMargin会被置0。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [DividerOptions](arkts-arkui-divideroptions-i.md) \| null | 是 |  |

## divider

```TypeScript
divider(textDivider: Optional<DividerOptions | null>)
```

设置分割线样式，不设置该属性则按“默认值”展示分割线。与 [divider&lt;sup&gt;12+&lt;/sup&gt;](#divider)相比，textDivider参数新增了对 undefined类型的支持。  
[DividerOptions](arkts-arkui-divideroptions-i.md)中startMargin + endMargin 超过组件宽度后，startMargin和endMargin会被置0。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| textDivider | [Optional](arkts-arkui-optional-t.md)&lt;[DividerOptions](arkts-arkui-divideroptions-i.md) \| null & gt; | 是 | 默认值： {strokeWidth: '2px', startMargin: 0, endMargin: 0, color: '#33000000'}  1. 当textDivider的值为undefined时，使用默认值。  2. 当textDivider设置为有效的[DividerOptions](arkts-arkui-divideroptions-i.md)时，按设置的样式显示分割线。  3. 当textDivider设置为null时，不显示分割线。 |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enable: Optional<boolean>)
```

设置是否开启触控反馈。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 设置是否开启触控反馈。    - true：开启触控反馈。    - false：不开启触控反馈。    默认值：true 设置为true后，其生效情况取决于系统的硬件是否支持。若硬件不支持触控反馈功能，开启该功能不会产生触控反馈效果，也不会抛出异常。 |

## gradientHeight

```TypeScript
gradientHeight(value: Dimension)
```

设置渐隐效果的高度。若未设置该属性，则显示默认渐隐效果。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 是 | 内容区上下边缘的渐隐高度。 默认值：36vp 取值范围：[0, +∞)，支持百分比。    **说明：** 1. value设置为百分比时，100%为TextPicker高度的一半。  2. value设置为0时不显示渐隐效果。  3. value设置为数字且超过TextPicker高度的一半时，使用默认值。  4. 当value的值为负数时，使用默认值。 |

## gradientHeight

```TypeScript
gradientHeight(height: Optional<Dimension>)
```

设置渐隐效果的高度。若未设置该属性，则显示默认渐隐效果。与 [gradientHeight&lt;sup&gt;12+&lt;/sup&gt;](#gradientheight)相比，height参数新增了对 undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | [Optional](arkts-arkui-optional-t.md)&lt;[Dimension](../arkts-apis/arkts-arkui-dimension-t.md)&gt; | 是 | 内容区上下边缘的渐隐高度。 默认值：36vp 取值范围：0, +∞)，支持百分比。    **说明：** 1. height设置为百分比时，100%为TextPicker高度的一半。  2. height设置为0时不显示渐隐效果。  3. height设置为数字且超过TextPicker高度的一半时，使用默认值。  4. 当height的值为undefined或负数时，使用默认值。 |

## onAccept

```TypeScript
onAccept(callback: (value: string, index: number) => void)
```

点击弹窗中的“确定”按钮时触发该回调。该事件仅在[文本滑动选择器弹窗中生效。

> **说明：**
> 
> 从API version 8开始支持，从API version 10开始废弃。此接口已完全移除，无替代接口。

**起始版本：** 8

**废弃版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (value: string, index: number) = & gt; void | 是 |  |

## onCancel

```TypeScript
onCancel(callback: () => void)
```

点击弹窗中的“取消”按钮时触发该回调。该事件仅在文本滑动选择器弹窗中生效。

> **说明：**
> 
> 从API version 8开始支持，从API version 10开始废弃。此接口已完全移除，无替代接口。

**起始版本：** 8

**废弃版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () = & gt; void | 是 |  |

## onChange

```TypeScript
onChange(callback: (value: string | string[], index: number | number[]) => void)
```

滑动TextPicker文本内容后，选项归位至选中项位置时，触发该回调。当用户滑动选择器导致选中项变化时触发，不能通过修改双向绑定的状态变量 （如selected）来触发。当显示文本或图片加文本列表时，value值为选中项中的文本值，当显示图片列表时，value值为空。回调会在滑动动画结束后触发，如果需要快速获取索引值变化， 建议使用[onEnterSelectedArea](#onenterselectedarea)接口。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (value: string \| string[], index: number \| number[]) = & gt; void | 是 |  |

## onChange

```TypeScript
onChange(callback: Optional<OnTextPickerChangeCallback>)
```

滑动TextPicker文本内容后，选项归位至选中项位置时，触发该回调。当用户滑动选择器导致选中项变化时触发，不能通过修改双向绑定的状态变量 （如selected）来触发。当显示文本或图片加文本列表时，value值为选中项中的文本值，当显示图片列表时，value值为空。与 onChange相比，callback参数新增了对undefined类型的支持。回调会在滑动动画结束后触发，如果需要快速获取索引值变化， 建议使用[onEnterSelectedArea]{@linkTextPickerAttribute#onEnterSelectedArea}接口。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;[OnTextPickerChangeCallback](arkts-arkui-ontextpickerchangecallback-t.md)&gt; | 是 | 滑动选中TextPicker文本内容后，触发的回调。 当callback的值为undefined时，不使用回调函数。 |

## onEnterSelectedArea

```TypeScript
onEnterSelectedArea(callback: TextPickerEnterSelectedAreaCallback)
```

滑动TextPicker过程中，选项进入分割线区域内（当前列的滑动距离超过选中项高度的一半）时，触发该回调。

> **说明：**
> 
> - 与
> onChange
> 事件的差别在于，该事件的触发时机早于
> onChange
> 事件。onEnterSelectedArea在滑动过程中选项进入选中区域时触发，适合实时获取索引值变化，适用于需要快速响应用户滑动的场景；onChange在滑
> 动结束且选中项归位后触发，适合获取最终确认的选中值，适用于需要获取用户最终选择的场景。
> 
> - 与[onScrollStop](#onscrollstop)事件的差别在于，
> onEnterSelectedArea关注的是选项进入选中区域的逻辑状态，onScrollStop关注的是滚动行为完全停止。需要更早响应索引变化时使用
> onEnterSelectedArea，需要确认滚动完全停止时使用
> [onScrollStop](#onscrollstop)。
> 
> - 在多列联动场景中，不建议使用该回调。该回调标识的是滑动过程中选项进入分割线区域内的节点；跟随变化的选项并不涉及滑动，因此回调返回值中仅当
> 前滑动列的值会正常变化，其余未滑动列的值保持不变。
> 
> - 该接口不支持在attributeModifier中调用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [TextPickerEnterSelectedAreaCallback](arkts-arkui-textpickerenterselectedareacallback-t.md) | 是 | 滑动TextPicker过程中，选项进入分割线区域时触发的回调。 |

## onScrollStop

```TypeScript
onScrollStop(callback: TextPickerScrollStopCallback)
```

文本选择器的选项列滑动停止时触发该事件。手指拖动选项列触发的滑动，手指离开屏幕且滑动停止时会触发该事件。

> **说明：**
> 
> - 与[onEnterSelectedArea](#onenterselectedarea)事件的差别在于，onScrollStop关注的
> 是滚动行为完全停止，onEnterSelectedArea关注的是选项进入选中区域的逻辑状态。onEnterSelectedArea能更早响应索引变化，
> 适合实时反馈场景，建议使用[onEnterSelectedArea](#onenterselectedarea)；若需确认滚动行为完全停止，
> 则使用onScrollStop。
> 
> - 从API version 20开始，该接口支持在attributeModifier中调用。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [TextPickerScrollStopCallback](arkts-arkui-textpickerscrollstopcallback-t.md) | 是 | 文本选择器的选项列滑动停止时触发该事件。 |

## onScrollStop

```TypeScript
onScrollStop(callback: Optional<TextPickerScrollStopCallback>)
```

文本选择器的选项列滑动停止时触发该事件。与 [onScrollStop&lt;sup&gt;14+&lt;/sup&gt;](#onscrollstop)相比， callback参数新增了对undefined类型的支持。手指拖动选项列触发的滑动，手指离开屏幕且滑动停止时会触发该事件。

> **说明：**
> 
> - 与[onEnterSelectedArea](#onenterselectedarea)事件的差别在于，onScrollStop关注的是滚动行为完全
> 停止，onEnterSelectedArea关注的是选项进入选中区域的逻辑状态。onEnterSelectedArea能更早响应索引变化，适合实时反馈场景，建议使用
> [onEnterSelectedArea](#onenterselectedarea)；若需确认滚动行为完全停止，则使用onScrollStop。
> 
> - 从API version 20开始，该接口支持在attributeModifier中调用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;[TextPickerScrollStopCallback](arkts-arkui-textpickerscrollstopcallback-t.md)&gt; | 是 | 文本选择器的选项列滑动停止时触发该事件。 当callback的值为undefined时，不使用回调函数。 |

## selectedBackgroundStyle

```TypeScript
selectedBackgroundStyle(style: Optional<PickerBackgroundStyle>)
```

设置选中项的背景样式。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;[PickerBackgroundStyle](arkts-arkui-pickerbackgroundstyle-i.md)&gt; | 是 | 选中项背景的颜色和边框圆角半径， 多列模式时会同时设置所有列的选中项背景的颜色和圆角半径。 默认值： {color: \\$r('sys.color.comp_background_tertiary'), borderRadius: \\$r('sys.float.corner_radius_level12') } |

## selectedIndex

```TypeScript
selectedIndex(value: number | number[])
```

设置选中项在数据选择列表中的索引值，优先级高于[TextPickerOptions](arkts-arkui-textpickeroptions-i.md)中的"value"属性。单列数据选择器使用 number类型。多列数据选择器使用number[]类型。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| number[] | 是 | 选中项在数据选择列表中的索引值，索引从0开始。 默认值：0 当value的值为负数或者超过数据选择列表的最大索引值时，使用默认值。 |

## selectedIndex

```TypeScript
selectedIndex(index: Optional<number | number[]>)
```

设置选中项在数据选择列表中的索引值，优先级高于[TextPickerOptions](arkts-arkui-textpickeroptions-i.md)中的"value"属性。单列数据选择器使用 number类型，多列数据选择器使用number[]类型。与[selectedIndex&lt;sup&gt;10+&lt;/sup&gt;] [selectedIndex](#selectedindex)相比，index参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | [Optional](arkts-arkui-optional-t.md)&lt;number \| number[] & gt; | 是 | 选中项在数据选择列表中的索引值，索引从0开始。 默认值：0 当index的值为undefined时，使用[TextPickerOptions](arkts-arkui-textpickeroptions-i.md)中的selected值。 当index的值为负数或者超过数据选择列表的最大索引值时，使用默认值。 |

## selectedTextStyle

```TypeScript
selectedTextStyle(value: PickerTextStyle)
```

设置选中项的文本颜色、字号、字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-pickertextstyle-i.md) | 是 | 选中项的文本颜色、字号、字体粗细。 默认值： {color: '#ff007dff', font: {size: '20fp', weight: FontWeight.Medium } }    **说明：**未调用该方法设置样式时，使用默认值。 |

## selectedTextStyle

```TypeScript
selectedTextStyle(style: Optional<PickerTextStyle>)
```

设置选中项的文本颜色、字号、字体粗细。与 [selectedTextStyle&lt;sup&gt;10+&lt;/sup&gt;](#selectedtextstyle)相比，style参 数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-pickertextstyle-i.md)&gt; | 是 | 选中项的文本颜色、字号、字体粗细。 默认值： {color: '#ff007dff', font: {size: '20fp', weight: FontWeight.Medium } } 当style的值为undefined时，使用默认值。 |

## selectedTextStyle

```TypeScript
selectedTextStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>)
```

设置选中项的文本颜色、字号、字体粗细、最大字号、最小字号、超长文本截断方式。与 [selectedTextStyle&lt;sup&gt;18+&lt;/sup&gt;](#selectedtextstyle)相 比，style参数新增了对[TextPickerTextStyle](arkts-arkui-textpickertextstyle-i.md)类型的支持。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-pickertextstyle-i.md) \| [TextPickerTextStyle](arkts-arkui-textpickertextstyle-i.md)&gt; | 是 | 选中项的文本颜色、字号、字体粗细、最大字号、最小字号、超长 文本截断方式。 默认值： {color: '#ff007dff', font: {size: '20fp', weight: FontWeight.Medium }, minFontSize: 0, maxFontSize: 0, overflow: TextOverflow.Clip } 当style的值为undefined时，使用默认值。 |

## textStyle

```TypeScript
textStyle(value: PickerTextStyle)
```

设置待选项（以选中项为基准向上或向下的第一项）的文本颜色、字号、字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-pickertextstyle-i.md) | 是 | 待选项的文本颜色、字号、字体粗细。 默认值： {color: '#ff182431', font: {size: '16fp', weight: FontWeight.Regular } }    **说明：**未调用该方法设置样式时，使用默认值。 |

## textStyle

```TypeScript
textStyle(style: Optional<PickerTextStyle>)
```

设置待选项（以选中项为基准向上或向下的第一项）的文本颜色、字号、字体粗细。与 [textStyle&lt;sup&gt;10+&lt;/sup&gt;](#textstyle)相比，style参数新增了对undefined 类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-pickertextstyle-i.md)&gt; | 是 | 待选项的文本颜色、字号、字体粗细。 默认值： {color: '#ff182431', font: {size: '16fp', weight: FontWeight.Regular } } 当style的值为undefined时，使用默认值。 |

## textStyle

```TypeScript
textStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>)
```

设置待选项（以选中项为基准向上或向下的第一项）的文本颜色、字号、字体粗细、最大字号、最小字号、超长文本截断方式。与 [textStyle&lt;sup&gt;18+&lt;/sup&gt;](#textstyle)相比，style参数新增了 对[TextPickerTextStyle](arkts-arkui-textpickertextstyle-i.md)类型的支持。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-pickertextstyle-i.md) \| [TextPickerTextStyle](arkts-arkui-textpickertextstyle-i.md)&gt; | 是 | 待选项的文本颜色、字号、字体粗细、最大字号、最小字号、超长 文本截断方式。 默认值： {color: '#ff182431', font: {size: '16fp', weight: FontWeight.Regular }, minFontSize: 0, maxFontSize: 0, overflow: TextOverflow.Clip } 当style的值为undefined时，使用默认值。 |
