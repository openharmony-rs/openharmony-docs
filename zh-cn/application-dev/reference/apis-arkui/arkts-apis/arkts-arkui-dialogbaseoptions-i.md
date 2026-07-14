# DialogBaseOptions

所有Dialog类型共享的基本选项。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: DialogBaseAlignment
```

对话框的对齐模式。

**类型：** DialogBaseAlignment

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoCancel

```TypeScript
autoCancel?: boolean
```

是否允许通过触摸面罩或按返回键退出。

**类型：** boolean

**默认值：** true

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

对话框的背景模糊样式。
<br>设置为BlurStyle.NONE将禁用背景模糊。

**类型：** BlurStyle

**默认值：** BlurStyle.COMPONENT_ULTRA_THICK

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

带选项的背景模糊样式。

**类型：** BackgroundBlurStyleOptions

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

对话框的背景颜色。
<br>当backgroundColor设置为非透明色时，backgroundBlurStyle必须设置为BlurStyle.NONE。

**类型：** ResourceColor

**默认值：** Color.Transparent

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

带选项的背景效果。

**类型：** BackgroundEffectOptions

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ResourceColor | EdgeColors | LocalizedEdgeColors
```

对话框的边框颜色。

**类型：** ResourceColor | EdgeColors | LocalizedEdgeColors

**默认值：** Color.Black

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: Dimension | BorderRadiuses | LocalizedBorderRadiuses
```

背景的边框半径。

**类型：** Dimension | BorderRadiuses | LocalizedBorderRadiuses

**默认值：** { topLeft: '32vp', topRight: '32vp', bottomLeft: '32vp', bottomRight: '32vp' }

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderStyle

```TypeScript
borderStyle?: BorderStyle | EdgeStyles
```

对话框边框样式。

**类型：** BorderStyle | EdgeStyles

**默认值：** BorderStyle.Solid

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Dimension | EdgeWidths | LocalizedEdgeWidths
```

对话框边框宽度。

**类型：** Dimension | EdgeWidths | LocalizedEdgeWidths

**默认值：** 0

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: DialogBaseController
```

Dialog 控制器。

**类型：** DialogBaseController

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dialogTransition

```TypeScript
dialogTransition?: TransitionEffect
```

用于打开/关闭对话框内容区域的对话框过渡动效参数。

**类型：** TransitionEffect

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayModeInSubWindow

```TypeScript
displayModeInSubWindow?: DialogDisplayMode
```

定义在子窗口中显示时的对话框显示模式。

**类型：** DialogDisplayMode

**默认值：** DialogDisplayMode.SCREEN_BASED

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

是否启用悬停模式。

**类型：** boolean

**默认值：** false

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## focusable

```TypeScript
focusable?: boolean
```

对话框是否可以获得焦点。

**类型：** boolean

**默认值：** true

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Dimension
```

对话框的高度。

**类型：** Dimension

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

悬停模式下对话框的显示区域。

**类型：** HoverModeAreaType

**默认值：** HoverModeAreaType.BOTTOM_SCREEN

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## immersiveMode

```TypeScript
immersiveMode?: ImmersiveMode
```

页面级对话框蒙层效果。

**类型：** ImmersiveMode

**默认值：** ImmersiveMode.DEFAULT

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isModal

```TypeScript
isModal?: boolean
```

对话框是否为模态。

**类型：** boolean

**默认值：** true

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidDistance

```TypeScript
keyboardAvoidDistance?: LengthMetrics
```

对话框与系统键盘之间的距离。

**类型：** LengthMetrics

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode?: KeyboardAvoidMode
```

键盘避让模式。

**类型：** KeyboardAvoidMode

**默认值：** KeyboardAvoidMode.DEFAULT

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelMode

```TypeScript
levelMode?: LevelMode
```

对话框的显示级别。

**类型：** LevelMode

**默认值：** LevelMode.OVERLAY

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelOrder

```TypeScript
levelOrder?: LevelOrder
```

对话框的显示顺序。

**类型：** LevelOrder

**默认值：** The value returned by LevelOrder.clamp(0)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelUniqueId

```TypeScript
levelUniqueId?: number
```

页面级对话框显示层下节点的唯一标识。
取值限定为整数。
<br>该参数仅在levelMode为LevelMode.EMBEDDED时生效。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskColor

```TypeScript
maskColor?: ResourceColor
```

对话框的蒙层颜色。

**类型：** ResourceColor

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

对话框的蒙层区域。

**类型：** Rectangle

**默认值：** { x: 0, y: 0, width: '100%', height: '100%' }

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskTransition

```TypeScript
maskTransition?: TransitionEffect
```

用于打开/关闭遮罩的蒙层过渡动效参数。

**类型：** TransitionEffect

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

对话框相对于对齐位置的偏移。

**类型：** Offset

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: VoidCallback
```

对话框出现时的回调函数。

**类型：** VoidCallback

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: VoidCallback
```

对话框消失时的回调函数。

**类型：** VoidCallback

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: VoidCallback
```

对话框打开动画开始前的回调函数。

**类型：** VoidCallback

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: VoidCallback
```

对话框关闭动画开始前的回调函数。

**类型：** VoidCallback

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: Callback<DialogDismissal>
```

对话框交互关闭的回调。
<br>如果注册了此回调，则用户点击后对话框不会立即关闭
遮罩或返回按钮。
回调中的reason参数用于判断是否可以关闭对话框。

**类型：** Callback<DialogDismissal>

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

对话框的阴影。

**类型：** ShadowOptions | ShadowStyle

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

是否在子窗口中显示。
<br>isModal = true和showInSubWindow = true不能同时使用。

**类型：** boolean

**默认值：** false

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

为对话框设置系统样式材质。不同的材料有不同的效果，会影响背景色、边框、阴影和对话框的其他视觉属性。

**类型：** SystemUiMaterial

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

对话框的宽度。

**类型：** Dimension

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.1.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

