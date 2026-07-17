# SheetOptions

继承自[BindOptions](arkts-arkui-common-bindoptions-i.md)。

半模态页面内容选项。

**继承/实现关系：** SheetOptions extends [BindOptions](arkts-arkui-common-bindoptions-i.md)

**起始版本：** 10

<!--Device-unnamed-declare interface SheetOptions extends BindOptions--><!--Device-unnamed-declare interface SheetOptions extends BindOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## blurStyle

```TypeScript
blurStyle?: BlurStyle
```

半模态面板的模糊背景。默认无模糊背景。

**类型：** BlurStyle

**默认值：** BlurStyle.NONE

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-blurStyle?: BlurStyle--><!--Device-SheetOptions-blurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ResourceColor | EdgeColors | LocalizedEdgeColors
```

设置半模态页面的边框颜色。

默认值：Color.Black

如果使用borderColor属性，需要和borderWidth属性一起使用。

**说明：**

底部弹窗时，底部边框颜色设置无效。

**类型：** ResourceColor | EdgeColors | LocalizedEdgeColors

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-borderColor?: ResourceColor | EdgeColors | LocalizedEdgeColors--><!--Device-SheetOptions-borderColor?: ResourceColor | EdgeColors | LocalizedEdgeColors-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderStyle

```TypeScript
borderStyle?: BorderStyle | EdgeStyles
```

设置半模态页面的边框样式。

默认值：BorderStyle.Solid

如果使用borderStyle属性，需要和borderWidth属性一起使用。

**说明：**

底部弹窗时，底部边框样式设置无效。

**类型：** BorderStyle | EdgeStyles

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-borderStyle?: BorderStyle | EdgeStyles--><!--Device-SheetOptions-borderStyle?: BorderStyle | EdgeStyles-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Dimension | EdgeWidths | LocalizedEdgeWidths
```

设置半模态页面的边框宽度。

可分别设置4个边框宽度。

默认值：0

百分比参数方式：以父元素半模态页面宽的百分比来设置半模态页面的边框宽度。

当半模态页面左边框和右边框大于半模态页面宽度，半模态页面上边框和下边框大于半模态页面高度，显示可能不符合预期。

**说明：**

底部弹窗时，底部边框宽度设置无效。

**类型：** Dimension | EdgeWidths | LocalizedEdgeWidths

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-borderWidth?: Dimension | EdgeWidths | LocalizedEdgeWidths--><!--Device-SheetOptions-borderWidth?: Dimension | EdgeWidths | LocalizedEdgeWidths-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## detentSelection

```TypeScript
detentSelection?: SheetSize | Length
```

支持非手势切换挡位。

**默认值：** detents[0]。

**说明：**

1. 该接口取值范围为detents数组范围，若设值非detents范围，该接口无效。2. 当设置SheetSize.FIT_CONTENT时，该接口无效。3. 不建议手势切换挡位与该接口切换挡位同时生效使用。

**类型：** SheetSize | Length

**默认值：** detents[0]

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-detentSelection?: SheetSize | Length--><!--Device-SheetOptions-detentSelection?: SheetSize | Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## detents

```TypeScript
detents?: [(SheetSize | Length), (SheetSize | Length)?, (SheetSize | Length)?]
```

半模态页面的切换高度挡位。

**说明：**

从API version 12开始，底部弹窗横屏时该属性设置生效。

底部弹窗竖屏生效，元组中第一个高度为初始高度。

面板可跟手滑动切换挡位，松手后是否滑动至目标挡位有两个判断条件：速度和距离。速度超过阈值，则执行滑动至与手速方向一致的目标挡位；速度小于阈值，则引入距离判断条件，当位移距离>当前位置与目标位置的1/2，滑动至与手速方向一致的目标挡位，位移距离当前位置与目标位置的1/2，返回至当前挡位。速度阈值：1000，距离阈值：50%。

**类型：** [(SheetSize | Length), (SheetSize | Length)?, (SheetSize | Length)?]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-detents?: [(SheetSize | Length), (SheetSize | Length)?, (SheetSize | Length)?]--><!--Device-SheetOptions-detents?: [(SheetSize | Length), (SheetSize | Length)?, (SheetSize | Length)?]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dragBar

```TypeScript
dragBar?: boolean
```

是否显示控制条。

默认值：true

true：显示控制条。

false：不显示控制条。

**说明：**

半模态面板的detents属性设置多个不同高度并且设置生效时，默认显示控制条。否则不显示控制条。

**类型：** boolean

**默认值：** true

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-dragBar?: boolean--><!--Device-SheetOptions-dragBar?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## effectEdge

```TypeScript
effectEdge?: number
```

设置半模态面板内容区边缘回弹效果，支持单边生效。

**默认值**：默认双边生效，即[EffectEdge](arkts-arkui-common-effectedge-e.md).START | [EffectEdge](arkts-arkui-common-effectedge-e.md).END（即数值3）。

**说明：**

1. 仅上边缘生效：[EffectEdge](arkts-arkui-common-effectedge-e.md).START。2. 仅下边缘生效：[EffectEdge](arkts-arkui-common-effectedge-e.md).END。3. 双边生效：[EffectEdge](arkts-arkui-common-effectedge-e.md).START | [EffectEdge](arkts-arkui-common-effectedge-e.md).END（即数值3）。4. 双边不生效：[EffectEdge](arkts-arkui-common-effectedge-e.md).START & [EffectEdge](arkts-arkui-common-effectedge-e.md).END（即数值0）。

**类型：** number

**默认值：** 3

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-effectEdge?: number--><!--Device-SheetOptions-effectEdge?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableFloatingDragBar

```TypeScript
enableFloatingDragBar?: boolean
```

控制条是否悬浮显示，true为悬浮显示，false为不悬浮显示。

默认值：false

**说明：**

悬浮效果只在控制条显示的场景生效，且控制条不占位。

title传入[CustomBuilder](../../../../reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8)时enableFloatingDragBar始终为false。

**类型：** boolean

**默认值：** false

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-enableFloatingDragBar?: boolean--><!--Device-SheetOptions-enableFloatingDragBar?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

是否响应悬停态。

默认值：false，默认不响应。

2in1设备默认值：true

true：响应悬停态。

false：不响应悬停态。

**说明：**

底部弹窗样式和跟手弹窗样式不响应悬停态。子窗模式不支持悬停态。

**类型：** boolean

**默认值：** false

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-enableHoverMode?: boolean--><!--Device-SheetOptions-enableHoverMode?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableOutsideInteractive

```TypeScript
enableOutsideInteractive?: boolean
```

半模态页面显示时，其下层页面是否允许交互。

**说明：**

设置为true时允许交互，不显示蒙层；设置为false时不允许交互，显示蒙层；若不进行设置，默认底部弹窗与居中弹窗不允许交互，跟手弹窗允许交互。当设置为true时，maskColor设置无效。

**类型：** boolean

**默认值：** false

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-enableOutsideInteractive?: boolean--><!--Device-SheetOptions-enableOutsideInteractive?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: SheetSize | Length
```

半模态高度，默认是LARGE。

**说明：**

1. API version 14开始，底部弹窗横屏时，无状态栏则最大高度为距离屏幕顶部8vp，有状态栏则最大高度为距离状态栏8vp。2. 底部弹窗时，当设置detents时，该属性设置无效。3. 底部弹窗竖屏时，最大高度为距离状态栏8vp。4. 居中弹窗和跟手弹窗设置类型为SheetSize.LARGE和SheetSize.MEDIUM无效，显示默认高度560vp。5. 居中弹窗和跟手弹窗最小高度为320vp，最大高度为窗口短边的90%。6. 居中弹窗和跟手弹窗当使用Length设置的高度时，高度大于最大高度，则显示最大高度，小于最小高度，则显示最小高度。7. 如果半模态使用SheetSize.FIT_CONTENT自适应模式，且类型设置为居中弹窗或跟手弹窗，API version 22及之前版本，高度大于最大高度时显示最大高度，高度小于最小高度时显示最小高度。从API version 23开始，高度大于最大高度时显示最大高度，高度小于最小高度时按照实际自适应高度生效。

**类型：** SheetSize | Length

**默认值：** SheetSize.LARGE

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-height?: SheetSize | Length--><!--Device-SheetOptions-height?: SheetSize | Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

悬停态下弹窗默认展示区域。

默认值：HoverModeAreaType.BOTTOM_SCREEN

2in1设备默认值：HoverModeAreaType.TOP_SCREEN

**类型：** HoverModeAreaType

**默认值：** HoverModeAreaType.BOTTOM_SCREEN

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-hoverModeArea?: HoverModeAreaType--><!--Device-SheetOptions-hoverModeArea?: HoverModeAreaType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode?: SheetKeyboardAvoidMode
```

设置半模态激活输入法时对软键盘的避让方式。

**默认值：** TRANSLATE_AND_SCROLL

**类型：** SheetKeyboardAvoidMode

**默认值：** SheetKeyboardAvoidMode.TRANSLATE_AND_SCROLL

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-keyboardAvoidMode?: SheetKeyboardAvoidMode--><!--Device-SheetOptions-keyboardAvoidMode?: SheetKeyboardAvoidMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskColor

```TypeScript
maskColor?: ResourceColor
```

半模态页面的背景蒙层颜色。

默认值：$r('sys.color.ohos_id_color_mask_thin')。

**类型：** ResourceColor

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-maskColor?: ResourceColor--><!--Device-SheetOptions-maskColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## modalTransition

```TypeScript
modalTransition?: ModalTransition
```

bindSheet全屏模态样式的系统转场方式。

默认值：ModalTransition.DEFAULT

**类型：** ModalTransition

**默认值：** ModalTransition.DEFAULT

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-modalTransition?: ModalTransition--><!--Device-SheetOptions-modalTransition?: ModalTransition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: SheetMode
```

设置半模态页面的显示层级。

默认值：SheetMode.OVERLAY

**说明：**

1. 半模态显示期间mode属性不支持动态切换，两种模式的显示层级完全不同，无法做到显示期间同一个半模态从一个层级变换到另一个层级。建议在使用时明确诉求固定mode值。2. 设置SheetMode.EMBEDDED时不支持设置UIContext属性，两者对应的半模态显示层级效果互相冲突。3. 使用[openBindSheet](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#openbindsheet12)启动半模态页面，若未传入有效的targetId，则不支持设置为SheetMode.EMBEDDED，默认为SheetMode.OVERLAY。

**类型：** SheetMode

**默认值：** SheetMode.OVERLAY

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-mode?: SheetMode--><!--Device-SheetOptions-mode?: SheetMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDetentsDidChange

```TypeScript
onDetentsDidChange?: Callback<number>
```

半模态页面挡位变化回调函数。

**说明：**

底部弹窗时，挡位变化返回最后的高度。

返回值为px。

**类型：** Callback<number>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-onDetentsDidChange?: Callback<number>--><!--Device-SheetOptions-onDetentsDidChange?: Callback<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHeightDidChange

```TypeScript
onHeightDidChange?: Callback<number>
```

半模态页面高度变化回调函数。

**说明：**

底部弹窗时，只有挡位变化和拖拽跟手才返回每一帧高度，拉起半模态和避让软键盘只返回最后的高度，其他弹窗只在半模态拉起返回最后高度。

返回值为px。

**类型：** Callback<number>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-onHeightDidChange?: Callback<number>--><!--Device-SheetOptions-onHeightDidChange?: Callback<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTypeDidChange

```TypeScript
onTypeDidChange?: Callback<SheetType>
```

半模态页面形态变化回调函数。

**说明：**

形态变化时返回最后的形态。

**类型：** Callback<SheetType>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-onTypeDidChange?: Callback<SheetType>--><!--Device-SheetOptions-onTypeDidChange?: Callback<SheetType>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWidthDidChange

```TypeScript
onWidthDidChange?: Callback<number>
```

半模态页面宽度变化回调函数。

**说明：**

宽度变化时返回最后的宽度。

返回值为px。

**类型：** Callback<number>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-onWidthDidChange?: Callback<number>--><!--Device-SheetOptions-onWidthDidChange?: Callback<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: Callback<DismissSheetAction>
```

半模态页面的交互式关闭回调函数。允许开发者注册，以获取关闭操作的类型，并决定是否关闭半模态状态。

**说明：**

当用户执行下拉关闭、侧拉关闭、点击遮罩层关闭、点击关闭按钮的交互操作时，若已注册回调函数，则不会立即关闭页面，而是由开发者通过回调函数[DismissSheetAction](arkts-arkui-common-dismisssheetaction-i.md)中的reason参数判断关闭操作的类型，进而根据具体原因自主选择是否关闭半模态页面。

如果不注册该回调函数，则用户执行关闭操作时，正常关闭半模态，无其他行为。

侧拉关闭又包含侧滑（左滑/右滑）、三键back、键盘ESC关闭。

在onWillDismiss回调中，不能再做onWillDismiss拦截。

建议在[二次确认](../../../../ui/arkts-sheet-page.md#二次确认能力)场景使用。

**类型：** Callback<DismissSheetAction>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-onWillDismiss?: Callback<DismissSheetAction>--><!--Device-SheetOptions-onWillDismiss?: Callback<DismissSheetAction>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillSpringBackWhenDismiss

```TypeScript
onWillSpringBackWhenDismiss?: Callback<SpringBackAction>
```

半模态页面交互式关闭前控制回弹函数。允许开发者注册，以控制半模态页面交互式关闭时的回弹效果。

**说明：**

当用户触发执行下拉关闭操作并同时注册该回调函数与shouldDismiss或onWillDismiss时，由开发者控制下滑关闭时是否回弹。在回调函数中可以通过调用springBack来实现回弹效果。也可以通过不调用springBack来取消回弹效果。

若不注册该回调函数，但注册shouldDismiss或onWillDismiss时，则默认在下拉关闭时，会触发回弹效果，回弹后再根据shouldDismiss或onWillDismiss内的回调行为决定半模态是否关闭。

如果不注册该回调函数，且未注册shouldDismiss或onWillDismiss时，默认在下滑关闭时，触发半模态关闭。

侧边弹窗样式则是在侧拉关闭场景生效springBack。

**类型：** Callback<SpringBackAction>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-onWillSpringBackWhenDismiss?: Callback<SpringBackAction>--><!--Device-SheetOptions-onWillSpringBackWhenDismiss?: Callback<SpringBackAction>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placement

```TypeScript
placement?: Placement
```

设置半模态popup样式弹窗相对于目标的显示位置。

默认值：Placement.Bottom

**说明：**

1. popup样式弹窗在确保指定位置能容纳弹窗尺寸的前提下，优先依据设定的placement展示弹窗。若不可行，则遵循先垂直翻转，后尝试90°水平旋转的规则调整显示位置，以预设方向为下方为例，调整顺序依次为：下、上、右、左。2. 如果设置的对齐方式导致组件布局超出窗口范围，将根据该对齐方式在水平或垂直方向上进行位移，直至组件完全显示在窗口内。3. 如果在四个方向上均无法容纳当前的popup样式弹窗，处理方式遵循开发者设置的placementOnTarget属性：

1）若属性值为true，将依据设定的placement，向其镜像方向平移，直至弹窗能够完全显示。

2）若属性值为false，则在四个方向中，选择能够完全展示弹窗宽度且剩余高度最大的方向，通过调整半模态高度以适应当前方向，确保弹窗能够放下，同时保持预设placement对应的对齐方式不变。

**类型：** Placement

**默认值：** Placement.Bottom

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-placement?: Placement--><!--Device-SheetOptions-placement?: Placement-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placementOnTarget

```TypeScript
placementOnTarget?: boolean
```

半模态popup样式弹窗在当前窗口下，四个方向均无法容纳该弹窗大小时，设置是否允许其覆盖在目标节点上。

默认值：true

true：允许其覆盖在目标节点上。

false：不允许其覆盖在目标节点上。

**类型：** boolean

**默认值：** true

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-placementOnTarget?: boolean--><!--Device-SheetOptions-placementOnTarget?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## preferType

```TypeScript
preferType?: SheetType
```

半模态页面的样式。

**说明：**

半模态在不同窗口所支持的显示类型：

1. 宽度 < 600vp：底部、全屏。默认底部样式。2. 600vp <= 宽度 < 840vp：底部、居中、跟手、侧边、全屏。默认居中样式。3. 宽度 >= 840vp：底部、居中、跟手、侧边、全屏。默认跟手样式。4. API version 20开始，窗口宽度大于600vp时，preferType支持设置为SheetType.SIDE。5. API version 20开始，preferType支持设置为SheetType.CONTENT_COVER，支持设置为全屏模态样式。

**类型：** SheetType

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-preferType?: SheetType--><!--Device-SheetOptions-preferType?: SheetType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses
```

设置半模态页面圆角半径。

不建议设置4个圆角大小不相等，圆角大小相等时面板视觉体验最佳。

**默认值**：32vp

**说明：**

1. 根据设置的圆角半径值显示，如果未设置，则使用默认值。底部样式不显示半模态底部2个圆角，即使设置了底部2个圆角也不生效。2. 分别设置4个方向的圆角半径后，如果某个方向的值异常，异常方向的圆角值重置为默认值，非异常方向的圆角值为已设置的值。统一设置4个方向的圆角时，如果设置的值异常，4个方向的圆角都重置为默认值。3. 半径设置为百分比时，以半模态页面的宽度为基准。4. 当圆角的半径大于半模态页面宽度一半时，圆角的半径取值为半模态页面宽度的一半。5. 当半模态页面高度过小且圆角半径设置过大时，可能导致显示异常。

**类型：** LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-radius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses--><!--Device-SheetOptions-radius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radiusRenderStrategy

```TypeScript
radiusRenderStrategy?: RenderStrategy
```

设置组件绘制圆角的模式。

默认值：RenderStrategy.FAST

**说明**: 当半模态设置模糊时，可通过设置为OFFSCREEN离屏模式解决半模态顶部或顶部圆角区域内显示效果异常问题。popup样式不支持设置组件绘制圆角模式。

**类型：** RenderStrategy

**默认值：** RenderStrategy.FAST

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-radiusRenderStrategy?: RenderStrategy--><!--Device-SheetOptions-radiusRenderStrategy?: RenderStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scrollSizeMode

```TypeScript
scrollSizeMode?: ScrollSizeMode
```

设置半模态面板滑动时，内容区域刷新时机。

默认值：ScrollSizeMode.FOLLOW_DETENT

**类型：** ScrollSizeMode

**默认值：** ScrollSizeMode.FELLOW_DETEND

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-scrollSizeMode?: ScrollSizeMode--><!--Device-SheetOptions-scrollSizeMode?: ScrollSizeMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

设置半模态页面的阴影。

2in1设备默认值：ShadowStyle.OUTER_FLOATING_SM。

**类型：** ShadowOptions | ShadowStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-SheetOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shouldDismiss

```TypeScript
shouldDismiss?: (sheetDismiss: SheetDismiss) => void
```

半模态页面交互式关闭回调函数。

**说明：**

当用户执行下拉关闭、侧拉关闭、点击遮罩层关闭、点击关闭按钮的交互操作时，如果已注册回调函数，模态窗口将不会立即关闭。要关闭半模态，需在回调函数中调用shouldDismiss.dismiss()方法来实现。

如果不注册该回调函数，则用户执行下拉关闭、侧拉关闭、点击遮罩层关闭、点击关闭按钮的交互操作时，正常关闭半模态，无其他行为。

侧拉关闭又包含侧滑（左滑/右滑）、三键back、键盘ESC关闭。

建议在[二次确认](../../../../ui/arkts-sheet-page.md#二次确认能力)场景使用。

**类型：** (sheetDismiss: SheetDismiss) => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-shouldDismiss?: (sheetDismiss: SheetDismiss) => void--><!--Device-SheetOptions-shouldDismiss?: (sheetDismiss: SheetDismiss) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showClose

```TypeScript
showClose?: boolean | Resource
```

是否显示关闭图标。

2in1设备默认无按钮底板。

默认值：true。

true：显示关闭图标。

false：不显示关闭图标。

**说明：**

Resource需要为boolean类型。

**类型：** boolean | Resource

**默认值：** true

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-showClose?: boolean | Resource--><!--Device-SheetOptions-showClose?: boolean | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

半模态是否在独立子窗中显示。

默认值：false

**说明：**

1. 若属性值为true，半模态可以在独立子窗口中展示，并且可以超过应用窗口范围。2. 若属性值为false，半模态只能在应用窗口范围内展示。3. 不建议在showInSubWindow为true的弹窗嵌套显示另一个showInSubWindow为true的弹窗，半模态可能会影响其他组件行为。4. 不建议在showInSubWindow为true的弹窗中使用CalendarPicker、CalendarPickerDialog、DatePickerDialog、TextPickerDialog、TimePickerDialog等picker组件，半模态会影响上述组件行为。5. 半模态显示期间该属性不支持动态切换。

**类型：** boolean

**默认值：** false

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-showInSubWindow?: boolean--><!--Device-SheetOptions-showInSubWindow?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

设置组件的系统材质。

默认值：undefined，会清除由该接口设置的材质效果。

**说明**: 不同系统材质对应不同的属性影响效果，该接口影响背景色[backgroundColor](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor)、边框颜色[borderColor](arkts-arkui-common-commonmethod-c.md#bordercolor-1)、边框宽度[borderWidth](arkts-arkui-common-commonmethod-c.md#borderwidth-1)、阴影[shadow](arkts-arkui-common-commonmethod-c.md#shadow-1)，不建议与上述接口一起使用。使用示例请参考[示例10（半模态设置系统材质）](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md#示例10半模态设置系统材质)。

**类型：** SystemUiMaterial

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-systemMaterial?: SystemUiMaterial--><!--Device-SheetOptions-systemMaterial?: SystemUiMaterial-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: SheetTitleOptions | CustomBuilder
```

半模态面板的标题。

**类型：** SheetTitleOptions | CustomBuilder

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-title?: SheetTitleOptions | CustomBuilder--><!--Device-SheetOptions-title?: SheetTitleOptions | CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## uiContext

```TypeScript
uiContext?: UIContext
```

在UIContext实例对应的窗口中显示半模态。

**说明：**

使用[openBindSheet](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#openbindsheet12)启动的半模态页面，不支持设置、更新该属性。

**类型：** UIContext

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-uiContext?: UIContext--><!--Device-SheetOptions-uiContext?: UIContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

设置半模态页面的宽度。

百分比参数方式：以父元素宽的百分比来设置半模态页面的宽度。

**类型：** Dimension

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetOptions-width?: Dimension--><!--Device-SheetOptions-width?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

