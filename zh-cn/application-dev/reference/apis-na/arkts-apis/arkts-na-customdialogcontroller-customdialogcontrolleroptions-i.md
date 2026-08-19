# CustomDialogControllerOptions

自定义弹窗的样式。 > **说明：** > > - 按下返回键和ESC键时会让弹窗退出。 > > - 弹窗在避让软键盘时到达极限高度之后会压缩高度。 > > 需要注意：高度压缩生效在外层容器上，如果容器根节点中的子组件设置了较大的固定高度，由于容器默认不裁剪，依然可能存在超出屏幕显示的情况。 > > - 自定义弹窗仅适用于简单提示场景，不能替代页面使用。弹窗避让软键盘时，与软键盘之间存在16vp的安全间距。 > > - 为了达成良好的视觉体验，弹窗的显示和关闭存在默认动画，动画时长不同设备间可能存在差异。 > > 需要注意：在动画播放过程中，页面不响应触摸、滑动、点击操作。关闭默认弹窗动画效果可设置openAnimation和closeAnimation的duration为0。 > > - 当前，ArkUI弹出框默认为非页面级弹出框，在页面路由跳转时，如果开发者未调用close方法将其关闭，弹出框将不会自动关闭。若需实现在跳转页面时覆盖弹出框的场景，可以使用 > [组件导航子页面显示类型的弹窗类型](../../../ui/arkts-navigation-navdestination.md#页面显示类型)或者 > [页面级弹出框](../../../ui/arkts-embedded-dialog.md)。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface CustomDialogControllerOptions--><!--Device-unnamed-export declare interface CustomDialogControllerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: DialogAlignment
```

弹窗在竖直方向上的对齐方式。 默认值：DialogAlignment.Default **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [DialogAlignment](arkts-na-alertdialog-dialogalignment-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-alignment?: DialogAlignment--><!--Device-CustomDialogControllerOptions-alignment?: DialogAlignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoCancel

```TypeScript
autoCancel?: boolean
```

是否允许点击遮障层退出，true表示关闭弹窗。false表示不关闭弹窗。 默认值：true **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-autoCancel?: boolean--><!--Device-CustomDialogControllerOptions-autoCancel?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

弹窗背板模糊材质。 默认值：从API版本26.0.0开始，为BlurStyle.NONE，API版本26.0.0之前，为BlurStyle.COMPONENT_ULTRA_THICK。 **说明：** 设置为BlurStyle.NONE即可关闭背景虚化。当设置了backgroundBlurStyle为非NONE值时，则不要设置backgroundColor，否则颜色显示将不符合预期效果。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [BlurStyle](../../apis-arkui/arkts-components/arkts-arkui-blurstyle-e.md)

**默认值：** BlurStyle.COMPONENT_ULTRA_THICK

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-backgroundBlurStyle?: BlurStyle--><!--Device-CustomDialogControllerOptions-backgroundBlurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

背景模糊效果。默认值请参考BackgroundBlurStyleOptions类型说明。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 19开始，该接口支持在原子化服务中使用。

**类型：** [BackgroundBlurStyleOptions](../../apis-arkui/arkts-components/arkts-arkui-backgroundblurstyleoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-CustomDialogControllerOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

设置弹窗背板填充。 默认值：Color.Transparent **说明：** 如果同时设置了内容构造器的背景色，则backgroundColor会被内容构造器的背景色覆盖。 backgroundColor会与模糊属性backgroundBlurStyle叠加产生效果，如果不符合预期，可将backgroundBlurStyle设置为BlurStyle.NONE，即可取消模糊。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-backgroundColor?: ResourceColor--><!--Device-CustomDialogControllerOptions-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

背景效果参数。默认值请参考BackgroundEffectOptions类型说明。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 19开始，该接口支持在原子化服务中使用。

**类型：** [BackgroundEffectOptions](../../apis-arkui/arkts-components/arkts-arkui-backgroundeffectoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-CustomDialogControllerOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ResourceColor | EdgeColors
```

设置弹窗背板的边框颜色。 默认值：Color.Black 如果使用borderColor属性，需要和borderWidth属性一起使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md) \| [EdgeColors](../../apis-arkui/arkts-apis/arkts-arkui-edgecolors-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-borderColor?: ResourceColor | EdgeColors--><!--Device-CustomDialogControllerOptions-borderColor?: ResourceColor | EdgeColors-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderStyle

```TypeScript
borderStyle?: BorderStyle | EdgeStyles
```

设置弹窗背板的边框样式。 默认值：BorderStyle.Solid 如果使用borderStyle属性，需要和borderWidth属性一起使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [BorderStyle](../../apis-arkui/arkts-apis/arkts-arkui-borderstyle-e.md) \| [EdgeStyles](../../apis-arkui/arkts-apis/arkts-arkui-edgestyles-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-borderStyle?: BorderStyle | EdgeStyles--><!--Device-CustomDialogControllerOptions-borderStyle?: BorderStyle | EdgeStyles-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Dimension | EdgeWidths
```

设置弹窗背板的边框宽度。 可分别设置4个边框宽度。 默认值：0。 百分比参数方式：以父元素弹窗宽的百分比来设置弹窗的边框宽度。 当弹窗左边框和右边框大于弹窗宽度，弹窗上边框和下边框大于弹窗高度，显示可能不符合预期。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md) \| [EdgeWidths](../../apis-arkui/arkts-apis/arkts-arkui-edgewidths-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-borderWidth?: Dimension | EdgeWidths--><!--Device-CustomDialogControllerOptions-borderWidth?: Dimension | EdgeWidths-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder: CustomBuilder | ExtendableComponent
```

自定义弹窗内容构造器。 **说明：** 若builder构造器使用回调函数作为入参，请注意使用this绑定问题，如builder: custombuilder({ callback: ()=> {...}})。 若在builder中监听数据变化可以使用[@Link](../../../ui/state-management/arkts-link.md)或 [@Consume](../../../ui/state-management/arkts-provide-and-consume.md)，而其他方式如 [@Prop](../../../reference/apis-arkui/arkui-ts/ts-state-management-prop.md)、 [@ObjectLink](../../../reference/apis-arkui/arkui-ts/ts-state-management-objectlink.md)不适用此场景。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** CustomBuilder \| [ExtendableComponent](arkts-na-extendablecomponent-extendablecomponent-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-builder: CustomBuilder | ExtendableComponent--><!--Device-CustomDialogControllerOptions-builder: CustomBuilder | ExtendableComponent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cancel

```TypeScript
cancel?: () => void
```

返回、ESC键和点击遮障层弹窗退出时的回调。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** () =&gt; void

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-cancel?: () => void--><!--Device-CustomDialogControllerOptions-cancel?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeAnimation

```TypeScript
closeAnimation?: AnimateParam
```

自定义设置弹窗关闭的动画效果相关参数。 **说明：** tempo默认值为1，当设置小于等于0的值时按默认值处理。 iterations默认值为1，默认播放一次，设置为其他数值时按默认值处理。 playMode控制动画播放模式，默认值为PlayMode.Normal，设置为其他数值时按照默认值处理。 页面转场切换时，建议使用默认关闭动效。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [AnimateParam](../../apis-arkui/arkts-components/arkts-arkui-animateparam-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-closeAnimation?: AnimateParam--><!--Device-CustomDialogControllerOptions-closeAnimation?: AnimateParam-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cornerRadius

```TypeScript
cornerRadius?: Dimension | BorderRadiuses
```

设置背板的圆角半径。 可分别设置4个圆角的半径。 默认值：{ topLeft: '32vp', topRight: '32vp', bottomLeft: '32vp', bottomRight: '32vp' } **说明：**自定义弹窗默认的背板圆角半径为32vp，如果需要使用cornerRadius属性，请和 borderRadius属性一起使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md) \| [BorderRadiuses](../../apis-arkui/arkts-apis/arkts-arkui-borderradiuses-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-cornerRadius?: Dimension | BorderRadiuses--><!--Device-CustomDialogControllerOptions-cornerRadius?: Dimension | BorderRadiuses-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## customStyle

```TypeScript
customStyle?: boolean
```

是否使用自定义样式。 默认值：false

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-customStyle?: boolean--><!--Device-CustomDialogControllerOptions-customStyle?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayModeInSubWindow

```TypeScript
displayModeInSubWindow?: DialogDisplayMode
```

Defines the dialog display mode when show in subwindow.

**类型：** [DialogDisplayMode](../../apis-arkui/arkts-apis/arkts-arkui-dialogdisplaymode-e.md)

**默认值：** DialogDisplayMode.SCREEN_BASED

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-displayModeInSubWindow?: DialogDisplayMode--><!--Device-CustomDialogControllerOptions-displayModeInSubWindow?: DialogDisplayMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

是否响应悬停态，值为true时，响应悬停态。 默认值：false，默认不响应。 **说明：** PC/2in1设备弹窗默认显示在上半屏，在enableHoverMode设置为true时，可以通过设置hoverModeArea参数显示在下半屏。其他设备弹窗在enableHoverMode设置为true时默认显示在下半屏，可 以通过设置hoverModeArea参数显示在上半屏。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 14开始，该接口支持在原子化服务中使用。

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-enableHoverMode?: boolean--><!--Device-CustomDialogControllerOptions-enableHoverMode?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## focusable

```TypeScript
focusable?: boolean
```

设置弹窗是否获取焦点。值为true表示获取焦点，值为false表示不获取焦点。 默认值：true **说明：** 只有弹出覆盖在当前窗口之上的弹窗才可以获取焦点。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 19开始，该接口支持在原子化服务中使用。

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-focusable?: boolean--><!--Device-CustomDialogControllerOptions-focusable?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## gridCount

```TypeScript
gridCount?: int
```

弹窗宽度占[栅格宽度](../../../ui/arkts-layout-development-grid-layout.md)的个数。 默认为按照窗口大小自适应，异常值按默认值处理，最大栅格数为系统最大栅格数。 取值范围：大于等于0的整数。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-gridCount?: int--><!--Device-CustomDialogControllerOptions-gridCount?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Dimension
```

设置弹窗背板的高度。 **说明：** - 弹窗高度默认最大值：0.9 *（窗口高度 - 安全区域）。 - 百分比参数方式：弹窗参考高度为（窗口高度 - 安全区域），在此基础上调小或调大。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-height?: Dimension--><!--Device-CustomDialogControllerOptions-height?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

悬停态下弹窗默认展示区域。 默认值：HoverModeAreaType.BOTTOM_SCREEN。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 14开始，该接口支持在原子化服务中使用。

**类型：** [HoverModeAreaType](../../apis-arkui/arkts-components/arkts-arkui-hovermodeareatype-e.md)

**默认值：** HoverModeAreaType.BOTTOM_SCREEN

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-hoverModeArea?: HoverModeAreaType--><!--Device-CustomDialogControllerOptions-hoverModeArea?: HoverModeAreaType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## immersiveMode

```TypeScript
immersiveMode?: ImmersiveMode
```

设置页面内弹窗蒙层效果。 **说明：** - 默认值：ImmersiveMode.DEFAULT - 当且仅当levelMode属性设置为LevelMode.EMBEDDED时生效。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 15开始，该接口支持在原子化服务中使用。

**类型：** [ImmersiveMode](arkts-na-promptaction-immersivemode-e.md)

**默认值：** ImmersiveMode.DEFAULT

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-immersiveMode?: ImmersiveMode--><!--Device-CustomDialogControllerOptions-immersiveMode?: ImmersiveMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isModal

```TypeScript
isModal?: boolean
```

弹窗是否为模态窗口。值为true表示为模态窗口且有蒙层，不可与弹窗周围其他控件进行交互，即蒙层区域无法事件透传。值为false表示为非模态窗口且无蒙层，可以与弹窗周围其他控件进行交互。 默认值：true **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-isModal?: boolean--><!--Device-CustomDialogControllerOptions-isModal?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidDistance

```TypeScript
keyboardAvoidDistance?: LengthMetrics
```

弹窗避让键盘后，和键盘之间的距离。 **说明：** - 默认值：16vp。 - 默认单位：vp。 - 当且仅当keyboardAvoidMode属性设置为DEFAULT时生效。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 15开始，该接口支持在原子化服务中使用。

**类型：** [LengthMetrics](../../apis-arkui/arkts-apis/arkts-arkui-graphics-lengthmetrics-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-keyboardAvoidDistance?: LengthMetrics--><!--Device-CustomDialogControllerOptions-keyboardAvoidDistance?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode?: KeyboardAvoidMode
```

用于设置弹窗是否在拉起软键盘时进行自动避让。 默认值：KeyboardAvoidMode.DEFAULT **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [KeyboardAvoidMode](../../apis-arkui/arkts-components/arkts-arkui-keyboardavoidmode-e.md)

**默认值：** KeyboardAvoidMode.DEFAULT

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-keyboardAvoidMode?: KeyboardAvoidMode--><!--Device-CustomDialogControllerOptions-keyboardAvoidMode?: KeyboardAvoidMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelMode

```TypeScript
levelMode?: LevelMode
```

设置弹窗显示层级。 **说明：** - 默认值：LevelMode.OVERLAY。 - 当且仅当showInSubWindow属性设置为false时生效。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 15开始，该接口支持在原子化服务中使用。

**类型：** [LevelMode](arkts-na-promptaction-levelmode-e.md)

**默认值：** LevelMode.OVERLAY

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-levelMode?: LevelMode--><!--Device-CustomDialogControllerOptions-levelMode?: LevelMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelOrder

```TypeScript
levelOrder?: LevelOrder
```

设置弹窗显示的顺序。 **说明：** - 默认值：LevelOrder.clamp(0) - 不支持动态刷新顺序。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 18开始，该接口支持在原子化服务中使用。

**类型：** [LevelOrder](arkts-na-promptaction-levelorder-c.md)

**默认值：** The value returns by LevelOrder.clamp(0)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-levelOrder?: LevelOrder--><!--Device-CustomDialogControllerOptions-levelOrder?: LevelOrder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelUniqueId

```TypeScript
levelUniqueId?: int
```

设置页面级弹窗需要显示的层级下的[getUniqueId](../../apis-arkui/arkts-apis/arkts-arkui-framenode-c.md#getuniqueid)。 取值范围：大于等于0的数字。 **说明：** - 当且仅当levelMode属性设置为LevelMode.EMBEDDED时生效。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 15开始，该接口支持在原子化服务中使用。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-levelUniqueId?: int--><!--Device-CustomDialogControllerOptions-levelUniqueId?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskColor

```TypeScript
maskColor?: ResourceColor
```

自定义蒙层颜色。 默认值：0x33000000 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-maskColor?: ResourceColor--><!--Device-CustomDialogControllerOptions-maskColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

弹窗遮蔽层区域，在遮蔽层区域内的事件不透传，在遮蔽层区域外的事件透传。 默认值：{ x: 0, y: 0, width: '100%', height: '100%' } **说明：** showInSubWindow为true时，maskRect不生效。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [Rectangle](../../apis-arkui/arkts-components/arkts-arkui-rectangle-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-maskRect?: Rectangle--><!--Device-CustomDialogControllerOptions-maskRect?: Rectangle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

弹窗相对alignment所在位置的偏移量。 默认值：{ dx: 0, dy: 0 } **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [Offset](../../apis-arkui/arkts-apis/arkts-arkui-offset-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-offset?: Offset--><!--Device-CustomDialogControllerOptions-offset?: Offset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: VoidCallback
```

弹窗弹出后的事件回调。 **说明：** 1.正常时序依次为：onWillAppear>>onDidAppear>>onWillDisappear>>onDidDisappear。 2.在onDidAppear内设置改变弹窗显示效果的回调事件，二次弹出生效。 3.快速点击弹出，关闭弹窗时，onWillDisappear在onDidAppear前生效。 4.弹窗入场动效未完成时彻底关闭弹窗，动效打断，onDidAppear不会触发。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 19开始，该接口支持在原子化服务中使用。

**类型：** [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-onDidAppear?: VoidCallback--><!--Device-CustomDialogControllerOptions-onDidAppear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: VoidCallback
```

弹窗消失后的事件回调。 **说明：** 1.正常时序依次为：onWillAppear>>onDidAppear>>onWillDisappear>>onDidDisappear。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 19开始，该接口支持在原子化服务中使用。

**类型：** [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-onDidDisappear?: VoidCallback--><!--Device-CustomDialogControllerOptions-onDidDisappear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: VoidCallback
```

弹窗显示动效前的事件回调。 **说明：** 1.正常时序依次为：onWillAppear>>onDidAppear>>onWillDisappear>>onDidDisappear。 2.在onWillAppear内设置改变弹窗显示效果的回调事件，二次弹出生效。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 19开始，该接口支持在原子化服务中使用。

**类型：** [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-onWillAppear?: VoidCallback--><!--Device-CustomDialogControllerOptions-onWillAppear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: VoidCallback
```

弹窗退出动效前的事件回调。 **说明：** 1.正常时序依次为：onWillAppear>>onDidAppear>>onWillDisappear>>onDidDisappear。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 19开始，该接口支持在原子化服务中使用。

**类型：** [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-onWillDisappear?: VoidCallback--><!--Device-CustomDialogControllerOptions-onWillDisappear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: Callback<DismissDialogAction>
```

交互式关闭回调函数。 **说明：** 1.当用户执行点击遮障层关闭、侧滑（左滑/右滑）、三键back、键盘ESC关闭交互操作时，如果注册该回调函数，则不会立刻关闭弹窗。在回调函数中可以通过reason得到阻拦关闭弹窗的操作类型，从而根据原因选择是否能关闭弹窗。当前 组件返回的reason中，暂不支持CLOSE_BUTTON的枚举值。 2.在onWillDismiss回调中，不能再做onWillDismiss拦截。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;[DismissDialogAction](arkts-na-actionsheet-dismissdialogaction-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-onWillDismiss?: Callback<DismissDialogAction>--><!--Device-CustomDialogControllerOptions-onWillDismiss?: Callback<DismissDialogAction>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## openAnimation

```TypeScript
openAnimation?: AnimateParam
```

自定义设置弹窗弹出的动画效果相关参数。 **说明：** tempo默认值为1，当设置小于等于0的值时按默认值处理。 iterations默认值为1，默认播放一次，设置为其他数值时按默认值处理。 playMode控制动画播放模式，默认值为PlayMode.Normal，设置为其他数值时按照默认值处理。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [AnimateParam](../../apis-arkui/arkts-components/arkts-arkui-animateparam-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-openAnimation?: AnimateParam--><!--Device-CustomDialogControllerOptions-openAnimation?: AnimateParam-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

设置弹窗背板的阴影。 当设备为2in1时，默认场景下获焦阴影值为ShadowStyle.OUTER_FLOATING_MD，失焦为ShadowStyle.OUTER_FLOATING_SM。其他设备默认无阴影。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [ShadowOptions](../../apis-arkui/arkts-components/arkts-arkui-shadowoptions-i.md) \| [ShadowStyle](../../apis-arkui/arkts-components/arkts-arkui-shadowstyle-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-CustomDialogControllerOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

某弹框需要显示在主窗口之外时，是否在子窗口显示此弹窗。值为true表示在子窗口显示弹窗。 默认值：false，弹窗显示在应用内，而非独立子窗口。 **说明：**showInSubWindow为true的弹窗无法触发显示另一个showInSubWindow为true的弹窗。不建议在showInSubWindow为true的弹窗中使用CalendarPicker、 CalendarPickerDialog、DatePickerDialog、TextPickerDialog、TimePickerDialog、Toast组件，弹窗会影响上述组件行为。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-showInSubWindow?: boolean--><!--Device-CustomDialogControllerOptions-showInSubWindow?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

设置弹窗的系统材质。 **说明：** - 默认值：ImmersiveOptions的style为ImmersiveStyle.ULTRA_THICK的ImmersiveMaterial对象。设置undefined时与默认值保持一致。 - 不同的材质具有不同的效果，该接口影响背景色backgroundColor、背景模糊 backgroundBlurStyle 、背景效果backgroundEffect、边框颜色 borderColor、边框宽度borderWidth、阴影 shadow，不建议与上述接口一起使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**类型：** [SystemUiMaterial](../../apis-arkui/arkts-components/arkts-arkui-systemuimaterial-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-systemMaterial?: SystemUiMaterial--><!--Device-CustomDialogControllerOptions-systemMaterial?: SystemUiMaterial-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

设置弹窗背板的宽度。 **说明：** - 弹窗宽度默认最大值：400vp。 - 百分比参数方式：弹窗参考宽度为所在窗口的宽度，在此基础上调小或调大。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-width?: Dimension--><!--Device-CustomDialogControllerOptions-width?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

