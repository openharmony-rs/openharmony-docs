# CustomDialogControllerOptions

自定义弹窗的样式。

> **说明：**  
>  
> - 按下返回键和ESC键时会让弹窗退出。  
>  
> - 弹窗在避让软键盘时到达极限高度之后会压缩高度。  
> > 需要注意：高度压缩生效在外层容器上，如果容器根节点中的子组件设置了较大的固定高度，由于容器默认不裁剪，依然可能存在超出屏幕显示的情况。  
>  
> - 自定义弹窗仅适用于简单提示场景，不能替代页面使用。弹窗避让软键盘时，与软键盘之间存在16vp的安全间距。  
>  
> - 为了达成良好的视觉体验，弹窗的显示和关闭存在默认动画，动画时长不同设备间可能存在差异。  
> > 需要注意：在动画播放过程中，页面不响应触摸、滑动、点击操作。关闭默认弹窗动画效果可设置openAnimation和closeAnimation的duration为0。  
>  
> - 当前，ArkUI弹出框默认为非页面级弹出框，在页面路由跳转时，如果开发者未调用close方法将其关闭，弹出框将不会自动关闭。若需实现在跳转页面时覆盖弹出框的场景，可以使用  
> [组件导航子页面显示类型的弹窗类型](../../../../ui/arkts-navigation-navdestination.md#页面显示类型)或者  
> [页面级弹出框](../../../../ui/arkts-embedded-dialog.md)。

**起始版本：** 7

<!--Device-unnamed-declare interface CustomDialogControllerOptions--><!--Device-unnamed-declare interface CustomDialogControllerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: DialogAlignment
```

弹窗在竖直方向上的对齐方式。

默认值：DialogAlignment.Default

**类型：** DialogAlignment

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-alignment?: DialogAlignment--><!--Device-CustomDialogControllerOptions-alignment?: DialogAlignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoCancel

```TypeScript
autoCancel?: boolean
```

是否允许点击遮障层退出，true表示关闭弹窗。false表示不关闭弹窗。

默认值：true

**类型：** boolean

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-autoCancel?: boolean--><!--Device-CustomDialogControllerOptions-autoCancel?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

弹窗背板模糊材质。

默认值：从API版本26.0.0开始，为BlurStyle.NONE，API版本26.0.0之前，为BlurStyle.COMPONENT_ULTRA_THICK。

**说明：**

设置为BlurStyle.NONE即可关闭背景虚化。当设置了backgroundBlurStyle为非NONE值时，则不要设置backgroundColor，否则颜色显示将不符合预期效果。

**类型：** BlurStyle

**默认值：** BlurStyle.COMPONENT_ULTRA_THICK

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-backgroundBlurStyle?: BlurStyle--><!--Device-CustomDialogControllerOptions-backgroundBlurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

背景模糊效果。默认值请参考BackgroundBlurStyleOptions类型说明。

**类型：** BackgroundBlurStyleOptions

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-CustomDialogControllerOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

设置弹窗背板填充。

默认值：Color.Transparent

**说明：** 如果同时设置了内容构造器的背景色，则backgroundColor会被内容构造器的背景色覆盖。

backgroundColor会与模糊属性backgroundBlurStyle叠加产生效果，如果不符合预期，可将backgroundBlurStyle设置为BlurStyle.NONE，即可取消模糊。

**类型：** ResourceColor

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-backgroundColor?: ResourceColor--><!--Device-CustomDialogControllerOptions-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

背景效果参数。默认值请参考BackgroundEffectOptions类型说明。

**类型：** BackgroundEffectOptions

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-CustomDialogControllerOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ResourceColor | EdgeColors
```

设置弹窗背板的边框颜色。

默认值：Color.Black

如果使用borderColor属性，需要和borderWidth属性一起使用。

**类型：** ResourceColor | EdgeColors

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-borderColor?: ResourceColor | EdgeColors--><!--Device-CustomDialogControllerOptions-borderColor?: ResourceColor | EdgeColors-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderStyle

```TypeScript
borderStyle?: BorderStyle | EdgeStyles
```

设置弹窗背板的边框样式。

默认值：BorderStyle.Solid

如果使用borderStyle属性，需要和borderWidth属性一起使用。

**类型：** BorderStyle | EdgeStyles

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-borderStyle?: BorderStyle | EdgeStyles--><!--Device-CustomDialogControllerOptions-borderStyle?: BorderStyle | EdgeStyles-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Dimension | EdgeWidths
```

设置弹窗背板的边框宽度。

可分别设置4个边框宽度。

默认值：0。

百分比参数方式：以父元素弹窗宽的百分比来设置弹窗的边框宽度。

当弹窗左边框和右边框大于弹窗宽度，弹窗上边框和下边框大于弹窗高度，显示可能不符合预期。

**类型：** Dimension | EdgeWidths

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-borderWidth?: Dimension | EdgeWidths--><!--Device-CustomDialogControllerOptions-borderWidth?: Dimension | EdgeWidths-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder: any
```

自定义弹窗内容构造器。

**说明：**

若builder构造器使用回调函数作为入参，请注意使用this绑定问题，如builder: custombuilder({ callback: ()=> {...}})。

若在builder中监听数据变化可以使用@Link或@Consume，而其他方式如@Prop、@ObjectLink不适用此场景。

**类型：** any

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-builder: any--><!--Device-CustomDialogControllerOptions-builder: any-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cancel

```TypeScript
cancel?: () => void
```

返回、ESC键和点击遮障层弹窗退出时的回调。

**类型：** () => void

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-cancel?: () => void--><!--Device-CustomDialogControllerOptions-cancel?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeAnimation

```TypeScript
closeAnimation?: AnimateParam
```

自定义设置弹窗关闭的动画效果相关参数。

**说明**：

tempo默认值为1，当设置小于等于0的值时按默认值处理。

iterations默认值为1，默认播放一次，设置为其他数值时按默认值处理。

playMode控制动画播放模式，默认值为PlayMode.Normal，设置为其他数值时按照默认值处理。

页面转场切换时，建议使用默认关闭动效。

**类型：** AnimateParam

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-closeAnimation?: AnimateParam--><!--Device-CustomDialogControllerOptions-closeAnimation?: AnimateParam-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cornerRadius

```TypeScript
cornerRadius?: Dimension | BorderRadiuses
```

设置背板的圆角半径。

可分别设置4个圆角的半径。

默认值：{ topLeft: '32vp', topRight: '32vp', bottomLeft: '32vp', bottomRight: '32vp' }

**说明**：自定义弹窗默认的背板圆角半径为32vp，如果需要使用cornerRadius属性，请和[borderRadius](../arkts-components/arkts-arkui-common-commonmethod-c.md#borderradius-1)属性一起使用。

**类型：** Dimension | BorderRadiuses

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-cornerRadius?: Dimension | BorderRadiuses--><!--Device-CustomDialogControllerOptions-cornerRadius?: Dimension | BorderRadiuses-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## customStyle

```TypeScript
customStyle?: boolean
```

弹窗容器样式是否自定义。值为true表示弹窗容器样式不能自定义，值为false表示弹窗容器样式能自定义。

默认值：false

设置为false时：

1. 默认圆角为32vp。2. 未设置弹窗宽度高度：弹窗容器的宽度根据栅格系统自适应。高度自适应自定义的内容节点。3. 设置弹窗宽度高度：弹窗容器的宽度不超过默认样式下的最大宽度（自定义节点设置100%的宽度），弹窗容器的高度不超过默认样式下的最大高度（自定义节点设置100%的高度）。4. 受安全区域的影响，弹窗显示区域将排除安全区域。例如在PC/2in1设备上避让屏幕边缘以及窗口标题栏。

设置为true时：

1. 圆角为0，弹窗背景色为透明色。2. 不支持设置弹窗宽度、高度、边框宽度、边框样式、边框颜色以及阴影宽度。3. 弹窗显示区域为屏幕。

**类型：** boolean

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-customStyle?: boolean--><!--Device-CustomDialogControllerOptions-customStyle?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayModeInSubWindow

```TypeScript
displayModeInSubWindow?: DialogDisplayMode
```

弹窗在子窗口中的显示模式。

默认值：DialogDisplayMode.SCREEN_BASED

**说明**：

仅当showInSubWindow设置为true时生效。

**类型：** DialogDisplayMode

**默认值：** DialogDisplayMode.SCREEN_BASED

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-displayModeInSubWindow?: DialogDisplayMode--><!--Device-CustomDialogControllerOptions-displayModeInSubWindow?: DialogDisplayMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

是否响应悬停态，值为true时，响应悬停态。

默认值：false，默认不响应。

**说明：**

PC/2in1设备弹窗默认显示在上半屏，在enableHoverMode设置为true时，可以通过设置hoverModeArea参数显示在下半屏。其他设备弹窗在enableHoverMode设置为true时默认显示在下半屏，可以通过设置hoverModeArea参数显示在上半屏。

**类型：** boolean

**默认值：** false

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-enableHoverMode?: boolean--><!--Device-CustomDialogControllerOptions-enableHoverMode?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## focusable

```TypeScript
focusable?: boolean
```

设置弹窗是否获取焦点。值为true表示获取焦点，值为false表示不获取焦点。

默认值：true

**说明：**

只有弹出覆盖在当前窗口之上的弹窗才可以获取焦点。

**类型：** boolean

**默认值：** true

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-focusable?: boolean--><!--Device-CustomDialogControllerOptions-focusable?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## gridCount

```TypeScript
gridCount?: number
```

弹窗宽度占[栅格宽度](../../../../ui/arkts-layout-development-grid-layout.md)的个数。

默认为按照窗口大小自适应，异常值按默认值处理，最大栅格数为系统最大栅格数。

取值范围：大于等于0的整数。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-gridCount?: number--><!--Device-CustomDialogControllerOptions-gridCount?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Dimension
```

设置弹窗背板的高度。

**说明：**

- 弹窗高度默认最大值：0.9 *（窗口高度 - 安全区域）。  
- 百分比参数方式：弹窗参考高度为（窗口高度 - 安全区域），在此基础上调小或调大。

**类型：** Dimension

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-height?: Dimension--><!--Device-CustomDialogControllerOptions-height?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

悬停态下弹窗默认展示区域。

默认值：HoverModeAreaType.BOTTOM_SCREEN。

**类型：** HoverModeAreaType

**默认值：** HoverModeAreaType.BOTTOM_SCREEN

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-hoverModeArea?: HoverModeAreaType--><!--Device-CustomDialogControllerOptions-hoverModeArea?: HoverModeAreaType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## immersiveMode

```TypeScript
immersiveMode?: ImmersiveMode
```

设置页面内弹窗蒙层效果。

**说明：**

- 默认值：ImmersiveMode.DEFAULT  
- 当且仅当levelMode属性设置为LevelMode.EMBEDDED时生效。

**类型：** ImmersiveMode

**默认值：** ImmersiveMode.DEFAULT

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-immersiveMode?: ImmersiveMode--><!--Device-CustomDialogControllerOptions-immersiveMode?: ImmersiveMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isModal

```TypeScript
isModal?: boolean
```

弹窗是否为模态窗口。值为true表示为模态窗口且有蒙层，不可与弹窗周围其他控件进行交互，即蒙层区域无法事件透传。值为false表示为非模态窗口且无蒙层，可以与弹窗周围其他控件进行交互。

默认值：true

**类型：** boolean

**默认值：** true

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-isModal?: boolean--><!--Device-CustomDialogControllerOptions-isModal?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidDistance

```TypeScript
keyboardAvoidDistance?: LengthMetrics
```

弹窗避让键盘后，和键盘之间的距离。

**说明：**

- 默认值：16vp。  
- 默认单位：vp。  
- 当且仅当keyboardAvoidMode属性设置为DEFAULT时生效。

**类型：** LengthMetrics

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-keyboardAvoidDistance?: LengthMetrics--><!--Device-CustomDialogControllerOptions-keyboardAvoidDistance?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode?: KeyboardAvoidMode
```

用于设置弹窗是否在拉起软键盘时进行自动避让。

默认值：KeyboardAvoidMode.DEFAULT

**类型：** KeyboardAvoidMode

**默认值：** KeyboardAvoidMode.DEFAULT

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-keyboardAvoidMode?: KeyboardAvoidMode--><!--Device-CustomDialogControllerOptions-keyboardAvoidMode?: KeyboardAvoidMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelMode

```TypeScript
levelMode?: LevelMode
```

设置弹窗显示层级。

**说明：**

- 默认值：LevelMode.OVERLAY。  
- 当且仅当showInSubWindow属性设置为false时生效。

**类型：** LevelMode

**默认值：** LevelMode.OVERLAY

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-levelMode?: LevelMode--><!--Device-CustomDialogControllerOptions-levelMode?: LevelMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelOrder

```TypeScript
levelOrder?: LevelOrder
```

设置弹窗显示的顺序。

**说明：**

- 默认值：LevelOrder.clamp(0)  
- 不支持动态刷新顺序。

**类型：** LevelOrder

**默认值：** The value returns by LevelOrder.clamp(0)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-levelOrder?: LevelOrder--><!--Device-CustomDialogControllerOptions-levelOrder?: LevelOrder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelUniqueId

```TypeScript
levelUniqueId?: number
```

设置页面级弹窗需要显示的层级下的节点UniqueID，UniqueID可以通过[getUniqueId](arkts-arkui-framenode-c.md#getuniqueid-1)获取。

取值范围：大于等于0的数字。

**说明：**

- 当且仅当levelMode属性设置为LevelMode.EMBEDDED时生效。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-levelUniqueId?: number--><!--Device-CustomDialogControllerOptions-levelUniqueId?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskColor

```TypeScript
maskColor?: ResourceColor
```

自定义蒙层颜色。

默认值：0x33000000

**类型：** ResourceColor

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-maskColor?: ResourceColor--><!--Device-CustomDialogControllerOptions-maskColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

弹窗遮蔽层区域，在遮蔽层区域内的事件不透传，在遮蔽层区域外的事件透传。

默认值：{ x: 0, y: 0, width: '100%', height: '100%' }

**说明：**

showInSubWindow为true时，maskRect不生效。

**类型：** Rectangle

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-maskRect?: Rectangle--><!--Device-CustomDialogControllerOptions-maskRect?: Rectangle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

弹窗相对alignment所在位置的偏移量。

默认值：{ dx: 0, dy: 0 }

**类型：** Offset

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-offset?: Offset--><!--Device-CustomDialogControllerOptions-offset?: Offset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: Callback<void>
```

弹窗弹出后的事件回调。

**说明：**

1.正常时序依次为：onWillAppear>>onDidAppear>>onWillDisappear>>onDidDisappear。

2.在onDidAppear内设置改变弹窗显示效果的回调事件，二次弹出生效。

3.快速点击弹出，关闭弹窗时，onWillDisappear在onDidAppear前生效。

4.弹窗入场动效未完成时彻底关闭弹窗，动效打断，onDidAppear不会触发。

**类型：** Callback<void>

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-onDidAppear?: Callback<void>--><!--Device-CustomDialogControllerOptions-onDidAppear?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: Callback<void>
```

弹窗消失后的事件回调。

**说明：**

1.正常时序依次为：onWillAppear>>onDidAppear>>onWillDisappear>>onDidDisappear。

**类型：** Callback<void>

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-onDidDisappear?: Callback<void>--><!--Device-CustomDialogControllerOptions-onDidDisappear?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: Callback<void>
```

弹窗显示动效前的事件回调。

**说明：**

1.正常时序依次为：onWillAppear>>onDidAppear>>onWillDisappear>>onDidDisappear。

2.在onWillAppear内设置改变弹窗显示效果的回调事件，二次弹出生效。

**类型：** Callback<void>

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-onWillAppear?: Callback<void>--><!--Device-CustomDialogControllerOptions-onWillAppear?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: Callback<void>
```

弹窗退出动效前的事件回调。

**说明：**

1.正常时序依次为：onWillAppear>>onDidAppear>>onWillDisappear>>onDidDisappear。

**类型：** Callback<void>

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-onWillDisappear?: Callback<void>--><!--Device-CustomDialogControllerOptions-onWillDisappear?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: Callback<DismissDialogAction>
```

交互式关闭回调函数。

**说明：**

1.当用户执行点击遮障层关闭、侧滑（左滑/右滑）、三键back、键盘ESC关闭交互操作时，如果注册该回调函数，则不会立刻关闭弹窗。在回调函数中可以通过reason得到阻拦关闭弹窗的操作类型，从而根据原因选择是否能关闭弹窗。当前组件返回的reason中，暂不支持CLOSE_BUTTON的枚举值。

2.在onWillDismiss回调中，不能再做onWillDismiss拦截。

**类型：** Callback<DismissDialogAction>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-onWillDismiss?: Callback<DismissDialogAction>--><!--Device-CustomDialogControllerOptions-onWillDismiss?: Callback<DismissDialogAction>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## openAnimation

```TypeScript
openAnimation?: AnimateParam
```

自定义设置弹窗弹出的动画效果相关参数。

**说明**：

tempo默认值为1，当设置小于等于0的值时按默认值处理。

iterations默认值为1，默认播放一次，设置为其他数值时按默认值处理。

playMode控制动画播放模式，默认值为PlayMode.Normal，设置为其他数值时按照默认值处理。

**类型：** AnimateParam

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-openAnimation?: AnimateParam--><!--Device-CustomDialogControllerOptions-openAnimation?: AnimateParam-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

设置弹窗背板的阴影。

当设备为2in1时，默认场景下获焦阴影值为ShadowStyle.OUTER_FLOATING_MD，失焦为ShadowStyle.OUTER_FLOATING_SM。其他设备默认无阴影。

**类型：** ShadowOptions | ShadowStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-CustomDialogControllerOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

某弹框需要显示在主窗口之外时，是否在子窗口显示此弹窗。值为true表示在子窗口显示弹窗。

默认值：false，弹窗显示在应用内，而非独立子窗口。

**说明**：showInSubWindow为true的弹窗无法触发显示另一个showInSubWindow为true的弹窗。不建议在showInSubWindow为true的弹窗中使用CalendarPicker、CalendarPickerDialog、DatePickerDialog、TextPickerDialog、TimePickerDialog、Toast组件，弹窗会影响上述组件行为。

**类型：** boolean

**默认值：** false [since 11]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-showInSubWindow?: boolean--><!--Device-CustomDialogControllerOptions-showInSubWindow?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

设置弹窗的系统材质。

**说明：**

- 默认值：[ImmersiveOptions](../../../../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)的style为ImmersiveStyle.ULTRA_THICK的[ImmersiveMaterial](../../../../reference/apis-arkui/arkts-apis-uimaterial.md#immersivematerial)对象。设置undefined时与默认值保持一致。  
- 不同的材质具有不同的效果，该接口影响背景色[backgroundColor](../arkts-components/arkts-arkui-common-commonmethod-c.md#backgroundcolor-1)、背景模糊[backgroundBlurStyle](../arkts-components/arkts-arkui-common-commonmethod-c.md#backgroundblurstyle-1)、背景效果[backgroundEffect](../arkts-components/arkts-arkui-common-commonmethod-c.md#backgroundeffect-1)、边框颜色[borderColor](../arkts-components/arkts-arkui-common-commonmethod-c.md#bordercolor-1)、边框宽度[borderWidth](../arkts-components/arkts-arkui-common-commonmethod-c.md#borderwidth-1)、阴影[shadow](../arkts-components/arkts-arkui-common-commonmethod-c.md#shadow-1)，不建议与上述接口一起使用。

**类型：** SystemUiMaterial

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-systemMaterial?: SystemUiMaterial--><!--Device-CustomDialogControllerOptions-systemMaterial?: SystemUiMaterial-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

设置弹窗背板的宽度。

**说明：**

- 弹窗宽度默认最大值：400vp。  
- 百分比参数方式：弹窗参考宽度为所在窗口的宽度，在此基础上调小或调大。

**类型：** Dimension

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomDialogControllerOptions-width?: Dimension--><!--Device-CustomDialogControllerOptions-width?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

