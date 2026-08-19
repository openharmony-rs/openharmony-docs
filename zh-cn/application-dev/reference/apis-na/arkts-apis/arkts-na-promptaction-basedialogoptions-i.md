# BaseDialogOptions

弹窗的选项。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-promptAction-export interface BaseDialogOptions--><!--Device-promptAction-export interface BaseDialogOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## alignment

```TypeScript
alignment?: DialogAlignment
```

弹窗在竖直方向上的对齐方式。<br>默认值：DialogAlignment.Default <br/>**说明：**<br/>若在UIExtension中设置showInSubWindow为true, 弹窗将基于UIExtension的宿主窗口对齐。

**类型：** DialogAlignment

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-alignment?: DialogAlignment--><!--Device-BaseDialogOptions-alignment?: DialogAlignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoCancel

```TypeScript
autoCancel?: boolean
```

点击遮障层时，是否关闭弹窗，true表示关闭弹窗。false表示不关闭弹窗。<br/>默认值：true

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-autoCancel?: boolean--><!--Device-BaseDialogOptions-autoCancel?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

背景模糊效果。默认值请参考BackgroundBlurStyleOptions类型说明。

**类型：** BackgroundBlurStyleOptions

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-BaseDialogOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

背景效果参数。默认值请参考BackgroundEffectOptions类型说明。

**类型：** BackgroundEffectOptions

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-BaseDialogOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dialogTransition

```TypeScript
dialogTransition?: TransitionEffect
```

设置弹窗内容显示的过渡效果。默认无动效。

**类型：** TransitionEffect

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-dialogTransition?: TransitionEffect--><!--Device-BaseDialogOptions-dialogTransition?: TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayModeInSubWindow

```TypeScript
displayModeInSubWindow?: DialogDisplayMode
```

Defines the dialog display mode when show in subwindow.

**类型：** DialogDisplayMode

**默认值：** DialogDisplayMode.SCREEN_BASED

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-displayModeInSubWindow?: DialogDisplayMode--><!--Device-BaseDialogOptions-displayModeInSubWindow?: DialogDisplayMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

是否响应悬停态，值为true时，响应悬停态。&lt;br /&gt;默认值：false，默认不响应。 &lt;br /&gt;**说明：**&lt;br /&gt;PC/2in1设备弹窗默认显示在上半屏，在enableHoverMode设置为true。可以通过设置hoverModeArea参数显示在下半屏。 其他设备弹窗在enableHoverMode设置为true时默认显示在下半屏，可以通过设置hoverModeArea参数显示在上半屏。

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-enableHoverMode?: boolean--><!--Device-BaseDialogOptions-enableHoverMode?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## focusable

```TypeScript
focusable?: boolean
```

设置弹窗是否获取焦点。值为true表示获取焦点，值为false表示不获取焦点。&lt;br /&gt;默认值：true &lt;br /&gt;**说明：**&lt;br /&gt;只有弹出覆盖在当前窗口之上的弹窗才可以获取焦点。

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-focusable?: boolean--><!--Device-BaseDialogOptions-focusable?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

悬停态下弹窗默认展示区域。&lt;br /&gt;默认值：HoverModeAreaType.BOTTOM_SCREEN

**类型：** HoverModeAreaType

**默认值：** HoverModeAreaType.BOTTOM_SCREEN

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-hoverModeArea?: HoverModeAreaType--><!--Device-BaseDialogOptions-hoverModeArea?: HoverModeAreaType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## immersiveMode

```TypeScript
immersiveMode?: ImmersiveMode
```

设置页面内弹窗蒙层效果。&lt;br /&gt;**说明：**&lt;br /&gt;- 默认值：ImmersiveMode.DEFAULT &lt;br /&gt;- 当且仅当levelMode属性设置为LevelMode.EMBEDDED时生效。

**类型：** [ImmersiveMode](arkts-na-promptaction-immersivemode-e.md)

**默认值：** ImmersiveMode.DEFAULT

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-immersiveMode?: ImmersiveMode--><!--Device-BaseDialogOptions-immersiveMode?: ImmersiveMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isModal

```TypeScript
isModal?: boolean
```

弹窗是否为模态窗口。值为true表示为模态窗口且有蒙层，不可与弹窗周围其他控件进行交互，即蒙层区域无法事件透传。 值为false表示为非模态窗口且无蒙层，可以与弹窗周围其他控件进行交互。<br/>默认值：true

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-isModal?: boolean--><!--Device-BaseDialogOptions-isModal?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidDistance

```TypeScript
keyboardAvoidDistance?: LengthMetrics
```

弹窗避让键盘后，和键盘之间距离。&lt;br /&gt;**说明：**<br/>- 默认值：16vp&lt;br /&gt;- 默认单位：vp &lt;br /&gt;- 当且仅当keyboardAvoidMode属性设置为DEFAULT时生效。

**类型：** LengthMetrics

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-keyboardAvoidDistance?: LengthMetrics--><!--Device-BaseDialogOptions-keyboardAvoidDistance?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode?: KeyboardAvoidMode
```

用于设置弹窗是否在拉起软键盘时进行自动避让。<br/>默认值：KeyboardAvoidMode.DEFAULT

**类型：** KeyboardAvoidMode

**默认值：** KeyboardAvoidMode.DEFAULT

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-keyboardAvoidMode?: KeyboardAvoidMode--><!--Device-BaseDialogOptions-keyboardAvoidMode?: KeyboardAvoidMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelMode

```TypeScript
levelMode?: LevelMode
```

设置弹窗显示层级。&lt;br /&gt;**说明：**&lt;br /&gt;- 默认值：LevelMode.OVERLAY &lt;br /&gt;- 当且仅当showInSubWindow属性设置为false时生效。

**类型：** [LevelMode](arkts-na-promptaction-levelmode-e.md)

**默认值：** LevelMode.OVERLAY

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-levelMode?: LevelMode--><!--Device-BaseDialogOptions-levelMode?: LevelMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelOrder

```TypeScript
levelOrder?: LevelOrder
```

设置弹窗显示的顺序。&lt;br /&gt;**说明：**&lt;br /&gt;- 默认值：LevelOrder.clamp(0) &lt;br /&gt;- 不支持动态刷新顺序。

**类型：** [LevelOrder](arkts-na-promptaction-levelorder-c.md)

**默认值：** The value returned by LevelOrder.clamp(0)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-levelOrder?: LevelOrder--><!--Device-BaseDialogOptions-levelOrder?: LevelOrder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelUniqueId

```TypeScript
levelUniqueId?: int
```

设置页面级弹窗需要显示的层级下的节点UniqueID，该ID可以通过[getUniqueId](../../apis-arkui/arkts-apis/arkts-arkui-framenode-c.md#getuniqueid)获取。 <br/>取值范围：大于等于0的数字。&lt;br /&gt;**说明：** &lt;br /&gt;- 当且仅当levelMode属性设置为LevelMode.EMBEDDED时生效。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-levelUniqueId?: int--><!--Device-BaseDialogOptions-levelUniqueId?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskColor

```TypeScript
maskColor?: ResourceColor
```

自定义蒙层颜色。<br>默认值: 0x33000000

**类型：** ResourceColor

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-maskColor?: ResourceColor--><!--Device-BaseDialogOptions-maskColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

弹窗遮蔽层区域。 <br/>默认值：{ x: 0, y: 0, width: '100%', height: '100%' } <br/>**说明：** <br/>showInSubWindow为true时，maskRect不生效。 <br/>maskRect在设置[Rectangle](../../../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md#rectangle8)中的部分属性后， 若未设置其余的属性，则其余属性的默认值为0。

**类型：** Rectangle

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-maskRect?: Rectangle--><!--Device-BaseDialogOptions-maskRect?: Rectangle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskTransition

```TypeScript
maskTransition?: TransitionEffect
```

设置蒙层显示的过渡效果。默认无动效。

**类型：** TransitionEffect

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-maskTransition?: TransitionEffect--><!--Device-BaseDialogOptions-maskTransition?: TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

弹窗相对alignment所在位置的偏移量。<br/>默认值：{&nbsp;dx:&nbsp;0&nbsp;,&nbsp;dy:&nbsp;0&nbsp;}

**类型：** Offset

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-offset?: Offset--><!--Device-BaseDialogOptions-offset?: Offset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: VoidCallback
```

弹窗弹出后的事件回调。 &lt;br /&gt;**说明：** &lt;br /&gt;1.正常时序依次为：onWillAppear>>onDidAppear>>(onDateAccept/onCancel/onDateChange)>>onWillDisappear>>onDidDisappear。 &lt;br /&gt;2.在onDidAppear内设置改变弹窗显示效果的回调事件，二次弹出生效。 &lt;br /&gt;3.快速点击弹出，消失弹窗时，存在onWillDisappear在onDidAppear前生效。 &lt;br /&gt;4. 当弹窗入场动效未完成时关闭弹窗，该回调不会触发。

**类型：** VoidCallback

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-onDidAppear?: VoidCallback--><!--Device-BaseDialogOptions-onDidAppear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: VoidCallback
```

弹窗消失后的事件回调。 &lt;br /&gt;**说明：** &lt;br /&gt;正常时序依次为：onWillAppear>>onDidAppear>>(onDateAccept/onCancel/onDateChange)>>onWillDisappear>>onDidDisappear。 <br/>当弹窗退场动画未完成时（例如：同时触发弹窗关闭和页面切换），该回调不会触发。

**类型：** VoidCallback

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-onDidDisappear?: VoidCallback--><!--Device-BaseDialogOptions-onDidDisappear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: VoidCallback
```

弹窗显示动效前的事件回调。 &lt;br /&gt;**说明：** &lt;br /&gt;1.正常时序依次为：onWillAppear>>onDidAppear>>(onDateAccept/onCancel/onDateChange)>>onWillDisappear>>onDidDisappear。 &lt;br /&gt;2.在onWillAppear内设置改变弹窗显示效果的回调事件，二次弹出生效。

**类型：** VoidCallback

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-onWillAppear?: VoidCallback--><!--Device-BaseDialogOptions-onWillAppear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: VoidCallback
```

弹窗退出动效前的事件回调。 &lt;br /&gt;**说明：** &lt;br /&gt;1.正常时序依次为：onWillAppear>>onDidAppear>>(onDateAccept/onCancel/onDateChange)>>onWillDisappear>>onDidDisappear。 &lt;br /&gt;2.快速点击弹出，消失弹窗时，存在onWillDisappear在onDidAppear前生效。

**类型：** VoidCallback

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-onWillDisappear?: VoidCallback--><!--Device-BaseDialogOptions-onWillDisappear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: Callback<DismissDialogAction>
```

交互式关闭回调函数。 <br/>**说明：** <br/>1.当用户执行点击遮障层关闭、侧滑（左滑/右滑）、三键back、键盘ESC关闭交互操作时，如果注册该回调函数，则不会立刻关闭弹窗。 在回调函数中可以通过reason得到阻拦关闭弹窗的操作类型，从而根据原因选择是否能关闭弹窗。当前组件返回的reason中，暂不支持CLOSE_BUTTON的枚举值。 <br/>2.在onWillDismiss回调中，不能再做onWillDismiss拦截。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DismissDialogAction](../../apis-arkui/arkts-apis/arkts-arkui-promptaction-dismissdialogaction-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-onWillDismiss?: Callback<DismissDialogAction>--><!--Device-BaseDialogOptions-onWillDismiss?: Callback<DismissDialogAction>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

某弹窗需要显示在主窗口之外时，是否在子窗口显示此弹窗。值为true表示在子窗口显示弹窗。<br/>默认值：false，弹窗显示在应用内，而非独立子窗口。

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-showInSubWindow?: boolean--><!--Device-BaseDialogOptions-showInSubWindow?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: uiMaterial.Material
```

设置弹窗的系统材质。<br/>**说明：**<br/>- 默认值：ImmersiveOptions的style为ImmersiveStyle.ULTRA_THICK的ImmersiveMaterial对象。 设置undefined时与默认值保持一致。<br/>- 不同的材质具有不同的效果，该接口影响 背景色backgroundColor、 背景模糊backgroundBlurStyle、 背景效果backgroundEffect、 边框颜色borderColor、边框宽度borderWidth、 阴影shadow，不建议与上述接口一起使用。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-systemMaterial?: uiMaterial.Material--><!--Device-BaseDialogOptions-systemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition?: TransitionEffect
```

设置弹窗显示和退出的过渡效果。<br/>**说明：**<br/> 1.如果不设置，则使用默认的显示/退出动效。 <br/> 2.显示动效中按back键，打断显示动效，执行退出动效，动画效果为显示动效与退出动效的曲线叠加后的效果。 <br/> 3.退出动效中按back键，不会打断退出动效，退出动效继续执行，继续按back键退出应用。

**类型：** TransitionEffect

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseDialogOptions-transition?: TransitionEffect--><!--Device-BaseDialogOptions-transition?: TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

