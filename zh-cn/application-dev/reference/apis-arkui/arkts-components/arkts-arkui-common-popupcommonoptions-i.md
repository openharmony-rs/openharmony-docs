# PopupCommonOptions

配置弹出气泡的参数。使用[UIContext](../arkts-apis/arkts-arkui-uicontext.md)中的[getPromptAction()](@ohos.arkui.UIContext#getPromptAction)方法获取到[PromptAction](@ohos.arkui.UIContext#PromptAction)对象，再通过该对象调用[openPopup](../../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#openpopup18)和[updatePopup](../../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#updatepopup18)时传入的options参数。

**起始版本：** 18

<!--Device-unnamed-declare interface PopupCommonOptions--><!--Device-unnamed-declare interface PopupCommonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowHeight

```TypeScript
arrowHeight?: Dimension
```

The height of the arrow.

**类型：** Dimension

**默认值：** 8.0_vp.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-arrowHeight?: Dimension--><!--Device-PopupCommonOptions-arrowHeight?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowOffset

```TypeScript
arrowOffset?: Length
```

Popup箭头在气泡处的偏移。

箭头在气泡上下方时，数值为0表示箭头居最左侧，偏移量为箭头至最左侧的距离，默认居中。

箭头在气泡左右侧时，偏移量为箭头至最上侧的距离，默认居中。

显示在屏幕边缘时，气泡会自动左右偏移，数值为0时箭头始终指向绑定组件。

单位：vp

**说明：**

1. 没设置arrowOffset的情况下，气泡箭头与四个角的距离不能小于圆角半径。2. 只有arrowPointPosition不设置或者设置为null、undefined时，arrowOffset属性才生效。3. 不支持设置百分比。

**类型：** Length

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-arrowOffset?: Length--><!--Device-PopupCommonOptions-arrowOffset?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowPointPosition

```TypeScript
arrowPointPosition?: ArrowPointPosition
```

The position of the sharp corner of popup.

**类型：** ArrowPointPosition

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-arrowPointPosition?: ArrowPointPosition--><!--Device-PopupCommonOptions-arrowPointPosition?: ArrowPointPosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowWidth

```TypeScript
arrowWidth?: Dimension
```

The width of the arrow.

**类型：** Dimension

**默认值：** 16.0_vp.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-arrowWidth?: Dimension--><!--Device-PopupCommonOptions-arrowWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoCancel

```TypeScript
autoCancel?: boolean
```

页面有操作时，值为true表示自动关闭气泡，值为false表示气泡不会自动关闭。

默认值：true

**类型：** boolean

**默认值：** true

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-autoCancel?: boolean--><!--Device-PopupCommonOptions-autoCancel?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## avoidTarget

```TypeScript
avoidTarget?: AvoidanceMode
```

设置Popup避让时是否覆盖指向组件。

默认值：AvoidanceMode.COVER_TARGET

**类型：** AvoidanceMode

**默认值：** AvoidanceMode.COVER_TARGET

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-avoidTarget?: AvoidanceMode--><!--Device-PopupCommonOptions-avoidTarget?: AvoidanceMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Defines popup background blur Style

**类型：** BlurStyle

**默认值：** BlurStyle.COMPONENT_ULTRA_THICK

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-backgroundBlurStyle?: BlurStyle--><!--Device-PopupCommonOptions-backgroundBlurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

定义Popup的背景模糊样式选项。

**类型：** BackgroundBlurStyleOptions

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-PopupCommonOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

定义Popup的背景效果选项。

**类型：** BackgroundEffectOptions

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-PopupCommonOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderLinearGradient

```TypeScript
borderLinearGradient?: PopupBorderLinearGradient
```

设置Popup组件内描边线性渐变的颜色。

**说明：**

1. borderLinearGradient不设置或者设置为null、undefined时，内描边没有线性渐变效果。2. borderLinearGradient设置时，direction默认值是：GradientDirection.Bottom。

**类型：** PopupBorderLinearGradient

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-borderLinearGradient?: PopupBorderLinearGradient--><!--Device-PopupCommonOptions-borderLinearGradient?: PopupBorderLinearGradient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Dimension
```

设置Popup组件内描边的宽度。

默认值：1

单位：vp

**说明：**

1. 不支持设置百分比，设置百分比时按0处理。2. 在没有设置Popup组件内描边的情况下，该接口需要和borderLinearGradient配合使用。3. 当设置双描边时，建议内描边宽度不超过10vp。

**类型：** Dimension

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-borderWidth?: Dimension--><!--Device-PopupCommonOptions-borderWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colorMode

```TypeScript
colorMode?: AnchoredColorMode
```

设置气泡深浅色模式，默认跟随绑定组件深浅色模式。

默认值：AnchoredColorMode.FOLLOW_TARGET

**说明：**

1. 仅当绑定组件使用了[WithTheme](../../../../reference/apis-arkui/arkui-ts/ts-container-with-theme.md#接口)标签时，该属性才会生效。2. 该属性仅影响组件的默认样式，以及开发者设置的涉及深浅色资源的属性。3. 设置为AnchoredColorMode.FOLLOW_SYSTEM时，模糊材质可以跟随，文字颜色以及涉及深浅色资源的属性仍保持跟随绑定组件的深浅色配置。

**类型：** AnchoredColorMode

**默认值：** AnchoredColorMode.FOLLOW_TARGET

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-colorMode?: AnchoredColorMode--><!--Device-PopupCommonOptions-colorMode?: AnchoredColorMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableArrow

```TypeScript
enableArrow?: boolean
```

是否显示箭头。值为true时显示箭头，值为false时不显示箭头。

如果箭头所在方位侧的气泡长度不足以显示下箭头，则会默认不显示箭头。比如：placement设置为Left，此时如果气泡高度小于箭头的宽度（32vp）与气泡圆角两倍（48vp）之和（80vp），则实际不会显示箭头。

默认值：true

**类型：** boolean

**默认值：** true

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-enableArrow?: boolean--><!--Device-PopupCommonOptions-enableArrow?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Popup组件是否响应悬停态（半折叠状态）变化，即在悬停态下是否触发避让折痕区域。

默认值：false，2in1设备默认为true。未设置或者值为非法值时，生效默认值。

**说明：**

1. 如果Popup的弹出位置在悬停态折痕区域，Popup组件不会响应悬停态。2. 2in1设备从API version 20开始生效。3. 2in1设备仅在窗口瀑布模式下生效。

**类型：** boolean

**默认值：** false

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-enableHoverMode?: boolean--><!--Device-PopupCommonOptions-enableHoverMode?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## focusable

```TypeScript
focusable?: boolean
```

设置气泡弹出后是否获焦。

true：气泡可以获焦；false：气泡不会获焦。

默认值：false

**说明：**

不支持通过[updatePopup](../../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#updatepopup18)进行更新。

**类型：** boolean

**默认值：** false

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-focusable?: boolean--><!--Device-PopupCommonOptions-focusable?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## followTransformOfTarget

```TypeScript
followTransformOfTarget?: boolean
```

气泡绑定的宿主组件或其宿主组件的父容器添加了旋转、缩放等变换时，气泡是否跟随宿主组件变换。

true：气泡可以拿到变换后宿主的位置，显示到相应位置；false：气泡拿不到宿主变换后的位置，可能显示异常。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-followTransformOfTarget?: boolean--><!--Device-PopupCommonOptions-followTransformOfTarget?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelMode

```TypeScript
levelMode?: LevelMode
```

设置气泡的显示层级模式。

默认值：LevelMode.OVERLAY

**类型：** LevelMode

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-levelMode?: LevelMode--><!--Device-PopupCommonOptions-levelMode?: LevelMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mask

```TypeScript
mask?: boolean | PopupMaskType
```

设置气泡是否有遮罩层及遮罩颜色。设置为false时不显示遮罩层，设置为true时显示透明色遮罩层，设置为PopupMaskType时显示指定颜色的遮罩层。默认值：true

**类型：** boolean | PopupMaskType

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-mask?: boolean | PopupMaskType--><!--Device-PopupCommonOptions-mask?: boolean | PopupMaskType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Position
```

设置Popup组件相对于placement设置的显示位置的偏移。

**说明：**

不支持设置百分比。

默认值：{ x: 0, y: 0 }

单位：vp

**类型：** Position

**默认值：** { x: 0, y: 0 }

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-offset?: Position--><!--Device-PopupCommonOptions-offset?: Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onStateChange

```TypeScript
onStateChange?: PopupStateChangeCallback
```

气泡状态变化事件回调。

**说明：**

不支持通过[updatePopup](../../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#updatepopup18)进行更新。

**类型：** PopupStateChangeCallback

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-onStateChange?: PopupStateChangeCallback--><!--Device-PopupCommonOptions-onStateChange?: PopupStateChangeCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: boolean | Callback<DismissPopupAction>
```

设置Popup交互式关闭拦截开关及拦截回调函数，默认值为true，Popup响应点击、侧滑（左滑/右滑）、三键back。

1. 当为boolean类型时，如果设置为false，则不响应点击、侧滑（左滑/右滑）、三键back、路由跳转或键盘ESC退出事件，仅当设置“气泡显示状态”参数show值为false时才退出；如果设置为true，则正常响应退出事件；2. 如果设置为函数类型，则拦截退出事件且执行回调函数。侧滑（左滑/右滑）、三键back、路由跳转或键盘ESC在回调函数中返回的reason为PRESS_BACK，点击为TOUCH_OUTSIDE。

**说明：**

1. 在onWillDismiss回调中，不能再做onWillDismiss拦截。2. 不支持通过[updatePopup](../../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#updatepopup18)进行更新。

**类型：** boolean | Callback<DismissPopupAction>

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-onWillDismiss?: boolean | Callback<DismissPopupAction>--><!--Device-PopupCommonOptions-onWillDismiss?: boolean | Callback<DismissPopupAction>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## outlineLinearGradient

```TypeScript
outlineLinearGradient?: PopupBorderLinearGradient
```

设置Popup组件外描边线性渐变的颜色。

**说明：**

1. outlineLinearGradient不设置或者设置为null、undefined时，外描边没有线性渐变效果。2. outlineLinearGradient设置时，direction默认值是：GradientDirection.Bottom。

**类型：** PopupBorderLinearGradient

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-outlineLinearGradient?: PopupBorderLinearGradient--><!--Device-PopupCommonOptions-outlineLinearGradient?: PopupBorderLinearGradient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## outlineWidth

```TypeScript
outlineWidth?: Dimension
```

设置Popup组件外描边的宽度。

默认值：1

单位：vp

**说明：**

1. 不支持设置百分比，设置百分比时按0处理。2. 在没有设置Popup组件外描边的情况下，该接口需要和outlineLinearGradient配合使用。3. 当设置双描边时，建议外描边宽度不超过10vp。

**类型：** Dimension

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-outlineWidth?: Dimension--><!--Device-PopupCommonOptions-outlineWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placement

```TypeScript
placement?: Placement
```

气泡组件优先显示的位置，当前位置显示不下时，会自动调整位置。

默认值：Placement.Bottom

**类型：** Placement

**默认值：** Placement.Bottom

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-placement?: Placement--><!--Device-PopupCommonOptions-placement?: Placement-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## popupColor

```TypeScript
popupColor?: ResourceColor
```

气泡的颜色。如需去除模糊背景填充效果，需将backgroundBlurStyle设置为BlurStyle.NONE。默认值：透明色[TRANSPARENT](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-scenetypes-color-i.md)加模糊背景填充效果[COMPONENT_ULTRA_THICK](arkts-arkui-common-blurstyle-e.md)。

**类型：** ResourceColor

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-popupColor?: ResourceColor--><!--Device-PopupCommonOptions-popupColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius?: Dimension
```

The round corners of the popup.

**类型：** Dimension

**默认值：** 20.0_vp.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-radius?: Dimension--><!--Device-PopupCommonOptions-radius?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

The style of popup Shadow.

**类型：** ShadowOptions | ShadowStyle

**默认值：** ShadowStyle.OUTER_DEFAULT_MD.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-PopupCommonOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

取值为true时，气泡会显示在创建的子窗里，取值为false时，气泡会显示在对应的主窗中。

默认值：false

**说明：**

不支持通过[updatePopup](../../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#updatepopup18)进行更新。

**类型：** boolean

**默认值：** false

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-showInSubWindow?: boolean--><!--Device-PopupCommonOptions-showInSubWindow?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

设置组件的系统材质。

默认值：undefined，会清除由该接口设置的材质效果。

**说明：**

不同系统材质对应不同的属性影响效果，该接口影响背景色[backgroundColor](arkts-arkui-common-commonmethod-c.md#backgroundcolor-1)、边框颜色[borderColor](arkts-arkui-common-commonmethod-c.md#bordercolor-1)、边框宽度[borderWidth](arkts-arkui-common-commonmethod-c.md#borderwidth-1)、阴影[shadow](arkts-arkui-common-commonmethod-c.md#shadow-1)，不建议与上述接口一起使用。

**类型：** SystemUiMaterial

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-systemMaterial?: SystemUiMaterial--><!--Device-PopupCommonOptions-systemMaterial?: SystemUiMaterial-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## targetSpace

```TypeScript
targetSpace?: Length
```

设置Popup与宿主节点的间隙。不支持设置百分比。

默认值：8

单位：vp

**类型：** Length

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-targetSpace?: Length--><!--Device-PopupCommonOptions-targetSpace?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition?: TransitionEffect
```

自定义设置Popup气泡显示和退出的动画效果。

**说明：**

1. 如果不设置，则使用默认的显示/退出动效。2. 显示动效中按back键，打断显示动效，执行退出动效，动画效果为显示动效与退出动效的曲线叠加后的效果。3. 退出动效中按back键，不会打断退出动效，退出动效继续执行，back键不被响应。

4.不支持通过[updatePopup](../../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#updatepopup18)进行更新。

**类型：** TransitionEffect

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-transition?: TransitionEffect--><!--Device-PopupCommonOptions-transition?: TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

Set the width of the popup.

**类型：** Dimension

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupCommonOptions-width?: Dimension--><!--Device-PopupCommonOptions-width?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

