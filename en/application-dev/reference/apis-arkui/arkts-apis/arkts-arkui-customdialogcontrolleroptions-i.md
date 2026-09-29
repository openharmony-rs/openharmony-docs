# CustomDialogControllerOptions

```TypeScript
declare interface CustomDialogControllerOptions
```

Defines the style of the custom dialog box.

> **NOTE:** 
> 
> - Pressing the Back or ESC key closes the dialog box.
> 
> - If the dialog box reaches its maximum allowable height on the screen when avoiding the soft keyboard, it reduces its height to fit.
> 
> It should be noted that this height adjustment is applied to the outermost container. If a child component within
> this container has been assigned a larger fixed height, since the container does not clip its content by default,
> parts of the dialog box may still be displayed off-screen.
> 
> - Use the custom dialog box to contain simple alert messages only. Do not use it as a page. When the dialog box avoids the soft keyboard, there is a 16 vp safe spacing between the two.
> 
> - For optimal visual experience, dialog box display and closing include default animations, though the animation duration may vary by device.
> 
> Note: During animation playback, the page does not respond to touch, swipe, or click interactions. To disable
> default dialog box animations, set **duration** of both **openAnimation** and **closeAnimation** to **0**.
> 
> - In ArkUI, dialog boxes do not close automatically when you switch pages unless you manually call **close**. To enable a dialog box to be dismissed during page navigation.

**Since:** 7

<!--Device-unnamed-declare interface CustomDialogControllerOptions--><!--Device-unnamed-declare interface CustomDialogControllerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cancel

```TypeScript
cancel?: () => void
```

Callback invoked when the dialog box is closed after the Back button or mask is touched or the Esc key is pressed.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomDialogControllerOptions-cancel?: () => void--><!--Device-CustomDialogControllerOptions-cancel?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: DialogAlignment
```

Alignment mode of the dialog box in the vertical direction.

Default value: **DialogAlignment.Default**

**Type:** [DialogAlignment](arkts-arkui-dialogalignment-e.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomDialogControllerOptions-alignment?: DialogAlignment--><!--Device-CustomDialogControllerOptions-alignment?: DialogAlignment-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoCancel

```TypeScript
autoCancel?: boolean
```

Whether to close the dialog box when the mask is touched. The value **true** means to close the dialog box when the mask is touched, and **false** means the opposite.

Default value: **true**

**Type:** boolean

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomDialogControllerOptions-autoCancel?: boolean--><!--Device-CustomDialogControllerOptions-autoCancel?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur style of the dialog box.

Default value: **BlurStyle.NONE** (API version 26.0.0 and later); **BlurStyle.COMPONENT_ULTRA_THICK** (earlier than API version 26.0.0)

**NOTE:** 

Setting this parameter to **BlurStyle.NONE** disables the background blur. When **backgroundBlurStyle** is set to a value other than **NONE**, do not set **backgroundColor**. If you do, the color display may not produce the expected visual effect.

**Type:** [BlurStyle](../arkts-components/arkts-arkui-common-comp-blurstyle-e.md)

**Default:** BlurStyle.COMPONENT_ULTRA_THICK

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomDialogControllerOptions-backgroundBlurStyle?: BlurStyle--><!--Device-CustomDialogControllerOptions-backgroundBlurStyle?: BlurStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Options for customizing the background blur style. For details about the default value, see **BackgroundBlurStyleOptions**.

**Type:** [BackgroundBlurStyleOptions](../arkts-components/arkts-arkui-common-comp-backgroundblurstyleoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-CustomDialogControllerOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-CustomDialogControllerOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Background color of the dialog box.

Default value: **Color.Transparent**

**NOTE:** 

If the content builder also has the background color set, the background color set here will be overridden by the background color of the content builder.

The background color will be visually combined with the blur effect when both properties are set. If the resulting effect does not match your design requirements, you can disable the blur effect entirely by explicitly setting the **backgroundBlurStyle** property to **BlurStyle.NONE**.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomDialogControllerOptions-backgroundColor?: ResourceColor--><!--Device-CustomDialogControllerOptions-backgroundColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

Options for customizing the background effect. For details about the default value, see **BackgroundEffectOptions**.

**Type:** [BackgroundEffectOptions](../arkts-components/arkts-arkui-common-comp-backgroundeffectoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-CustomDialogControllerOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-CustomDialogControllerOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ResourceColor | EdgeColors
```

Border color of the dialog box.

Default value: **Color.Black**

**borderColor** must be used with **borderWidth** in pairs.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md) &#124; EdgeColors

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomDialogControllerOptions-borderColor?: ResourceColor | EdgeColors--><!--Device-CustomDialogControllerOptions-borderColor?: ResourceColor | EdgeColors-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderStyle

```TypeScript
borderStyle?: BorderStyle | EdgeStyles
```

Border style of the dialog box.

Default value: **BorderStyle.Solid**

**borderStyle** must be used with **borderWidth** in pairs.

**Type:** [BorderStyle](arkts-arkui-borderstyle-e.md) &#124; EdgeStyles

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomDialogControllerOptions-borderStyle?: BorderStyle | EdgeStyles--><!--Device-CustomDialogControllerOptions-borderStyle?: BorderStyle | EdgeStyles-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Dimension | EdgeWidths
```

Border width of the dialog box.

You can set the width for all four sides or set separate widths for individual sides.

Default value: **0**

When set to a percentage, the value defines the border width as a percentage of the parent dialog box's width.

If the left and right borders are greater than its width, or the top and bottom borders are greater than its height, the dialog box may not display as expected.

**Type:** [Dimension](arkts-arkui-dimension-t.md) &#124; EdgeWidths

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomDialogControllerOptions-borderWidth?: Dimension | EdgeWidths--><!--Device-CustomDialogControllerOptions-borderWidth?: Dimension | EdgeWidths-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder: any
```

Builder of the custom dialog box content.

**NOTE:** 

If the builder uses a callback as the input parameter, as in **builder: custombuilder({ callback: ()=&gt; {...}})**, pay attention to the binding of **this**.

To listen for data changes in the builder, use the @Link or @Consume decorator; other decorators, such as @Prop and @ObjectLink, do not apply.

**Type:** any

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomDialogControllerOptions-builder: any--><!--Device-CustomDialogControllerOptions-builder: any-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## closeAnimation

```TypeScript
closeAnimation?: AnimateParam
```

Parameters for defining the close animation of the dialog box.

**NOTE:** 

**tempo**: The default value is **1**; a value less than or equal to 0 is handled as the default value.

**iterations**: The default value is **1**, indicating that the animation is played once; any other value is handled as the default value.

**playMode**: The default value is **PlayMode.Normal**; any other value is handled as the default value.

For page transition, you are advised to use the default close animation.

**Type:** [AnimateParam](../arkts-components/arkts-arkui-common-comp-animateparam-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomDialogControllerOptions-closeAnimation?: AnimateParam--><!--Device-CustomDialogControllerOptions-closeAnimation?: AnimateParam-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cornerRadius

```TypeScript
cornerRadius?: Dimension | BorderRadiuses
```

Rounded corner radius of the background.

You can set separate radii for the four corners.

Default value: **{ topLeft: '32vp', topRight: '32vp', bottomLeft: '32vp', bottomRight: '32vp' }**

Note: The default corner radius of the background is 32 vp. This attribute must be used together with the [borderRadius](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#borderradius) attribute.

**Type:** [Dimension](arkts-arkui-dimension-t.md) &#124; [BorderRadiuses](arkts-arkui-borderradiuses-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomDialogControllerOptions-cornerRadius?: Dimension | BorderRadiuses--><!--Device-CustomDialogControllerOptions-cornerRadius?: Dimension | BorderRadiuses-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## customStyle

```TypeScript
customStyle?: boolean
```

Whether to use a custom style for the dialog box. **true** means a custom style cannot be used for the dialog box, and **false** means the opposite.

Default value: **false**

When this parameter is set to **false**:

1. The default rounded corner radius is 32 vp.
2. If the width and height of the dialog box are not set, the dialog box automatically adapts its width to the grid system and its height to the custom content node.
3. The set width of the dialog box cannot exceed the maximum width in the default style (100% width for a custom node), and the set height cannot exceed the maximum height (100% height for a custom node).
4. Due to safe area constraints, the dialog box display area excludes safe areas. For example, on PC/2-in-1 devices, it avoids screen edges and window title bars.

When this parameter is set to **true**:

1. The rounded corner radius is 0, and the background color is transparent.
2. The width, height, border width, border style, border color, and shadow width cannot be set for the dialog box.
3. The dialog box display area covers the entire screen.

**Type:** boolean

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomDialogControllerOptions-customStyle?: boolean--><!--Device-CustomDialogControllerOptions-customStyle?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayModeInSubWindow

```TypeScript
displayModeInSubWindow?: DialogDisplayMode
```

Display mode of the dialog box in the subwindow.

Default value: **DialogDisplayMode.SCREEN_BASED**

**NOTE:** 

This parameter is valid only when **showInSubWindow** is set to **true**.

**Type:** [DialogDisplayMode](arkts-arkui-dialogdisplaymode-e.md)

**Default:** DialogDisplayMode.SCREEN_BASED

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CustomDialogControllerOptions-displayModeInSubWindow?: DialogDisplayMode--><!--Device-CustomDialogControllerOptions-displayModeInSubWindow?: DialogDisplayMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Whether to respond when the device is in semi-folded mode. The value **true** means to respond when the device is in semi-folded mode.

Default value: **false**, meaning not to enable the hover state.

**NOTE:** 

For a PC or 2-in-1 device, the dialog box is displayed on the upper half of the screen by default when **enableHoverMode** is set to **true**. You can set **hoverModeArea** to display the dialog box on the lower half of the screen. For other devices, the dialog box is displayed on the lower half of the screen by default when **enableHoverMode** is set to **true**. You can set **hoverModeArea** to display the dialog box on the upper half of the screen.

**Type:** boolean

**Default:** false

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-CustomDialogControllerOptions-enableHoverMode?: boolean--><!--Device-CustomDialogControllerOptions-enableHoverMode?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## focusable

```TypeScript
focusable?: boolean
```

Whether the dialog box can gain focus. **true**: The dialog box can gain focus. **false**: The dialog box cannot gain focus.

Default value: **true**

**NOTE:** 

Only dialog boxes that are displayed on top of the current window can gain focus.

**Type:** boolean

**Default:** true

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-CustomDialogControllerOptions-focusable?: boolean--><!--Device-CustomDialogControllerOptions-focusable?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## gridCount

```TypeScript
gridCount?: number
```

Number of grid columns occupied by the dialog box.

The default value is subject to the window size, and the maximum value is the maximum number of columns supported by the system. If this parameter is set to an invalid value, the default value is used.

Value range: an integer no less than 0

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomDialogControllerOptions-gridCount?: number--><!--Device-CustomDialogControllerOptions-gridCount?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Dimension
```

Height of the dialog box.

**NOTE:** 

- Default maximum height of the dialog box: 0.9 x (Window height – Safe area)  
- When this parameter is set to a percentage, the reference height of the dialog box is the height of the window  
where the dialog box is located minus the safe area. You can decrease or increase the height as needed.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomDialogControllerOptions-height?: Dimension--><!--Device-CustomDialogControllerOptions-height?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

Display area of the dialog box in the hover state.

Default value: **HoverModeAreaType.BOTTOM_SCREEN**

**Type:** [HoverModeAreaType](../arkts-components/arkts-arkui-common-comp-hovermodeareatype-e.md)

**Default:** HoverModeAreaType.BOTTOM_SCREEN

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-CustomDialogControllerOptions-hoverModeArea?: HoverModeAreaType--><!--Device-CustomDialogControllerOptions-hoverModeArea?: HoverModeAreaType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## immersiveMode

```TypeScript
immersiveMode?: ImmersiveMode
```

Overlay effect for the page-level dialog box.

**NOTE:** 

- Default value: **ImmersiveMode.DEFAULT**  
- This parameter takes effect only when **levelMode** is set to **LevelMode.EMBEDDED**.

**Type:** [ImmersiveMode](arkts-arkui-immersivemode-t.md)

**Default:** ImmersiveMode.DEFAULT

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-CustomDialogControllerOptions-immersiveMode?: ImmersiveMode--><!--Device-CustomDialogControllerOptions-immersiveMode?: ImmersiveMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isModal

```TypeScript
isModal?: boolean
```

Whether the dialog box is a modal, which has a mask applied and does not allow for interaction with other components around the menu.

**true**: The dialog box is a modal.

**false**: The dialog box is not a modal.

Default value: **true**

**Type:** boolean

**Default:** true

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomDialogControllerOptions-isModal?: boolean--><!--Device-CustomDialogControllerOptions-isModal?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidDistance

```TypeScript
keyboardAvoidDistance?: LengthMetrics
```

Distance between the dialog box and the keyboard after keyboard avoidance is applied.

**NOTE:** 

- Default value: **16vp**  
- Default unit: vp  
- This parameter takes effect only when **keyboardAvoidMode** is set to **DEFAULT**.

**Type:** [LengthMetrics](arkts-arkui-lengthmetrics-t.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-CustomDialogControllerOptions-keyboardAvoidDistance?: LengthMetrics--><!--Device-CustomDialogControllerOptions-keyboardAvoidDistance?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode?: KeyboardAvoidMode
```

How the dialog box avoids the soft keyboard when it is brought up.

Default value: **KeyboardAvoidMode.DEFAULT**

**Type:** KeyboardAvoidMode

**Default:** KeyboardAvoidMode.DEFAULT

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomDialogControllerOptions-keyboardAvoidMode?: KeyboardAvoidMode--><!--Device-CustomDialogControllerOptions-keyboardAvoidMode?: KeyboardAvoidMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## levelMode

```TypeScript
levelMode?: LevelMode
```

Display level of the dialog box.

**NOTE:** 

- Default value: **LevelMode.OVERLAY.**  
- This parameter takes effect only when **showInSubWindow** is set to **false**.

**Type:** [LevelMode](arkts-arkui-levelmode-t.md)

**Default:** LevelMode.OVERLAY

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-CustomDialogControllerOptions-levelMode?: LevelMode--><!--Device-CustomDialogControllerOptions-levelMode?: LevelMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## levelOrder

```TypeScript
levelOrder?: LevelOrder
```

Display order of the dialog box.

**NOTE:** 

- Default value: **LevelOrder.clamp(0)**  
- Dynamic updating is not supported.

**Type:** [LevelOrder](arkts-arkui-levelorder-t.md)

**Default:** The value returns by LevelOrder.clamp(0)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CustomDialogControllerOptions-levelOrder?: LevelOrder--><!--Device-CustomDialogControllerOptions-levelOrder?: LevelOrder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## levelUniqueId

```TypeScript
levelUniqueId?: number
```

Unique ID of the node under the display level for the page-level dialog box. The unique ID can be obtained via [getUniqueId](arkts-arkui-framenode-c.md#getuniqueid).

Value range: a number no less than 0

**NOTE:** 

- This parameter takes effect only when **levelMode** is set to **LevelMode.EMBEDDED**.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-CustomDialogControllerOptions-levelUniqueId?: number--><!--Device-CustomDialogControllerOptions-levelUniqueId?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskColor

```TypeScript
maskColor?: ResourceColor
```

Custom mask color.

Default value: **0x33000000**.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomDialogControllerOptions-maskColor?: ResourceColor--><!--Device-CustomDialogControllerOptions-maskColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

Mask area of the dialog box. Events outside the mask area are transparently transmitted, and events within the mask area are not.

Default value: **{ x: 0, y: 0, width: '100%', height: '100%' }**

**NOTE:** 

**maskRect** does not take effect when **showInSubWindow** is set to **true**.

**Type:** [Rectangle](../arkts-components/arkts-arkui-common-comp-rectangle-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomDialogControllerOptions-maskRect?: Rectangle--><!--Device-CustomDialogControllerOptions-maskRect?: Rectangle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

Offset of the dialog box relative to the alignment position.

Default value: **{dx: 0, dy: 0}**

**Type:** [Offset](arkts-arkui-offset-t.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomDialogControllerOptions-offset?: Offset--><!--Device-CustomDialogControllerOptions-offset?: Offset-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: Callback<void>
```

Event callback after the dialog box appears.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; onWillDisappear &gt; onDidDisappear.
2. You can set the callback event for changing the dialog box display effect in **onDidAppear**.
The settings take effect next time the dialog box appears.
3. When a dialog box is dismissed immediately after being shown,  
**onWillDisappear** may be triggered before **onDidAppear**.
4. If the dialog box is dismissed before its entrance animation is finished, the animation will be interrupted,
and **onDidAppear** will not be triggered.

**Type:** Callback&lt;void&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-CustomDialogControllerOptions-onDidAppear?: Callback<void>--><!--Device-CustomDialogControllerOptions-onDidAppear?: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: Callback<void>
```

Event callback after the dialog box disappears.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; onWillDisappear &gt; onDidDisappear.

**Type:** Callback&lt;void&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-CustomDialogControllerOptions-onDidDisappear?: Callback<void>--><!--Device-CustomDialogControllerOptions-onDidDisappear?: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: Callback<void>
```

Event callback when the dialog box is about to appear.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; onWillDisappear &gt; onDidDisappear.
2. You can set the callback event for changing the dialog box display effect in **onWillAppear**. The settings take effect next time the dialog box appears.

**Type:** Callback&lt;void&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-CustomDialogControllerOptions-onWillAppear?: Callback<void>--><!--Device-CustomDialogControllerOptions-onWillAppear?: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: Callback<void>
```

Event callback when the dialog box is about to disappear.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; onWillDisappear &gt; onDidDisappear.

**Type:** Callback&lt;void&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-CustomDialogControllerOptions-onWillDisappear?: Callback<void>--><!--Device-CustomDialogControllerOptions-onWillDisappear?: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: Callback<DismissDialogAction>
```

Callback for interactive closure of the dialog box.

**NOTE:** 

1. If this callback is registered, the dialog box will not be dismissed immediately after
the user touches the mask or the Back button, presses the Esc key, or swipes left or right on the screen. The **reason** parameter in the callback is used to determine whether the dialog box can be closed. The reason returned by the component does not support the value **CLOSE_BUTTON**.
2. In the **onWillDismiss** callback, another **onWillDismiss** callback is not allowed.

**Type:** Callback&lt;[DismissDialogAction](arkts-arkui-dismissdialogaction-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomDialogControllerOptions-onWillDismiss?: Callback<DismissDialogAction>--><!--Device-CustomDialogControllerOptions-onWillDismiss?: Callback<DismissDialogAction>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## openAnimation

```TypeScript
openAnimation?: AnimateParam
```

Parameters for defining the open animation of the dialog box.

**NOTE:** 

**tempo**: The default value is **1**; a value less than or equal to 0 is handled as the default value.

**iterations**: The default value is **1**, indicating that the animation is played once; any other value is handled as the default value.

**playMode**: The default value is **PlayMode.Normal**; any other value is handled as the default value.

**Type:** [AnimateParam](../arkts-components/arkts-arkui-common-comp-animateparam-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomDialogControllerOptions-openAnimation?: AnimateParam--><!--Device-CustomDialogControllerOptions-openAnimation?: AnimateParam-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

Shadow of the dialog box.

Default value on 2-in-1 devices: **ShadowStyle.OUTER_FLOATING_MD** when the dialog box is focused and **ShadowStyle.OUTER_FLOATING_SM** otherwise. On other devices, the dialog box has no shadow by default.

**Type:** [ShadowOptions](../arkts-components/arkts-arkui-common-comp-shadowoptions-i.md) &#124; [ShadowStyle](../arkts-components/arkts-arkui-common-comp-shadowstyle-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomDialogControllerOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-CustomDialogControllerOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

Whether to show the dialog box in a subwindow when the dialog box needs to be displayed outside the main window. **true**: The dialog box is shown in a subwindow.

Default value: **false**

**NOTE:** 

A dialog box whose **showInSubWindow** attribute is **true** cannot trigger the display of another dialog box whose **showInSubWindow** attribute is also **true**. Avoid using the **CalendarPicker**, **CalendarPickerDialog**, **DatePickerDialog**, **TextPickerDialog**, **TimePickerDialog**, and **Toast** components in the dialog box where **showInSubWindow** is set to **true**, as the dialog box may affect the behavior of these components.

**Type:** boolean

**Default:** 
- API version 11+: false

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomDialogControllerOptions-showInSubWindow?: boolean--><!--Device-CustomDialogControllerOptions-showInSubWindow?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

System material of the dialog box.

**NOTE:** 

- Default value: ImmersiveMaterial object whose **style** in [ImmersiveOptions](arkts-arkui-uimaterial-immersiveoptions-i.md) is  
**ImmersiveStyle.ULTRA_THICK** If this parameter is set to **undefined**, the default value is used.  
- Different materials produce distinct effects. This API impacts the following attributes:[backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), [backgroundBlurStyle](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundblurstyle), [backgroundEffect](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundeffect), [borderColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bordercolor), [borderWidth](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#borderwidth), and [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow). When the system material is set, the aforementioned attributes do not take effect.

**Type:** [SystemUiMaterial](../arkts-components/arkts-arkui-common-comp-systemuimaterial-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CustomDialogControllerOptions-systemMaterial?: SystemUiMaterial--><!--Device-CustomDialogControllerOptions-systemMaterial?: SystemUiMaterial-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

Width of the dialog box.

**NOTE:** 

- Default maximum width of the dialog box: 400 vp  
- When this parameter is set to a percentage, the reference width of the dialog box is the width of the window  
where the dialog box is located. You can decrease or increase the width as needed.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomDialogControllerOptions-width?: Dimension--><!--Device-CustomDialogControllerOptions-width?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
