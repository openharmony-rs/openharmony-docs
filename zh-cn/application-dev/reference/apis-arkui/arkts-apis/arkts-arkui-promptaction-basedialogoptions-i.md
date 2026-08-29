# BaseDialogOptions

弹窗的选项。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## onDidAppear

```TypeScript
onDidAppear?: () => void
```

弹窗弹出后的事件回调。   
**说明：**
1.正常时序依次为：onWillAppear&gt;&gt;onDidAppear&gt;&gt;(onDateAccept/onCancel/onDateChange)&gt;&gt;onWillDisappear&gt;&gt;onDidDisappear。 
2.在onDidAppear内设置改变弹窗显示效果的回调事件，二次弹出生效。 
3.快速点击弹出，消失弹窗时，存在onWillDisappear在onDidAppear前生效。 
4. 当弹窗入场动效未完成时关闭弹窗，该回调不会触发。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: () => void
```

弹窗消失后的事件回调。   
**说明：** 正常时序依次为：onWillAppear&gt;&gt;onDidAppear&gt;&gt;(onDateAccept/onCancel/onDateChange)&gt;&gt;onWillDisappear&gt;&gt;onDidDisappear。 当弹窗退场动画未完成时（例如：同时触发弹窗关闭和页面切换），该回调不会触发。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: () => void
```

弹窗显示动效前的事件回调。   
**说明：**
1.正常时序依次为：onWillAppear&gt;&gt;onDidAppear&gt;&gt;(onDateAccept/onCancel/onDateChange)&gt;&gt;onWillDisappear&gt;&gt;onDidDisappear。 
2.在onWillAppear内设置改变弹窗显示效果的回调事件，二次弹出生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: () => void
```

弹窗退出动效前的事件回调。   
**说明：**
1.正常时序依次为：onWillAppear&gt;&gt;onDidAppear&gt;&gt;(onDateAccept/onCancel/onDateChange)&gt;&gt;onWillDisappear&gt;&gt;onDidDisappear。 
2.快速点击弹出，消失弹窗时，存在onWillDisappear在onDidAppear前生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: DialogAlignment
```

弹窗在竖直方向上的对齐方式。 默认值：DialogAlignment.Default   
**说明：** 若在UIExtension中设置showInSubWindow为true, 弹窗将基于UIExtension的宿主窗口对齐。

**类型：** [DialogAlignment](arkts-arkui-dialogalignment-e.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoCancel

```TypeScript
autoCancel?: boolean
```

点击遮障层时，是否关闭弹窗，true表示关闭弹窗。false表示不关闭弹窗。默认值：true

**类型：** boolean

**默认值：** true

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

背景模糊效果。默认值请参考BackgroundBlurStyleOptions类型说明。

**类型：** [BackgroundBlurStyleOptions](../arkts-components/arkts-arkui-backgroundblurstyleoptions-i.md)

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

背景效果参数。默认值请参考BackgroundEffectOptions类型说明。

**类型：** [BackgroundEffectOptions](../arkts-components/arkts-arkui-backgroundeffectoptions-i.md)

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dialogTransition

```TypeScript
dialogTransition?: TransitionEffect
```

设置弹窗内容显示的过渡效果。默认无动效。

**类型：** [TransitionEffect](../arkts-components/arkts-arkui-transitioneffect-c.md)

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayModeInSubWindow

```TypeScript
displayModeInSubWindow?: DialogDisplayMode
```

弹窗在子窗口中的显示模式。 默认值：DialogDisplayMode.SCREEN_BASED   
**说明：** 仅当showInSubWindow设置为true时生效。

**类型：** [DialogDisplayMode](arkts-arkui-dialogdisplaymode-e.md)

**默认值：** DialogDisplayMode.SCREEN_BASED

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

是否响应悬停态，值为true时，响应悬停态。 默认值：false，默认不响应。   
**说明：** PC/2in1设备弹窗默认显示在上半屏，在enableHoverMode设置为true。 可以通过设置hoverModeArea参数显示在下半屏。其他设备弹窗在enableHoverMode设置为true时默认显示在下半屏，可以通过设置hoverModeArea参数显示在上半屏。

**类型：** boolean

**默认值：** false

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## focusable

```TypeScript
focusable?: boolean
```

设置弹窗是否获取焦点。值为true表示获取焦点，值为false表示不获取焦点。 默认值：true   
**说明：** 只有弹出覆盖在当前窗口之上的弹窗才可以获取焦点。

**类型：** boolean

**默认值：** true

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

悬停态下弹窗默认展示区域。默认值：HoverModeAreaType.BOTTOM_SCREEN

**类型：** [HoverModeAreaType](../arkts-components/arkts-arkui-hovermodeareatype-e.md)

**默认值：** HoverModeAreaType.BOTTOM_SCREEN

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## immersiveMode

```TypeScript
immersiveMode?: ImmersiveMode
```

设置页面内弹窗蒙层效果。   
**说明：**
- 默认值：ImmersiveMode.DEFAULT
- 当且仅当levelMode属性设置为LevelMode.EMBEDDED时生效。

**类型：** [ImmersiveMode](arkts-arkui-promptaction-immersivemode-e.md)

**默认值：** ImmersiveMode.DEFAULT

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isModal

```TypeScript
isModal?: boolean
```

弹窗是否为模态窗口。值为true表示为模态窗口且有蒙层，不可与弹窗周围其他控件进行交互，即蒙层区域无法事件透传。 值为false表示为非模态窗口且无蒙层，可以与弹窗周围其他控件进行交互。 默认值：true

**类型：** boolean

**默认值：** true

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidDistance

```TypeScript
keyboardAvoidDistance?: LengthMetrics
```

弹窗避让键盘后，和键盘之间距离。   
**说明：**
- 默认值：16vp
- 默认单位：vp
- 当且仅当keyboardAvoidMode属性设置为DEFAULT时生效。

**类型：** LengthMetrics

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode?: KeyboardAvoidMode
```

用于设置弹窗是否在拉起软键盘时进行自动避让。默认值：KeyboardAvoidMode.DEFAULT

**类型：** KeyboardAvoidMode

**默认值：** KeyboardAvoidMode.DEFAULT

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelMode

```TypeScript
levelMode?: LevelMode
```

设置弹窗显示层级。   
**说明：**
- 默认值：LevelMode.OVERLAY
- 当且仅当showInSubWindow属性设置为false时生效。

**类型：** [LevelMode](arkts-arkui-promptaction-levelmode-e.md)

**默认值：** LevelMode.OVERLAY

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelOrder

```TypeScript
levelOrder?: LevelOrder
```

设置弹窗显示的顺序。  
**说明：**
- 默认值：LevelOrder.clamp(0)
- 不支持动态刷新顺序。

**类型：** [LevelOrder](arkts-arkui-promptaction-levelorder-c.md)

**默认值：** The value returned by LevelOrder.clamp(0)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelUniqueId

```TypeScript
levelUniqueId?: number
```

设置页面级弹窗需要显示的层级下的节点UniqueID。 取值范围：大于等于0的数字。   
**说明：**
- 当且仅当levelMode属性设置为LevelMode.EMBEDDED时生效。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskColor

```TypeScript
maskColor?: ResourceColor
```

自定义蒙层颜色。默认值: 0x33000000

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

弹窗遮蔽层区域。 默认值：{ x: 0, y: 0, width: '100%', height: '100%' }   
**说明：** showInSubWindow为true时，maskRect不生效。 maskRect在设置Rectangle中的部分属性后，若未设置其余的属性，则其余属性的默认值为0。

**类型：** [Rectangle](../arkts-components/arkts-arkui-rectangle-i.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskTransition

```TypeScript
maskTransition?: TransitionEffect
```

设置蒙层显示的过渡效果。默认无动效。

**类型：** [TransitionEffect](../arkts-components/arkts-arkui-transitioneffect-c.md)

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

弹窗相对alignment所在位置的偏移量。 默认值：{&nbsp;dx:&nbsp;0&nbsp;,&nbsp;dy:&nbsp;0&nbsp;}

**类型：** Offset

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: Callback<DismissDialogAction>
```

交互式关闭回调函数。   
**说明：**
1.当用户执行点击遮障层关闭、侧滑（左滑/右滑）、三键back、键盘ESC关闭交互操作时，如果注册该回调函数，则不会立刻关闭弹窗。 在回调函数中可以通过reason得到阻拦关闭弹窗的操作类型，从而根据原因选择是否能关闭弹窗。当前组件返回的reason中，暂不支持CLOSE_BUTTON的枚举值。 
2.在onWillDismiss回调中，不能再做onWillDismiss拦截。

**类型：** Callback&lt;[DismissDialogAction](arkts-arkui-promptaction-dismissdialogaction-i.md)&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

某弹窗需要显示在主窗口之外时，是否在子窗口显示此弹窗。值为true表示在子窗口显示弹窗。 默认值：false，弹窗显示在应用内，而非独立子窗口。

**类型：** boolean

**默认值：** false

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

设置弹窗的系统材质。   
**说明：**
- 默认值：[ImmersiveOptions](arkts-arkui-uimaterial-immersiveoptions-i.md)的style为 ImmersiveStyle.ULTRA_THICK的[ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md)对象。 设置undefined时与默认值保持一致。
- 不同的材质具有不同的效果，该接口影响 背景色backgroundColor、 背景模糊backgroundBlurStyle、 背景效果backgroundEffect、 边框颜色borderColor、 边框宽度borderWidth、 阴影shadow，不建议与上述接口一起使用。

**类型：** SystemUiMaterial

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition?: TransitionEffect
```

设置弹窗显示和退出的过渡效果。   
**说明：**
 1.如果不设置，则使用默认的显示/退出动效。 
 2.显示动效中按back键，打断显示动效，执行退出动效，动画效果为显示动效与退出动效的曲线叠加后的效果。 
 3.退出动效中按back键，不会打断退出动效，退出动效继续执行，继续按back键退出应用。

**类型：** [TransitionEffect](../arkts-components/arkts-arkui-transitioneffect-c.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
