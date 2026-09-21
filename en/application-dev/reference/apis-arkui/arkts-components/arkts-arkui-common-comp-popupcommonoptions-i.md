# PopupCommonOptions

```TypeScript
declare interface PopupCommonOptions
```

Configures the parameters of a popup. You can use the [getPromptAction()](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getpromptaction) method in [UIContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [PromptAction](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) object, and then call the attributes of **options** when [openPopup](../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#openpopup18) or [updatePopup](../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#updatepopup18) is called.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onStateChange

```TypeScript
onStateChange?: PopupStateChangeCallback
```

Represents the callback invoked when the popup state changes.

**NOTE:** 

[updatePopup](../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#updatepopup18) cannot be used for update.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## arrowHeight

```TypeScript
arrowHeight?: Dimension
```

Arrow height.

Default value: **8**

Unit: vp

**NOTE:** 

Percentage values are not supported.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 8.0_vp.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## arrowOffset

```TypeScript
arrowOffset?: Length
```

Offset of the popup arrow relative to the popup.

When the arrow is at the top or bottom of the popup: The value **0** indicates that the arrow is located on the leftmost, and any other value indicates the distance from the arrow to the leftmost; the arrow is centered by default.

When the arrow is on the left or right side of the popup: The value indicates the distance from the arrow to the top; the arrow is centered by default.

When the popup is displayed on either edge of the screen, it automatically adjusts horizontally. When the value is **0**, the arrow always points to the bound component.

Unit: vp

**NOTE:** 

1. If **arrowOffset** is not set, the distance between the popup arrow and the four corners must be no less than the corner radius.
2. If **arrowPointPosition** is set, **arrowOffset** does not take effect.
3. Percentage values are not supported.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## arrowPointPosition

```TypeScript
arrowPointPosition?: ArrowPointPosition
```

Position of the tooltip arrow relative to its parent component. Available positions are **Start**, **Center**, and **End**, in both vertical and horizontal directions. All these positions are within the parent component area.

Default value: **ArrowPointPosition.CENTER**

**Type:** [ArrowPointPosition](../arkts-apis/arkts-arkui-arrowpointposition-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## arrowWidth

```TypeScript
arrowWidth?: Dimension
```

Arrow thickness. If the arrow thickness exceeds the length of the edge minus twice the size of the popup rounded corner, the arrow is not drawn.

Default value: **16**

Unit: vp

**NOTE:** 

Percentage values are not supported.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 16.0_vp.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoCancel

```TypeScript
autoCancel?: boolean
```

Whether to automatically dismiss the popup when there is a page operation. The value **true** means to automatically dismiss the popup when there is a page operation, and **false** means the opposite.

Default value: **true**

**Type:** boolean

**Default:** true

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## avoidTarget

```TypeScript
avoidTarget?: AvoidanceMode
```

Whether the popup covers the pointing component during avoidance.

Default value: **AvoidanceMode.COVER_TARGET**

**Type:** [AvoidanceMode](arkts-arkui-select-comp-avoidancemode-e.md)

**Default:** AvoidanceMode.COVER_TARGET

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur style of the popup.

Default value: **BlurStyle.COMPONENT_ULTRA_THICK**

**Type:** [BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)

**Default:** BlurStyle.COMPONENT_ULTRA_THICK

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Defines the popup's background blur style with options

**Type:** [BackgroundBlurStyleOptions](arkts-arkui-common-comp-backgroundblurstyleoptions-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

Defines the popup's background effect with options

**Type:** [BackgroundEffectOptions](arkts-arkui-common-comp-backgroundeffectoptions-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderLinearGradient

```TypeScript
borderLinearGradient?: PopupBorderLinearGradient
```

Linear gradient color of the inner outline of the popup.

**NOTE:** 

1. If **borderLinearGradient** is not set or set to **null** or **undefined**, the linear gradient color of the inner outline does not take effect.
2. When **borderLinearGradient** is set, the default value of **direction** is **GradientDirection.Bottom**.

**Type:** [PopupBorderLinearGradient](arkts-arkui-common-comp-popupborderlineargradient-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Dimension
```

Width of the inner outline of the popup.

Default value: **1**

Unit: vp

**NOTE:** 

1. Percentage values are not supported. If a percentage value is set, the value **0** is used.
2. If no inner outline is set, this parameter must be used together with **borderLinearGradient**.
3. For double outlines, it is recommended that the inner outline width should not exceed 10 vp.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## colorMode

```TypeScript
colorMode?: AnchoredColorMode
```

Define the popup theme color mode.

**Type:** [AnchoredColorMode](arkts-arkui-common-comp-anchoredcolormode-e.md)

**Default:** AnchoredColorMode.FOLLOW_TARGET

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableArrow

```TypeScript
enableArrow?: boolean
```

Whether to display the arrow. The value **true** means to display the arrow, and **false** means the opposite.

If the position set for the popup is not large enough, the arrow will not be displayed. For example, if **placement** is set to **Left**, and the popup height is less than the sum of the arrow width (32 vp) and twice the popup corner radius (48 vp), that is, 80 vp, the arrow will not be displayed.

Default value: **true**

**Type:** boolean

**Default:** true

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Whether the popup responds when the device is in hover mode (semi-folded state), that is, whether it triggers avoidance of the crease area in hover mode.

Default value: **false** (**true** for 2-in-1 devices by default). If this parameter is not set or set to an invalid value, the default value is used.

**NOTE:** 

1. If the popup position is within the crease area in hover mode, it will not respond in hover mode.
2. This parameter is supported on 2-in-1 devices since API version 20.
3. This parameter only takes effect in window waterfall mode for 2-in-1 devices.

**Type:** boolean

**Default:** false

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## focusable

```TypeScript
focusable?: boolean
```

Whether the popup obtains focus when displayed.

**true**: The popup can obtain the focus; **false**: The popup cannot obtain the focus.

Default value: **false**

**NOTE:** 

[updatePopup](../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#updatepopup18) cannot be used for update.

**Type:** boolean

**Default:** false

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## followTransformOfTarget

```TypeScript
followTransformOfTarget?: boolean
```

Whether the popup aligns with the transformed position of the target when the target component or its parent container has transformations (such as rotation and scaling).

**true**: The popup aligns with the transformed position of the target; **false**: The popup does not track such transformations, which may result in incorrect display.

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## levelMode

```TypeScript
levelMode?: LevelMode
```

Defines the display level of the popup.

**Type:** LevelMode

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## mask

```TypeScript
mask?: boolean | PopupMaskType
```

Whether to apply a mask with the specified color to the popup. The value **false** means that no mask is applied, **true** means that a transparent mask is applied, and **PopupMaskType** means that a mask with the specified color is applied. Default value: **true**

**Type:** boolean &#124; [PopupMaskType](arkts-arkui-common-comp-popupmasktype-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Position
```

Offset of the popup relative to the display position specified by **placement**.

**NOTE:** 

Percentage values are not supported.

Default value: **{x:0, y:0}**

Unit: vp

**Type:** Position

**Default:** { x: 0, y: 0 }

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: boolean | Callback<DismissPopupAction>
```

Interactive dismissal behavior. The default value is **true**, meaning that the popup responds to clicks, swipes (left or right), and the back button.

1. For the boolean type, if this parameter is set to **false**, the popup ignores clicks, swipes, back button, route navigation, and **Esc** key events, and can only be dismissed by setting the **show** parameter to **false**; if this parameter is set to **true**, the popup responds to dismissal events.
2. If this parameter is set to a function, the dismissal event is intercepted and the callback function is executed. For swipes, back button, route navigation, and the **Esc** key, the value of **reason** returned in the callback function is **PRESS_BACK**. For clicks, the value is **TOUCH_OUTSIDE**.

**NOTE:** 

1. No more **onWillDismiss** callback is allowed in an **onWillDismiss** callback.
2. [updatePopup](../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#updatepopup18) cannot be used for update.

**Type:** boolean &#124; [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[DismissPopupAction](arkts-arkui-common-comp-dismisspopupaction-i.md)&gt;

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## outlineLinearGradient

```TypeScript
outlineLinearGradient?: PopupBorderLinearGradient
```

Linear gradient color of the outer outline of the popup.

**NOTE:** 

1. If **outlineLinearGradient** is not set or set to **null** or **undefined**, the linear gradient color of the outer outline does not take effect.
2. When **outlineLinearGradient** is set, the default value of **direction** is **GradientDirection.Bottom**.

**Type:** [PopupBorderLinearGradient](arkts-arkui-common-comp-popupborderlineargradient-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## outlineWidth

```TypeScript
outlineWidth?: Dimension
```

Width of the outer outline of the popup.

Default value: **1**

Unit: vp

**NOTE:** 

1. Percentage values are not supported. If a percentage value is set, the value **0** is used.
2. If the outer outline is not set, this parameter must be used together with **outlineLinearGradient**.
3. For double outlines, it is recommended that the outer outline width should not exceed 10 vp.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placement

```TypeScript
placement?: Placement
```

Preferred position of the popup. If the set position is insufficient for holding the popup, it will be automatically adjusted.

Default value: **Placement.Bottom**

**Type:** [Placement](../arkts-apis/arkts-arkui-placement-e.md)

**Default:** Placement.Bottom

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## popupColor

```TypeScript
popupColor?: ResourceColor
```

Color of the popup. To remove the background blur, set **backgroundBlurStyle** to **BlurStyle.NONE**. Default value: TRANSPARENT plus [COMPONENT_ULTRA_THICK](arkts-arkui-common-comp-blurstyle-e.md)

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius?: Dimension
```

Rounded corner radius of the popup.

Default value: **20**

Unit: vp

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 20.0_vp.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

Popup shadow.

Default value: **ShadowStyle.OUTER_DEFAULT_MD**

**Type:** [ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md) &#124; [ShadowStyle](arkts-arkui-common-comp-shadowstyle-e.md)

**Default:** ShadowStyle.OUTER_DEFAULT_MD.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

Whether to show the popup in a subwindow. The value **true** means to show the popup in a subwindow, and **false** means to show the popup in the main window.

Default value: **false**

**NOTE:** 

[updatePopup](../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#updatepopup18) cannot be used for update.

**Type:** boolean

**Default:** false

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

Set system-styled materials for popup. Different materials have different effects, which can influence the backgroundColor, border, shadow, and other visual attributes of popup.

**Type:** [SystemUiMaterial](arkts-arkui-common-comp-systemuimaterial-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## targetSpace

```TypeScript
targetSpace?: Length
```

Spacing between the popup and the host node. Percentage values are not supported.

Default value: **8**

Unit: vp

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition?: TransitionEffect
```

Transition animations for the entrance and exit of the popup.

**NOTE:** 

1. If this parameter is not set, the default effect is used.
2. Touching the back button during the entrance animation interrupts it and starts the exit animation. The final effect is one obtained after the curves of the entrance and exit animations are combined.
3. Touching the back button during the exit animation does not affect the animation playback; the back button is unresponsive.
4. [updatePopup](../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#updatepopup18) cannot be used for update.

**Type:** [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

Width of the popup.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
