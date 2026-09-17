# CustomPopupOptions

Provides information for displaying a custom popup.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onStateChange

```TypeScript
onStateChange?: (event: {
    /**
     * is Visible.
     *
     * @type { boolean }
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @stagemodelonly
     * @crossplatform
     * @since 10
     */
    /**
     * is Visible.
     *
     * @type { boolean }
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @stagemodelonly
     * @crossplatform
     * @atomicservice
     * @since 11
     */
    isVisible: boolean
  }) => void
```

Callback for popup visibility state changes. The parameter indicates the visibility of the popup. It returns **true** when the popup transitions from closed to open, and **false** when the popup transitions from open to closed.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | {     /**      * is Visible.      *      * @type { boolean }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @stagemodelonly      * @crossplatform      * @since 10      */     /**      * is Visible.      *      * @type { boolean }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @stagemodelonly      * @crossplatform      * @atomicservice      * @since 11      */     isVisible: boolean   } | Yes |  |

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

**Default:** 
- API version 11: 8.0_vp.
- API version 12+: 8.0_vp. <p><strong>NOTE</strong>: <br>This parameter cannot be set in percentage. </p>

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## arrowPointPosition

```TypeScript
arrowPointPosition?: ArrowPointPosition
```

Position of the tooltip arrow relative to its parent component. Available positions are **Start**, **Center**, and **End**, in both vertical and horizontal directions. All these positions are within the parent component area.

Default value: **ArrowPointPosition.CENTER**

**Type:** [ArrowPointPosition](../arkts-apis/arkts-arkui-arrowpointposition-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**Default:** 
- API version 11: 16.0_vp.
- API version 12+: 16.0_vp. <p><strong>NOTE</strong>: <br>This parameter cannot be set in percentage. </p>

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoCancel

```TypeScript
autoCancel?: boolean
```

Whether the popup is automatically closed when an operation is performed on the page.

**true**: The popup is automatically closed; **false**: The popup is not automatically closed.

Default value: **true**

**NOTE:** 

To dismiss the popup upon a click on it, place a layout component in the **builder**, place the **Popup** component in the layout component, and set **show** to **false** in the **onClick** event of the layout component.

**Type:** boolean

**Default:** 
- API version 11+: true

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## avoidTarget

```TypeScript
avoidTarget?: AvoidanceMode
```

Whether the popup covers the pointing component during avoidance.

Default value: **AvoidanceMode.COVER_TARGET**

**Type:** [AvoidanceMode](arkts-arkui-avoidancemode-e.md)

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

**Type:** [BlurStyle](arkts-arkui-blurstyle-e.md)

**Default:** BlurStyle.COMPONENT_ULTRA_THICK

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Defines the popup's background blur style with options

**Type:** [BackgroundBlurStyleOptions](arkts-arkui-backgroundblurstyleoptions-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

Defines the popup's background effect with options

**Type:** [BackgroundEffectOptions](arkts-arkui-backgroundeffectoptions-i.md)

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

**Type:** [PopupBorderLinearGradient](arkts-arkui-popupborderlineargradient-i.md)

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

## builder

```TypeScript
builder: CustomBuilder
```

Popup builder.

**NOTE:** 

1. The **Popup** attribute is a universal attribute. A custom popup does not support display of another popup. The **position** attribute cannot be used for the first-layer container in the builder. If the **position** attribute is used, the popup will not be displayed.
2. If a custom component is used in the **builder**, the **aboutToAppear** and **aboutToDisappear** lifecycle callbacks of the custom component are irrelevant to the visibility of the popup. As such, the lifecycle of the custom component cannot be used to determine whether the popup is displayed or not.
3. The **builder** of this constructor can be defined only in UI components, such as the **Builder** function/method or the [build](../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#build) method.

**Type:** [CustomBuilder](arkts-arkui-custombuilder-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## colorMode

```TypeScript
colorMode?: AnchoredColorMode
```

Define the popup theme color mode.

**Type:** [AnchoredColorMode](arkts-arkui-anchoredcolormode-e.md)

**Default:** AnchoredColorMode.FOLLOW_TARGET

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableArrow

```TypeScript
enableArrow?: boolean
```

Whether to display the arrow.

**true**: The arrow is displayed; **false**: The arrow is not displayed.

Since API version 9, if the position set for the popup is not large enough, the arrow will not be displayed. For example, if **placement** is set to **Left**, and the popup height is less than the sum of the arrow width (32 vp) and twice the popup corner radius (48 vp), that is, 80 vp, the arrow will not be displayed.

Default value: **true**

**Type:** boolean

**Default:** 
- API version 11+: true

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**Type:** boolean

**Default:** 
- API version 11: true
- API version 12+: false

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode?: KeyboardAvoidMode
```

Whether to avoid the soft keyboard. By default, the popup does not avoid the soft keyboard. When configured to avoid the soft keyboard, if the popup display space is insufficient, the display mode of the popup changes from being centered over the parent component to being translated and covering the parent component.. In addition, if the popup arrow does not point to the host, the arrow will not be displayed.

Default value: **KeyboardAvoidMode.NONE**

**Type:** [KeyboardAvoidMode](arkts-arkui-keyboardavoidmode-e.md)

**Default:** KeyboardAvoidMode.NONE

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## levelMode

```TypeScript
levelMode?: LevelMode
```

Defines the display level of the popup.

**Type:** [LevelMode](../arkts-apis/arkts-arkui-levelmode-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## mask

```TypeScript
mask?: boolean | { color: ResourceColor }
```

Whether to apply a mask with the specified color to the popup. The value **true** means to apply a transparent mask to the popup, **false** means not to apply a mask to the popup, and a color value means to apply a mask in the corresponding color to the popup. Default value: **true**

**Type:** boolean &#124; { color: ResourceColor }

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskColor

```TypeScript
maskColor?: Color | string | Resource | number
```

Color of the popup mask.

**NOTE:** 

This parameter is deprecated since API version 10. You are advised to use **mask** instead.

**Type:** [Color](../arkts-apis/arkts-arkui-color-e.md) &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; number

**Since:** 8

**Deprecated since:** 10

**Substitutes:** [mask](#mask)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Position
```

Offset of the popup relative to the display position specified by **placement**.

Default value: **{x:0, y:0}**

Unit: vp

**NOTE:** 

Percentage values are not supported.

**Type:** Position

**Default:** 
- API version 11+: { x: 0, y: 0 }

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: boolean | Callback<DismissPopupAction>
```

Interactive dismissal behavior. The default value is **true**, meaning that the popup responds to clicks, swipes (left or right), and the back button.

1. For the boolean type, if this parameter is set to **false**, the popup ignores clicks, swipes, back button, route navigation, and **Esc** key events, and can only be dismissed by setting the **show** parameter to **false**; if this parameter is set to **true**, the popup responds to dismissal events.
2. If this parameter is set to a function, the dismissal event is intercepted and the callback function is executed. For swipes, back button, route navigation, and the **Esc** key, the value of **reason** returned in the callback function is **PRESS_BACK**. For clicks, the value is **TOUCH_OUTSIDE**.

**NOTE:** 

No more **onWillDismiss** callback is allowed in an **onWillDismiss** callback.

**Type:** boolean &#124; [Callback](arkts-arkui-callback-i.md)&lt;[DismissPopupAction](arkts-arkui-dismisspopupaction-i.md)&gt;

**Default:** true

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## outlineLinearGradient

```TypeScript
outlineLinearGradient?: PopupBorderLinearGradient
```

Linear gradient color of the outer outline of the popup.

**NOTE:** 

1. If **outlineLinearGradient** is not set or set to **null** or **undefined**, the linear gradient color of the outer outline does not take effect.
2. When **outlineLinearGradient** is set, the default value of **direction** is **GradientDirection.Bottom**.

**Type:** [PopupBorderLinearGradient](arkts-arkui-popupborderlineargradient-i.md)

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

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## popupColor

```TypeScript
popupColor?: Color | string | Resource | number
```

Color of the popup. To remove the background blur, set **backgroundBlurStyle** to **BlurStyle.NONE**.

The default value varies by API version.

API version 10: **'#4d4d4d'**

API version 11 and later: TRANSPARENT plus [COMPONENT_ULTRA_THICK](arkts-arkui-blurstyle-e.md)

**Type:** [Color](../arkts-apis/arkts-arkui-color-e.md) &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; number

**Default:** 
- API version 10: '#4d4d4d'
- API version 11+: TRANSPARENT plus COMPONENT_ULTRA_THICK

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

Popup shadow.

Default value: **ShadowStyle.OUTER_DEFAULT_MD**

**Type:** [ShadowOptions](arkts-arkui-shadowoptions-i.md) &#124; [ShadowStyle](arkts-arkui-shadowstyle-e.md)

**Default:** ShadowStyle.OUTER_DEFAULT_MD.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

Whether the popup is displayed in the created subwindow.

**true**: The popup is displayed in the created subwindow; **false**: The popup is displayed in the corresponding main window.

Default value: **false**

**Type:** boolean

**Default:** 
- API version 11+: false

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

Set system-styled materials for popup. Different materials have different effects, which can influence the backgroundColor, border, shadow, and other visual attributes of popup.

**Type:** [SystemUiMaterial](arkts-arkui-systemuimaterial-t.md)

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

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition?: TransitionEffect
```

Transition animations for the entrance and exit of the popup.

**NOTE:** 

1. If this parameter is not set, the default entrance and exit animations are used.
2. Touching the back button during the entrance animation interrupts it and starts the exit animation. The final effect is one obtained after the curves of the entrance and exit animations are combined.
3. Touching the back button during the exit animation does not affect the animation playback; the back button is unresponsive.

**Type:** [TransitionEffect](arkts-arkui-transitioneffect-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

Width of the popup. If this parameter is not set or the value is invalid, the popup width is automatically adjusted to adapt to the content width.

Unit: vp

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
