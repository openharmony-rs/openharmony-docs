# CustomPopupOptions

Defines the custom popup options.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface CustomPopupOptions--><!--Device-unnamed-export declare interface CustomPopupOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowHeight

```TypeScript
arrowHeight?: Dimension
```

The height of the arrow. &lt;p&gt;&lt;strong&gt;NOTE&lt;/strong&gt;: <br>This parameter cannot be set in percentage. &lt;/p&gt;

**类型：** [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md)

**默认值：** 8.0_vp.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-arrowHeight?: Dimension--><!--Device-CustomPopupOptions-arrowHeight?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowOffset

```TypeScript
arrowOffset?: Length
```

The offset of the sharp corner of popup. Offset of the popup arrow relative to the popup. When the arrow is at the top or bottom of the popup: <br>The value 0 indicates that the arrow is located on the leftmost, and any other value indicates the distance from the arrow to the leftmost; the arrow is centered by default. When the arrow is on the left or right side of the popup: The value indicates the distance from the arrow to the top; the arrow is centered by default. When the popup is displayed on either edge of the screen, it will automatically deviate leftward or rightward to stay within the safe area. When the value is 0, the arrow always points to the bound component.

**类型：** [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-arrowOffset?: Length--><!--Device-CustomPopupOptions-arrowOffset?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowPointPosition

```TypeScript
arrowPointPosition?: ArrowPointPosition
```

Position of the popup arrow relative to its parent component. Available positions are Start, Center, and End, in both vertical and horizontal directions. All these positions are within the parent component area.

**类型：** [ArrowPointPosition](../../apis-arkui/arkts-apis/arkts-arkui-arrowpointposition-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-arrowPointPosition?: ArrowPointPosition--><!--Device-CustomPopupOptions-arrowPointPosition?: ArrowPointPosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowWidth

```TypeScript
arrowWidth?: Dimension
```

Arrow thickness. If the arrow thickness exceeds the length of the edge minus twice the size of the popup rounded corner, the arrow is not drawn. &lt;p&gt;&lt;strong&gt;NOTE&lt;/strong&gt;: <br>This parameter cannot be set in percentage. &lt;/p&gt;

**类型：** [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md)

**默认值：** 16.0_vp.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-arrowWidth?: Dimension--><!--Device-CustomPopupOptions-arrowWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoCancel

```TypeScript
autoCancel?: boolean
```

Whether to automatically dismiss the popup when an operation is performed on the page. &lt;p&gt;&lt;strong&gt;NOTE&lt;/strong&gt;: <br>To enable the popup to disappear upon a click on it, place a layout component in the builder place the &lt;Popup&gt; component in the layout component, and modify the value of the bindPopup variable (show: boolean) in the onClick event of the layout component. &lt;/p&gt;

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-autoCancel?: boolean--><!--Device-CustomPopupOptions-autoCancel?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## avoidTarget

```TypeScript
avoidTarget?: AvoidanceMode
```

Determine if popup can avoid the target when the display space is insufficient.

**类型：** [AvoidanceMode](../../apis-arkui/arkts-components/arkts-arkui-avoidancemode-e.md)

**默认值：** AvoidanceMode.COVER_TARGET

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-avoidTarget?: AvoidanceMode--><!--Device-CustomPopupOptions-avoidTarget?: AvoidanceMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur style of the popup.

**类型：** [BlurStyle](arkts-na-common-blurstyle-e.md)

**默认值：** BlurStyle.COMPONENT_ULTRA_THICK

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-backgroundBlurStyle?: BlurStyle--><!--Device-CustomPopupOptions-backgroundBlurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Defines the popup's background blur style with options

**类型：** [BackgroundBlurStyleOptions](arkts-na-common-backgroundblurstyleoptions-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-CustomPopupOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

Defines the popup's background effect with options

**类型：** [BackgroundEffectOptions](arkts-na-common-backgroundeffectoptions-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-CustomPopupOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderLinearGradient

```TypeScript
borderLinearGradient?: PopupBorderLinearGradient
```

The LinearGradient of popup's innerline.

**类型：** [PopupBorderLinearGradient](arkts-na-common-popupborderlineargradient-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-borderLinearGradient?: PopupBorderLinearGradient--><!--Device-CustomPopupOptions-borderLinearGradient?: PopupBorderLinearGradient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Dimension
```

The width of popup's border.

**类型：** [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-borderWidth?: Dimension--><!--Device-CustomPopupOptions-borderWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder: CustomBuilder
```

Popup builder. &lt;p&gt;&lt;strong&gt;NOTE&lt;/strong&gt;: <br>The popup attribute is a universal attribute. A custom popup does not support display of another popup. <br>The position attribute cannot be used for the first-layer container in the builder. <br>If the position attribute is used, the popup will not be displayed. <br>If a custom component is used in the builder, the aboutToAppear and aboutToDisappear lifecycle callbacks of the custom component are irrelevant to the visibility of the popup. As such, the lifecycle of the custom component cannot be used to determine whether the popup is displayed or not. &lt;/p&gt;

**类型：** CustomBuilder

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-builder: CustomBuilder--><!--Device-CustomPopupOptions-builder: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colorMode

```TypeScript
colorMode?: AnchoredColorMode
```

Define the popup theme color mode.

**类型：** [AnchoredColorMode](arkts-na-common-anchoredcolormode-e.md)

**默认值：** AnchoredColorMode.FOLLOW_TARGET

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-colorMode?: AnchoredColorMode--><!--Device-CustomPopupOptions-colorMode?: AnchoredColorMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableArrow

```TypeScript
enableArrow?: boolean
```

whether show arrow

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-enableArrow?: boolean--><!--Device-CustomPopupOptions-enableArrow?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Determine if it is compatible popup's half folded.

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-enableHoverMode?: boolean--><!--Device-CustomPopupOptions-enableHoverMode?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## focusable

```TypeScript
focusable?: boolean
```

Set popup focusable

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-focusable?: boolean--><!--Device-CustomPopupOptions-focusable?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## followTransformOfTarget

```TypeScript
followTransformOfTarget?: boolean
```

Determine if popup can follow the target node when it has rotation or scale.

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-followTransformOfTarget?: boolean--><!--Device-CustomPopupOptions-followTransformOfTarget?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode?: KeyboardAvoidMode
```

Define the popup avoid keyboard mode.

**类型：** [KeyboardAvoidMode](arkts-na-common-keyboardavoidmode-e.md)

**默认值：** KeyboardAvoidMode.NONE

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-keyboardAvoidMode?: KeyboardAvoidMode--><!--Device-CustomPopupOptions-keyboardAvoidMode?: KeyboardAvoidMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelMode

```TypeScript
levelMode?: LevelMode
```

Defines the display level of the popup.

**类型：** [LevelMode](arkts-na-promptaction-levelmode-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-levelMode?: LevelMode--><!--Device-CustomPopupOptions-levelMode?: LevelMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mask

```TypeScript
mask?: boolean | PopupMaskType
```

The mask to block gesture events of popup. When mask is set false, gesture events are not blocked. When mask is set true, gesture events are blocked and mask color is transparent.

**类型：** boolean \| [PopupMaskType](arkts-na-common-popupmasktype-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-mask?: boolean | PopupMaskType--><!--Device-CustomPopupOptions-mask?: boolean | PopupMaskType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Position
```

Sets the position offset of the popup.

**类型：** [Position](../../apis-arkui/arkts-apis/arkts-arkui-position-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-offset?: Position--><!--Device-CustomPopupOptions-offset?: Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: VoidCallback
```

Callback function when the popup appears.

**类型：** [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-onDidAppear?: VoidCallback--><!--Device-CustomPopupOptions-onDidAppear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: VoidCallback
```

Callback function when the popup disappears.

**类型：** [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-onDidDisappear?: VoidCallback--><!--Device-CustomPopupOptions-onDidDisappear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onStateChange

```TypeScript
onStateChange?: PopupStateChangeCallback
```

on State Change

**类型：** [PopupStateChangeCallback](arkts-na-popupstatechangecallback-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-onStateChange?: PopupStateChangeCallback--><!--Device-CustomPopupOptions-onStateChange?: PopupStateChangeCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: VoidCallback
```

Callback function before the popup openAnimation starts.

**类型：** [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-onWillAppear?: VoidCallback--><!--Device-CustomPopupOptions-onWillAppear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: VoidCallback
```

Callback function before the popup closeAnimation starts.

**类型：** [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-onWillDisappear?: VoidCallback--><!--Device-CustomPopupOptions-onWillDisappear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: boolean | Callback<DismissPopupAction>
```

Whether to perform dismissal event interception and interception callback. 1. If this parameter is set to false, the system does not respond to the dismissal event initiated by touching the Back button, swiping left or right on the screen, or pressing the Esc key; and the system dismisses the popup only when show is set to false. If this parameter is set to true, the system responds to the dismissal event as expected. 2. If this parameter is set to a function, the dismissal event is intercepted and the callback function is executed. &lt;p&gt;&lt;strong&gt;NOTE&lt;/strong&gt;: <br>No more onWillDismiss callback is allowed in an onWillDismiss callback. &lt;/p&gt;

**类型：** boolean \| [Callback](arkts-na-callback-t.md)&lt;[DismissPopupAction](arkts-na-common-dismisspopupaction-i.md)&gt;

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-onWillDismiss?: boolean | Callback<DismissPopupAction>--><!--Device-CustomPopupOptions-onWillDismiss?: boolean | Callback<DismissPopupAction>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## outlineLinearGradient

```TypeScript
outlineLinearGradient?: PopupBorderLinearGradient
```

The LinearGradient of popup's outline.

**类型：** [PopupBorderLinearGradient](arkts-na-common-popupborderlineargradient-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-outlineLinearGradient?: PopupBorderLinearGradient--><!--Device-CustomPopupOptions-outlineLinearGradient?: PopupBorderLinearGradient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## outlineWidth

```TypeScript
outlineWidth?: Dimension
```

The width of popup's outline.

**类型：** [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-outlineWidth?: Dimension--><!--Device-CustomPopupOptions-outlineWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placement

```TypeScript
placement?: Placement
```

Preferred position of the popup. If the set position is insufficient for holding the popup, it will be automatically adjusted.

**类型：** [Placement](../../apis-arkui/arkts-apis/arkts-arkui-placement-e.md)

**默认值：** Placement.Bottom

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-placement?: Placement--><!--Device-CustomPopupOptions-placement?: Placement-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## popupColor

```TypeScript
popupColor?: Color | string | Resource | long
```

Color of the popup. To remove the background blur, set backgroundBlurStyle to BlurStyle.NONE.

**类型：** [Color](../../apis-arkui/arkts-apis/arkts-arkui-color-e.md) \| string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) \| long

**默认值：** TRANSPARENT plus COMPONENT_ULTRA_THICK

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-popupColor?: Color | string | Resource | long--><!--Device-CustomPopupOptions-popupColor?: Color | string | Resource | long-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius?: Dimension
```

Rounded corner radius of the popup.

**类型：** [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md)

**默认值：** 20.0_vp.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-radius?: Dimension--><!--Device-CustomPopupOptions-radius?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

Popup shadow.

**类型：** [ShadowOptions](arkts-na-common-shadowoptions-i.md) \| [ShadowStyle](arkts-na-common-shadowstyle-e.md)

**默认值：** ShadowStyle.OUTER_DEFAULT_MD.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-CustomPopupOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

Whether to display in the sub window.

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-showInSubWindow?: boolean--><!--Device-CustomPopupOptions-showInSubWindow?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

Set system-styled materials for popup. Different materials have different effects, which can influence the backgroundColor, border, shadow, and other visual attributes of popup.

**类型：** [SystemUiMaterial](arkts-na-systemuimaterial-t-sys.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-systemMaterial?: SystemUiMaterial--><!--Device-CustomPopupOptions-systemMaterial?: SystemUiMaterial-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## targetSpace

```TypeScript
targetSpace?: Length
```

Sets the space of between the popup and target.

**类型：** [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-targetSpace?: Length--><!--Device-CustomPopupOptions-targetSpace?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition?: TransitionEffect
```

Defines the transition effect of popup opening and closing

**类型：** [TransitionEffect](arkts-na-common-transitioneffect-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-transition?: TransitionEffect--><!--Device-CustomPopupOptions-transition?: TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

Width of the popup.

**类型：** [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomPopupOptions-width?: Dimension--><!--Device-CustomPopupOptions-width?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

