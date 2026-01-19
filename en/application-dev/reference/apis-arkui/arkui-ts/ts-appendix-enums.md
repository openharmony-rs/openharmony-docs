# Enums

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @jiyujia926; @yangfan229-->
<!--Designer: @piggyguy; @s10021109; @yangfan229-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->

>**NOTE**
>
>The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## AccessibilityHoverType<sup>12+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Value| Description                                                        |
| ------------ | - | ------------------------------------------------------------ |
| HOVER_ENTER  | 0 | A finger is pressed.        |
| HOVER_MOVE   | 1 | The touch moves.        |
| HOVER_EXIT   | 2 | A finger is lifted.             |
| HOVER_CANCEL | 3 | The current event is canceled. |

## Alignment

Defines the alignment mode for child elements in the container drawing area.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Value| Description      |
| ----------- | - | -------- |
| TopStart    | 0 | Top start.  |
| Top         | 1 | Horizontally centered on the top. |
| TopEnd      | 2 | Top end.   |
| Start       | 3 | Vertically centered start.|
| Center      | 4 | Horizontally and vertically centered.|
| End         | 5 | Vertically centered end. |
| BottomStart | 6 | Bottom start.  |
| Bottom      | 7 |Horizontally centered on the bottom. |
| BottomEnd   | 8 | Bottom end.   |

## AnimationPropertyType<sup>20+</sup>

Enumerates animatable property types for component animations.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   |  Value  | Description                  |
| ------  | ---- | -------------------- |
| ROTATION | 0 | Rotation angles for the x, y, and z axes. Parameters: 3. Unit: degrees (°).|
| TRANSLATION | 1 | Translation offsets for the x and y axes. Parameters: 2. Unit: px.|
| SCALE | 2 | Scale factors for the x and y axes. Parameters: 2. Value range: (-∞, +∞).|
| OPACITY | 3 | Opacity value. Parameters: 1. Value range: [0, 1].|

## AnimationStatus

Sets the animation playback status.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     |Value| Description       |
| ------- |-| --------- |
| Initial |0| The animation is in the initial state.  |
| Running |1| The animation is being played.|
| Paused  |2| The animation is paused.|
| Stopped |3| The animation is stopped.|

## AppRotation<sup>12+</sup>

Defines the rotation angle of the application's orientation.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    |Value| Description                           |
| ------ |-----| ----------------------------- |
| ROTATION_0 |0| 0 degrees.|
| ROTATION_90 |1|90 degrees.|
| ROTATION_180 |2| 180 degrees.|
| ROTATION_270 |3| 270 degrees.|

## ArrowPointPosition<sup>11+</sup>

Sets the position of the bubble arrow.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Value          | Description                                    |
| ------------- | -------------------------------------- | -------------------------------------- |
| START | 'Start' | On the leftmost side of the parent component in the horizontal layout; on the top of the parent component in the vertical layout.|
| CENTER | 'Center' | In the center of the parent component.|
| END | 'End' | On the rightmost side of the parent component in the horizontal layout; at the bottom of the parent component in the vertical layout.|

## Axis

Defines the axis direction.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Value| Description    |
| ---------- | -- | ------ |
| Vertical   | 0 | Vertical direction.|
| Horizontal | 1 | Horizontal direction.|

## AxisAction<sup>17+</sup>

Enumerates the types of axis actions for axis events.

**Atomic service API**: This API can be used in atomic services since API version 17.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Value  | Description                              |
| ------- | ---- | ---------------------------------- |
| NONE   | 0    | No axis event.|
| BEGIN  | 1    | The axis event begins.|
| UPDATE | 2    | The axis event is in progress.|
| END    | 3    | The axis event ends.|
| CANCEL | 4    | The axis event is canceled.|

## AxisModel<sup>15+</sup>

Enumerates the axis types for focus axis events.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Value  | Description                              |
| ------- | ---- | ---------------------------------- |
| ABS_X  | 0    | Game controller x-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 15.|
| ABS_Y  | 1    | Game controller y-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 15.|
| ABS_Z  | 2    | Game controller z-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 15.|
| ABS_RZ | 3    | Game controller rz-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 15.|
| ABS_GAS | 4    | Game controller GAS-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 15.|
| ABS_BRAKE | 5    | Game controller BRAKE-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 15.|
| ABS_HAT0X | 6    | Game controller HAT0X-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 15.|
| ABS_HAT0Y | 7    | Game controller HAT0Y-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 15.|
| ABS_RX<sup>23+</sup> | 8 | Game controller RX-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|
| ABS_RY<sup>23+</sup> | 9 | Game controller RY-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|
| ABS_THROTTLE<sup>23+</sup> | 10 | Game controller THROTTLE-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|
| ABS_RUDDER<sup>23+</sup> | 11 | Game controller RUDDER-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|
| ABS_WHEEL<sup>23+</sup> | 12 | Game controller WHEEL-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|
| ABS_HAT1X<sup>23+</sup> | 13 | Game controller HAT1X-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|
| ABS_HAT1Y<sup>23+</sup> | 14 | Game controller HAT1Y-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|
| ABS_HAT2X<sup>23+</sup> | 15 | Game controller HAT2X-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|
| ABS_HAT2Y<sup>23+</sup> | 16 | Game controller HAT2Y-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|
| ABS_HAT3X<sup>23+</sup> | 17 | Game controller HAT3X-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|
| ABS_HAT3Y<sup>23+</sup> | 18 | Game controller HAT3Y-axis.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|

## AxisType<sup>22+</sup>

Enumerates the axis types for axis events.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Value  | Description                              |
| ------- | ---- | ---------------------------------- |
| VERTICAL_AXIS   | 0    | Vertical scroll axis.|
| HORIZONTAL_AXIS  | 1    | Horizontal scroll axis.|
| PINCH_AXIS | 2    | Pinch axis.|

## BarState

Sets the scroll bar status.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Value| Description                |
| ---- | --- | ------------------ |
| Off  | 0 | Not displayed.              |
| Auto | 1 | Displayed when the screen is touched and hidden after 2s.|
| On   | 2 | Always displayed.             |

## BorderStyle

Sets the border style of an element.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Value| Description                           |
| ------ | --- | ----------------------------- |
| Dotted | 0 | Dotted border. The radius of a dot is half of **borderWidth**.|
| Dashed | 1 | Dashed border.                |
| Solid  | 2 |Solid border.                     |

## ClickEffectLevel<sup>10+</sup>

Sets the click effect level and animation parameters.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Description              | Animation Settings                         | Default Zoom Ratio                    |
| ------ | --------------------------------- | --------------------------------- | --------------------------------- |
| LIGHT  | Small area (light)| Spring effect, with stiffness of 410, damping of 38, and initial velocity of 1.| 90% |
| MIDDLE | Medium area (stable)| Spring effect, with stiffness of 350, damping of 35, and initial velocity of 0.5.| 95% |
| HEAVY  | Large area (heavy)| Spring effect, with stiffness of 240, damping of 28, and initial velocity of 0.| 95% |

## Color

Sets the color type.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                    | Value           | Description                                                        |
| ------------------------ | ------------- | ------------------------------------------------------------ |
| Black                    | 0x000000      | ![en-us_image_0000001219864153](figures/en-us_image_0000001219864153.png) |
| Blue                     | 0x0000ff      | ![en-us_image_0000001174104404](figures/en-us_image_0000001174104404.png) |
| Brown                    | 0xa52a2a      | ![en-us_image_0000001219744201](figures/en-us_image_0000001219744201.png) |
| Gray                     | 0x808080      | ![en-us_image_0000001174264376](figures/en-us_image_0000001174264376.png) |
| Grey                     | 0x808080      | ![en-us_image_0000001174264376](figures/en-us_image_0000001174264376.png) |
| Green                    | 0x008000      | ![en-us_image_0000001174422914](figures/en-us_image_0000001174422914.png) |
| Orange                   | 0xffa500      | ![en-us_image_0000001219662661](figures/en-us_image_0000001219662661.png) |
| Pink                     | 0xffc0cb      | ![en-us_image_0000001219662663](figures/en-us_image_0000001219662663.png) |
| Red                      | 0xff0000      | ![en-us_image_0000001219662665](figures/en-us_image_0000001219662665.png) |
| White                    | 0xffffff      | ![en-us_image_0000001174582866](figures/en-us_image_0000001174582866.png) |
| Yellow                   | 0xffff00      | ![en-us_image_0000001174582864](figures/en-us_image_0000001174582864.png) |
| Transparent<sup>9+</sup> | rgba(0,0,0,0) | Transparent                                                      |

## ColorSpace<sup>20+</sup>

Enumerates color space types for specifying color rendering modes.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   |  Value  | Description                  |
| ------  | ---- | -------------------- |
| SRGB | 0 | Standard RGB color space, suitable for most display devices.|
| DISPLAY_P3 | 1 | Display P3 color space with wider gamut, designed for high-end display devices.|

## ColoringStrategy<sup>10+</sup>

Enumerates the coloring strategies.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value| Description             |
| ------ | --- | --------------- |
| INVERT | invert | The foreground colors are the inverse of the component background colors. This strategy is only applicable when set within the [foregroundColor](ts-universal-attributes-foreground-color.md#foregroundcolor) attribute.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| AVERAGE<sup>11+</sup> | average | The shadow colors of the component are the average color obtained from the component background shadow area. This strategy is only applicable when set within the [shadow](ts-universal-attributes-image-effect.md#shadow) attribute whose input parameter type is ShadowOptions.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| PRIMARY<sup>11+</sup> | primary | The shadow colors of the component are the primary color obtained from the component background shadow area. This strategy is only applicable when set within the [shadow](ts-universal-attributes-image-effect.md#shadow) attribute whose input parameter type is ShadowOptions.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|

## CopyOptions<sup>9+</sup>

Sets the copy options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Value| Description      |
| ----------- | --- | -------- |
| None        | 0 | Copy disabled.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| InApp       | 1 | Copy and paste within the current application only.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| LocalDevice | 2 | Copy and paste across all applications on the device.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| CROSS_DEVICE<sup>(deprecated)</sup> | 3 | Cross-device copy.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 11.<br>Note: This API is supported since API version 11 and deprecated since API version 12.|

## CheckBoxShape<sup>11+</sup>

Sets the shape of check boxes.

**Widget capability**: This API can be used in ArkTS widgets since API version 11.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name          | Value  | Description    |
| -------------- | ---- | -------- |
| CIRCLE         | 0    | Circle.    |
| ROUNDED_SQUARE | 1    | Rounded square.|

## CrownAction<sup>18+</sup>

Enumerates the crown actions.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

|Name               | Value| Description                                  |
|-------------------| -- | ------------------------------------- |
| BEGIN             | 0  | The crown starts to rotate.                         |
| UPDATE            | 1  | The crown is rotating.                           |
| END                | 2  | The crown stops rotating.                         |

## CrownSensitivity<sup>18+</sup>

Enumerates the sensitivity levels for crown rotation.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name          | Value | Description                                     |
| -------------- | -- | ---------------------------------------- |
| LOW            | 0   | Low sensitivity.                                |
| MEDIUM         | 1   | Medium sensitivity.                                |
| HIGH           | 2   | High sensitivity.                                |

## Curve

Enumerates the interpolation curves. For details about the animation, see <!--RP1-->[Bezier Curve](../../../../design/ux-design/animation-attributes.md)<!--RP1End-->.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                 | Value| Description                                      |
| ------------------- | ------- | --------------------------------- |
| Linear              | 0 | The animation maintains a constant speed throughout the process.                       |
| Ease                | 1 | The animation starts slowly, accelerates, and then decelerates before ending. The curve is CubicBezier(0.25, 0.1, 0.25, 1.0).|
| EaseIn              | 2 | The animation starts at a low speed and then picks up speed until the end. The cubic-bezier curve (0.42, 0.0, 1.0, 1.0) is used.|
| EaseOut             | 3 | The animation ends at a low speed. The cubic-bezier curve (0.0, 0.0, 0.58, 1.0) is used.|
| EaseInOut           | 4 | The animation starts and ends at a low speed. The cubic-bezier curve (0.42, 0.0, 0.58, 1.0) is used.|
| FastOutSlowIn       | 5 | The animation uses the standard cubic-bezier curve (0.4, 0.0, 0.2, 1.0).  |
| LinearOutSlowIn     | 6 | The animation uses the deceleration cubic-bezier curve (0.0, 0.0, 0.2, 1.0).  |
| FastOutLinearIn     | 7 | The animation uses the acceleration cubic-bezier curve (0.4, 0.0, 1.0, 1.0).  |
| ExtremeDeceleration | 8 | The animation uses the extreme deceleration cubic-bezier curve (0.0, 0.0, 0.0, 1.0).  |
| Sharp               | 9 | The animation uses the sharp cubic-bezier curve (0.33, 0.0, 0.67, 1.0).|
| Rhythm              | 10 | The animation uses the rhythm cubic-bezier curve (0.7, 0.0, 0.2, 1.0).  |
| Smooth              | 11 | The animation uses the smooth cubic-bezier curve (0.4, 0.0, 0.4, 1.0).  |
| Friction            | 12 | The animation uses the friction cubic-bezier curve (0.2, 0.0, 0.2, 1.0).   |

## DialogButtonStyle<sup>10+</sup>

Sets the button style for dialog boxes.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Value  | Description                             |
| --------- | ---- | --------------------------------- |
| DEFAULT   | 0    | Blue text on white background (black background under the dark theme).|
| HIGHLIGHT | 1    | White text on blue background.                       |

## Direction

Defines the horizontal layout direction of elements.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Value  | Description         |
| ---- | ---- | ----------- |
| Ltr  | 0 | Components are arranged from left to right.  |
| Rtl  | 1 |Components are arranged from right to left.  |
| Auto | 2 |The default layout direction is used.|

## DividerMode<sup>19+</sup>

Enumerates divider modes.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Value| Description                                      |
| ------------------ | - | ---------------------------------------- |
| FLOATING_ABOVE_MENU| 0 | The divider floats above the menu without affecting the layout height. This is the default mode.     |
| EMBEDDED_IN_MENU   | 1 | The divider is embedded in the menu and affects the layout height.   |

## Edge

Controls the alignment position of the scrollable component in the layout..

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                            | Value| Description                                                        |
| -------------------------------- | --- | ------------------------------------------------------------ |
| Top                              | 0 | Top edge in the vertical direction.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| Center<sup>(deprecated) </sup>   | 1 | Center position in the vertical direction.<br> This API is deprecated since API version 9.           |
| Bottom                           | 2 | Bottom edge in the vertical direction.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| Baseline<sup>(deprecated) </sup> | 3 | Text baseline position in the cross axis direction.<br> This API is deprecated since API version 9.     |
| Start                            | 4 | Start position in the horizontal direction.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| Middle<sup>(deprecated) </sup>   | 5 | Center position in the horizontal direction.<br> This API is deprecated since API version 9.           |
| End                              | 6 | End position in the horizontal direction.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|

## EdgeEffect

Defines the sliding effect of the scrollable container.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value| Description                                      |
| ------ | --- | ---------------------------------------- |
| Spring | 0 | Spring effect. When at one of the edges, the component can move beyond the bounds through touches, and produces a bounce effect when the user releases their finger.<br>In API version 22 and earlier versions, the spring effect of the scrollable component does not take effect when the scrollbar is dragged.<br>In API version 23 and later versions, the spring effect of the scrollable component takes effect when the scrollbar is dragged by fingers, but does not take effect when the scrollbar is dragged by a mouse.|
| Fade   | 1 | Fade effect. When at one of the edges, the component produces a fade effect.                    |
| None   | 2 | No effect when the component is at one of the edges.                              |

## EllipsisMode<sup>11+</sup>

Sets the position of ellipsis.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Value| Description                                  |
| ----- | --- | -------------------------------------- |
| START  | 0 | An ellipsis is used at the start of the line of text.|
| CENTER | 1 | An ellipsis is used at the center of the line of text.|
| END | 2 | An ellipsis is used at the end of the line of text.|

## EmbeddedType<sup>12+</sup>
Enumerates the types of the providers that can be started by the **EmbeddedComponent**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                 | Value| Description                                               |
| --------------------- | - | ---------------------------------------------------- |
| EMBEDDED_UI_EXTENSION | 0 | EmbeddedUIExtensionAbility.|

## EventQueryType<sup>19+</sup>

Enumerates interaction event types that can be queried.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | -------- | -------- |
| ON_CLICK  | 0 | Click event.|

## FunctionKey<sup>10+</sup>

Enumerates the input method function keys.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Value| Description          |
| ---- | ------------ | ------------ |
| ESC  | 0 | Esc key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| F1   | 1 | F1 key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| F2   | 2 | F2 key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| F3   | 3 | F3 key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| F4   | 4 | F4 key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| F5   | 5 | F5 key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| F6   | 6 | F6 key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| F7   | 7 | F7 key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| F8   | 8 | F8 key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| F9   | 9 | F9 key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| F10  | 10 | F10 key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| F11  | 11 | F11 key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| F12  | 12 | F12 key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| TAB<sup>12+</sup>  | 13 | Tab key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| DPAD_UP<sup>12+</sup>   | 14 | Up arrow key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| DPAD_DOWN<sup>12+</sup> | 15 | Down arrow key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| DPAD_LEFT<sup>12+</sup> | 16 | Left arrow key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| DPAD_RIGHT<sup>12+</sup> | 17 | Right arrow key on the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|

## FillMode

Sets the status before and after execution of the animation in the current playback direction. The status after execution of the animation is jointly determined by the **fillMode** and **reverse** attributes. For example, if **fillMode** is set to **Forwards**, the target will retain the state defined by the last keyframe encountered during execution. In this case, if **reverse** is set to **false**, the target will retain the state defined by the last keyframe encountered in the forward direction, that is, the last image; if **reverse** is set to **true**, the target will retain the state defined by the last keyframe encountered in the backward direction, that is, the first image.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       |Value| Description                                      |
| --------- |-| ---------------------------------------- |
| None      |0| If the animation is not executed, no style is applied to the target. After the animation is played, the initial default state is restored.    |
| Forwards  |1| The target component retains the state set by the last keyframe encountered during execution of the animation.                  |
| Backwards |2| The animation applies the values defined in the first relevant keyframe once it is applied to the target component, and retains the values during the period set by **delay**. The first relevant keyframe depends on the value of **playMode**. If **playMode** is **Normal** or **Alternate**, the first relevant keyframe is in the **from** state. If **playMode** is **Reverse** or **AlternateReverse**, the first relevant keyframe is in the **to** state.|
| Both      |3| The animation follows the rules for both **Forwards** and **Backwards**, extending the animation attributes in both directions.|

## FlexAlign

Sets the alignment mode of an element on the main axis of the container.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name          | Description                                      |
| ------------ | ---------------------------------------- |
| Start        | The child components are aligned with the start edge of the main axis. The first component is aligned with the main-start, and subsequent components are aligned with the previous one.   |
| Center       | The child components are aligned in the center of the main axis. The space between the first component and the main-start is the same as that between the last component and the main-end.  |
| End          | The child components are aligned with the end edge of the main axis. The last component is aligned with the main-end, and other components are aligned with the next one.     |
| SpaceBetween | The child components are evenly distributed along the main axis. The space between any two adjacent components is the same. The first component is aligned with the main-start, the last component is aligned with the main-end, and the remaining components are distributed so that the space between any two adjacent components is the same.|
| SpaceAround  | The child components are evenly distributed along the main axis. The space between any two adjacent components is the same. The space between the first component and main-start, and that between the last component and cross-main are both half the size of the space between two adjacent components.|
| SpaceEvenly  | The child components are evenly distributed along the main axis. The space between the first component and main-start, the space between the last component and main-end, and the space between any two adjacent components are the same.|

## FlexDirection

Sets the direction in which child components are arranged in the **Flex** component, that is, the direction of the main axis.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Description              |
| ------------- | ---------------- |
| Row           | The child components are arranged in the same direction as the main axis runs along the rows. |
| RowReverse    | The child components are arranged opposite to the **Row** direction. |
| Column        | The child components are arranged in the same direction as the main axis runs down the columns. |
| ColumnReverse | The child components are arranged opposite to the **Column** direction.|

## FlexWrap

Sets whether elements are arranged in a single row/column or multiple rows/columns in the **Flex** container.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Description                         |
| ----------- | --------------------------- |
| NoWrap      | The child components in the flex container are arranged in a single line. If any of them have minimum size constraints applied, the flex container does not forcibly shrink them when overflow occurs. |
| Wrap        | The child components in the flex container are arranged in multiple lines, and they may overflow.  |
| WrapReverse | The child components in the flex container are reversely arranged in multiple lines, and they may overflow.|

## FontStyle

Sets the font style.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    |Value| Description      |
| ------ |-| -------- |
| Normal |0| Standard font style.|
| Italic |1| Italic font style.|

## FontWeight

Sets the font weight.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   |   Value  |  Description  |
| ------- | ----- |----------- |
| Lighter | - |100 font weight (thin).|
| Normal  | - |400 font weight (normal).|
| Regular | - |400 font weight (normal), which is the same as the Normal effect.|
| Medium  | - |500 font weight (medium).|
| Bold    | - |700 font weight (bold).  |
| Bolder  | - |900 font weight (extra bold).|

**FontWeight** is one of the types of the input parameter **value** of the [fontWeight](./ts-basic-components-text.md#fontweight) attribute. When **value** is of the **FontWeight**, **number**, or [ResourceStr](./ts-types.md#resourcestr) type, the mapping is as follows:

| FontWeight | number | ResourceStr |
| ---------------- | ------ | ------ |
| Lighter | 100 |'lighter' |
| Normal  | 400 |'normal' |
| Regular | 400 |'regular' |
| Medium  | 500 |'medium' |
| Bold    | 700 |'bold'   |
| Bolder  | 900 |'bolder' |

## FoldStatus<sup>11+</sup>

Sets the folding status of the device.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                     |Value| Description        |
| ----------------------  |----| ---------- |
| FOLD_STATUS_UNKNOWN     |0| The folding status of the device is unknown.|
| FOLD_STATUS_EXPANDED    |1| The device is fully open.  |
| FOLD_STATUS_FOLDED      |2| The device is folded (completely closed).  |
| FOLD_STATUS_HALF_FOLDED |3| The device is half-folded, somewhere between fully open and completely folded.|

## FocusDrawLevel<sup>19+</sup>

Enumerates the drawing levels of the focus box for a node.

**Widget capability**: This API can be used in ArkTS widgets since API version 19.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name          | Value | Description                                     |
| -------------- | -- | ---------------------------------------- |
| SELF           | 0   | The focus box is drawn on the node's own layer.                                |
| TOP            | 1   | The focus box is drawn on the topmost layer of the current instance's z-order.                                |

## FocusWrapMode<sup>20+</sup>

Enumerates focus wrapping modes for cross-axis directional navigation.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Value  | Description                                                        |
| --------------- | ---- | ------------------------------------------------------------ |
| DEFAULT         | 0    | Cross-axis directional navigation does not wrap focus.                                      |
| WRAP_WITH_ARROW | 1    | Cross-axis directional navigation wraps focus.<br>In irregular grid layouts, when moving focus along the cross axis, the system prioritizes focusable items within the same row.|

## GradientDirection

Sets the direction of the linear gradient.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Description   |
| ----------- | ----- |
| Left        | Right to left.|
| Top         | From bottom to top.|
| Right       | From left to right.|
| Bottom      | From top to bottom.|
| LeftTop     | From upper left to lower right.  |
| LeftBottom  | From lower left to upper right.  |
| RightTop    | From upper right to lower left.  |
| RightBottom | From lower right to upper left.  |
| None        | None.   |

## HorizontalAlign

Sets the horizontal alignment mode of child components.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Description          |
| ------ | ------------ |
| Start  | Aligned with the start edge in the same direction as the language in use.|
| Center | Aligned with the center. This is the default alignment mode.|
| End    | Aligned with the end edge in the same direction as the language in use. |

## HoverEffect<sup>8+</sup>

Sets the hover effect of the component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Description            |
| --------- | -------------- |
| Auto      | Default hover effect.|
| Scale     | Zoom-in and zoom-out effect.       |
| Highlight | Background fade-in and fade-out effect.  |
| None      | No effect.        |

## HitTestMode<sup>9+</sup>

Sets the response logic and node blocking rules for the hit test.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Description                                      |
| ----------- | ---------------------------------------- |
| Default     | Default hit test mode. The node itself and its child nodes respond to the hit test, but block the hit test of sibling nodes. It does not affect the hit test of ancestor nodes.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| Block       | The node itself responds to the hit test and blocks the hit test of child nodes, sibling nodes, and ancestor nodes.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| Transparent | Both the node itself and its child nodes respond to the hit test and do not block the hit test of sibling nodes and ancestor nodes.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| None        | The node itself does not respond to the hit test and does not block the hit test of child nodes, sibling nodes, and ancestor nodes.<br>**Atomic service API**: This API can be used in atomic services since API version 11.     |
| BLOCK_HIERARCHY<sup>20+</sup>   | The node itself and its child nodes respond to the hit test, preventing all sibling nodes and parent nodes with lower priority from participating in the hit test.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| BLOCK_DESCENDANTS<sup>20+</sup> | The node itself does not respond to the hit test, and all its descendants (children, grandchildren, and more) also do not respond to the hit test. It does not affect the hit test of ancestor nodes.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

## HeightBreakpoint<sup>13+</sup>

Enumerates the height breakpoint values corresponding to different window aspect ratio thresholds. The values are returned through [getWindowHeightBreakpoint](../arkts-apis-uicontext-uicontext.md#getwindowheightbreakpoint13).

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

The following table lists default aspect ratio breakpoint thresholds for typical devices, serving as a reference for responsive layout design based on window aspect ratios. Device manufacturers may customize these thresholds through product-specific configurations when needed.

| Name    | Value  | Description                  |
| -------- | ---- | ---------------------- |
| HEIGHT_SM | 0   | The window aspect ratio is less than 0.8.|
| HEIGHT_MD | 1   | The window aspect ratio is greater than or equal to 0.8 and less than 1.2.|
| HEIGHT_LG | 2   | The window aspect ratio is greater than or equal to 1.2.|

## ImageFit

Sets the image filling effect.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Value   | Description                             |
| --------- | ----- | ------------------------------- |
| Fill      | 0  | The image or video is scaled without maintaining the aspect ratio to fill the display boundaries, with horizontal center alignment.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>![ImageFit-Examples04](figures/image_fit_fill.png) |
| Contain   | 1  | The image or video is scaled with its aspect ratio retained to fit entirely within the display boundaries, with horizontal center alignment.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>![ImageFit-Examples01](figures/image_fit_contain.png) |
| Cover     | 2  | The image or video is scaled while maintaining the aspect ratio so that both sides are greater than or equal to the display boundaries, aligned horizontally in the center.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>![ImageFit-Examples02](figures/image_fit_cover.png) |
| Auto      | 3  | The image or video is scaled appropriately based on its own dimensions and the component's size to fill the view while maintaining the aspect ratio, aligned horizontally in the center.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>![ImageFit-Examples03](figures/image_fit_auto.png) |
| None      | 5  | The image is displayed at its original size, aligned horizontally in the center.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>![ImageFit-Examples06](figures/image_fit_none.png) |
| ScaleDown | 6  | The image or video is displayed while maintaining the aspect ratio, only scaling down or keeping the original size, aligned horizontally in the center.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>![ImageFit-Examples05](figures/image_fit_scaleDown.png) |
| TOP_START<sup>12+</sup> | 7  | The image or video is displayed at the top start position of the component in the original size.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>![ImageFit-Examples07](figures/image_fit_top_start.png) |
| TOP<sup>12+</sup>       | 8  | The image or video is displayed at the top center position of the component in the original size.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>![ImageFit-Examples08](figures/image_fit_top.png)  |
| TOP_END<sup>12+</sup>   | 9  | The image or video is displayed at the top end position of the component in the original size.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>![ImageFit-Examples09](figures/image_fit_top_end.png) |
| START<sup>12+</sup>     | 10  | The image or video is displayed at the start position (vertically centered) of the component in the original size.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>![ImageFit-Examples10](figures/image_fit_start.png) |
| CENTER<sup>12+</sup>    | 11  | The image or video is displayed at the center position of the component in the original size.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>![ImageFit-Examples11](figures/image_fit_center.png) |
| END<sup>12+</sup>       | 12  | The image or video is displayed at the end position (vertically centered) of the component in the original size.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>![ImageFit-Examples12](figures/image_fit_end.png) |
| BOTTOM_START<sup>12+</sup> | 13  | The image or video is displayed at the bottom start position of the component in the original size.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>![ImageFit-Examples13](figures/image_fit_bottom_start.png) |
| BOTTOM<sup>12+</sup>    | 14  | The image or video is displayed at the bottom center position of the component in the original size.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>![ImageFit-Examples14](figures/image_fit_bottom.png) |
| BOTTOM_END<sup>12+</sup>| 15  | The image or video is displayed at the bottom end position of the component in the original size.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>![ImageFit-Examples15](figures/image_fit_bottom_end.png) |
| MATRIX<sup>15+</sup>| 16  | The image, with the use of [imageMatrix](ts-basic-components-image.md#imagematrix15), is displayed in the specified position of the **Image component**, keeping its original size. SVG images are not supported.<br>**Atomic service API**: This API can be used in atomic services since API version 15.|

## ItemAlign

Sets the alignment mode of an element on the cross axis of the container.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Description                                      |
| -------- | ---------------------------------------- |
| Auto     | The default configuration of the flex container is used.                          |
| Start    | The items in the flex container are aligned with the cross-start edge.                   |
| Center   | The items in the flex container are centered along the cross axis.                   |
| End      | The items in the flex container are aligned with the cross-end edge.                   |
| Stretch  | The items in the flex container are stretched and padded along the cross axis. If the flex container has the **Wrap** attribute set to **FlexWrap.Wrap** or **FlexWrap.WrapReverse**, the items are stretched to the cross size of the widest element on the current row or column. In other cases, the items are stretched to the container size regardless of whether their size is set.|
| Baseline | The items in the flex container are aligned in such a manner that their text baselines are aligned along the cross axis.                 |

## ImageRepeat

Sets the image repeat pattern.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      |Value| Description           |
| -------- |-| ------------- |
| NoRepeat |0| The image is not repeatedly drawn.     |
| X        |1| The image is repeatedly drawn only along the horizontal axis.|
| Y        |2| Images are repeatedly drawn only on the vertical axis.|
| XY       |3| The image is repeatedly drawn along both axes. |

## ImageSize

Sets the width and height effect of an image.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Value   | Description                                 |
| ------- | -------------------------- | ----------------------------------- |
| Cover   | 1  | The image is scaled with its aspect ratio retained for both sides to be greater than or equal to the display boundaries.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| Contain | 2  | The image is scaled with its aspect ratio retained for the content to be completely displayed within the display boundaries.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br> **Atomic service API**: This API can be used in atomic services since API version 11.     |
| Auto    | 0  | The original image aspect ratio is retained.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br> **Atomic service API**: This API can be used in atomic services since API version 11.                        |
| FILL<sup>12+</sup> | 3  | The image is scaled to fill the display area, and its aspect ratio is not retained.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|

## ImageSpanAlignment<sup>10+</sup>

Sets the alignment mode of the image relative to the line height.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value| Description                          |
| -------- | ------------------------------ |------------------------------ |
| TOP      | 1 | The image is top aligned with the line.<br>**Atomic service API**: This API can be used in atomic services since API version 11.  |
| CENTER   | 2 | The image is centered aligned with the line.<br>**Atomic service API**: This API can be used in atomic services since API version 11.      |
| BOTTOM   | 3 | The image is bottom aligned with the line.<br>**Atomic service API**: This API can be used in atomic services since API version 11.  |
| BASELINE | 4 | The image is bottom aligned with the text baseline.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| FOLLOW_PARAGRAPH<sup>20+</sup>  | 5 |The alignment mode follows the parent component of the **Text** component.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

## InteractionHand<sup>15+</sup>

Enumerates how an input event is triggered.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value  | Description                  |
| -------- | ---- | ---------------------- |
| NONE     | 0   | Unspecified.|
| LEFT     | 1   | Left-hand interaction.|
| RIGHT    | 2   | Right-hand interaction.|

## KeySource

Sets the device type that triggers the button event.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Value| Description        |
| -------- | ---------- | ---------- |
| Unknown  | 0 | Unknown input device. |
| Keyboard | 4 | The input device is a keyboard.|
| JOYSTICK<sup>15+</sup> | 5 | The input device is a joystick.<br>**Atomic service API**: This API can be used in atomic services since API version 15.|

## KeyType

Sets the status type of a button operation.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Value| Description   |
| ---- | ----- | ----- |
| Down | 0 | The key is pressed.|
| Up   | 1 | The key is released.|

## LineJoinStyle

Sets the line connection style.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | ---- | ------------- |
| Miter | 0 | Miter is used to connect paths. |
| Round | 1 | Round is used to connect paths. |
| Bevel | 2 | Bevel is used to connect paths. |

## LocalizedAlignment<sup>20+</sup>

Enumerated type that supports the align and [layoutGravity](ts-universal-attributes-location.md#layoutgravity20) attributes.

**Widget capability**: This API can be used in ArkTS widgets since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Value           | Description      |
| ------------- | ------------- | ------------- |
| TOP_START     | 'top_start'   | Top start.  |
| TOP           | 'top'         | Horizontally centered on the top. |
| TOP_END       | 'top_end'     | Top end.   |
| START         | 'start'       | Vertically centered start.|
| CENTER        | 'center'      | Horizontally and vertically centered.|
| END           | 'end'         | Vertically centered end. |
| BOTTOM_START  | 'bottom_start'| Bottom start.  |
| BOTTOM        | 'bottom'      | Horizontally centered on the bottom. |
| BOTTOM_END    | 'bottom_end'  | Bottom end.   |

## LineCapStyle

Sets the line endpoint style.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| ------ | ---- | ------------- |
| Butt   | 0 | The ends of the line are squared off, and the line does not extend beyond its two endpoints.   |
| Round  | 1 | The line is extended at the endpoints by a half circle whose diameter is equal to the line width. |
| Square | 2 | The line is extended at the endpoints by a rectangle whose width is equal to half the line width and height equal to the line width.  |

## LineBreakStrategy<sup>12+</sup>

Sets the line break rule.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Value| Description                                                        |
| ------------ | --- | ------------------------------------------------------------ |
| GREEDY       | 0 | Places as many words on a line as possible and moves to the next line only if no more words can fit into the same line.|
| HIGH_QUALITY | 1 | Fills in lines as much as possible on the basis of **BALANCED**, which may results in a large blank area on the last line.|
| BALANCED     | 2 | Without splitting words, the width of each line in a paragraph is the same as much as possible.  |

## MouseButton<sup>8+</sup>

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Value| Description      |
| ------- | -------- | -------- |
| Left    | 1 | Left button on the mouse.   |
| Right   | 2 | Right button on the mouse.   |
| Middle  | 4 | Middle button on the mouse.   |
| Back    | 8 | Back button on the left of the mouse.|
| Forward | 16 | Forward button on the left of the mouse.|
| None    | 0 | No button.    |

## MouseAction<sup>8+</sup>

Sets the action type of a mouse operation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     |  Value | Description     |
| ------- | ----- |  ------- |
| Press   |   1   | The mouse button is pressed.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| Release |   2   | The mouse button is released.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| Move    |   3   | The mouse cursor moves.<br>**Atomic service API**: This API can be used in atomic services since API version 11.  |
| Hover   |   4   | The mouse pointer is hovered on an element.<br>Note: This value has no effect.<br>**Atomic service API**: This API can be used in atomic services since API version 11.  |
| ENTER_WINDOW<sup>23+</sup>   |   4   | The mouse pointer moves into the window.<br>**Atomic service API**: This API can be used in atomic services since API version 23.  |
| LEAVE_WINDOW<sup>23+</sup>   |   5   | The mouse pointer moves out of the window.<br>**Atomic service API**: This API can be used in atomic services since API version 23.  |
| CANCEL<sup>18+</sup>  |  13  | The mouse button action is canceled. It is triggered in the following scenarios:<br>1. Component focus loss: This action is triggered when a currently focused component loses focus due to a system event (such as pop-up interruption or app switching).<br>2. Event interruption: During a mouse operation, if a higher-priority event occurs (such as a system-level gesture or forced event stream recycling), causing the current mouse operation to be forcibly terminated.<br>3. Abnormal state exit: In scenarios such as component destruction or abnormal rendering environment, unfinished mouse events are marked as canceled.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|

## ModifierKey<sup>10+</sup>

Enumerates the input method modifier keys.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Value| Description          |
| ----- | ------------ | ------------ |
| CTRL  | 0 | Ctrl key on the keyboard. |
| SHIFT | 1 | Shift key on the keyboard.|
| ALT   | 2 | Alt key on the keyboard.  |

## MarqueeUpdateStrategy<sup>12+</sup>

Sets the scrolling strategy for the marquee after its attributes are updated.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Value     | Description                    |
| ---------- | ------------------------ | ------------------------ |
| DEFAULT | 0 | After the marquee attributes are updated, the marquee scrolls from the start position.    |
| PRESERVE_POSITION  | 1 | After the marquee attributes are updated, the marquee scrolls from the current position.|

## NestedScrollMode<sup>10+</sup>

Sets the nested mode of a nested scrollable component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value| Description                            |
| ------ | --- | ------------------------------ |
| SELF_ONLY   | 0 | The scrolling is contained within the component, and no scroll chaining occurs, that is, the parent component does not scroll when the component scrolling reaches the boundary. |
| SELF_FIRST | 1 | The component scrolls first, and when it hits the boundary, the parent component scrolls. When the parent component hits the boundary, its edge effect is displayed. If no edge effect is specified for the parent component, the edge effect of the child component is displayed instead.       |
| PARENT_FIRST  | 2 | The parent component scrolls first, and when it hits the boundary, the component scrolls. When the component hits the boundary, its edge effect is displayed. If no edge effect is specified for the component, the edge effect of the parent component is displayed instead.|
| PARALLEL  | 3 | The component and its parent component scroll at the same time. When both the component and its parent component hit the boundary, the edge effect of the component is displayed. If no edge effect is specified for the component, the edge effect of the parent component is displayed instead.|

## Nullable\<T><sup>11+</sup>

type Nullable\<T> = T | undefined

This type allows for an object of a custom type or **undefined**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type| Description                      |
| ---- | -------------------------- |
|  T   | The object can be of any custom type.|
| undefined | The object can be **undefined**.|

## ObscuredReasons<sup>10+</sup>

Sets how the component content is obscured.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Value| Description                    |
| ----------- | -- | ------------------------ |
| PLACEHOLDER | 0 |The content is replaced by a placeholder.|

## OptionWidthMode<sup>11+</sup>

Sets the width mode of the drop-down menu.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Value      | Description                          |
| ----------- | ------------------------------ | ------------------------------ |
| FIT_CONTENT | 'fit_content' | If this value is set, the width of the drop-down menu is 2 columns by default.           |
| FIT_TRIGGER | 'fit_trigger' | Inherits the width of the drop-down list button.|

## PlayMode

Sets the animation playback mode.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name              | Value| Description                                      |
| ---------------- | ----- | ----------------------------------- |
| Normal           | 0 | The animation is played forwards.                                |
| Reverse          | 1 | The animation is played backwards.                                 |
| Alternate        | 2 | The animation is played forwards for an odd number of times (1, 3, 5...) and backwards for an even number of times (2, 4, 6...).|
| AlternateReverse | 3 | The animation is played backwards for an odd number of times (1, 3, 5...) and forwards for an even number of times (2, 4, 6...).|

## Placement<sup>8+</sup>

Sets the position of a bubble.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                    | Description                                                        |
| ------------------------ | ------------------------------------------------------------ |
| Left                     | The popup is on the left of the component, vertically aligned with the component on the left.                  |
| Right                    | The popup is on the right of the component, vertically aligned with the component on the right.                  |
| Top                      | The popup is at the top of the component, horizontally aligned with the component at the top.                  |
| Bottom                   | The popup is at the bottom of the component, horizontally aligned with the component at the bottom.                  |
| TopLeft                  | The popup is at the top of the component and, since API version 9, aligned with the left of the component.|
| TopRight                 | The popup is at the top of the component and, since API version 9, aligned with the right of the component.|
| BottomLeft               | The popup is at the bottom of the component and, since API version 9, aligned with the left of the component.|
| BottomRight              | The popup is at the bottom of the component and, since API version 9, aligned with the right of the component.|
| LeftTop<sup>9+</sup>     | The popup is on the left of the component and aligned with the top of the component.                  |
| LeftBottom<sup>9+</sup>  | The popup is on the left of the component and aligned with the bottom of the component.                  |
| RightTop<sup>9+</sup>    | The popup is on the right of the component and aligned with the top of the component.                  |
| RightBottom<sup>9+</sup> | The popup is on the right of the component and aligned with the bottom of the component.                  |

## PixelRoundCalcPolicy<sup>11+</sup>

Enumerates the pixel rounding policies for component boundaries.

**Widget capability**: This API can be used in ArkTS widgets since API version 11.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    |Value| Description                           |
| ------ | ----|----------------------------- |
| NO_FORCE_ROUND |0| The value is not rounded off.|
| FORCE_CEIL |1| Rounded-up calculation.|
| FORCE_FLOOR |2| Rounded-down calculation.|

## PageFlipMode<sup>15+</sup>

Enumerates the modes for flipping pages using the mouse wheel.

**Widget capability**: This API can be used in ArkTS widgets since API version 15.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value  | Description                  |
| -------- | ---- | ---------------------- |
| CONTINUOUS | 0   | Continuous page flipping mode where multiple pages are turned continuously when the user scrolls the mouse wheel without interruption.|
| SINGLE | 1   | Single-page flipping mode where the mouse wheel event is ignored until the current page flipping animation is complete.|

## PixelRoundMode<sup>18+</sup>

Enumerates pixel rounding modes.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   |  Value  | Description                  |
| ------  |---- | -------------------- |
| PIXEL_ROUND_ON_LAYOUT_FINISH | 0 | Performs pixel rounding after the component finishes measuring its size and position. Default value.|
| PIXEL_ROUND_AFTER_MEASURE |  1 | Performs pixel rounding after the component finishes measuring its size.|

## PresetFillType<sup>22+</sup>

Enumerates column count policies for different [responsive breakpoints](../../../ui/arkts-layout-development-grid-layout.md#breakpoints).

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Value  | Description                                                        |
| --------------- | ---- | ------------------------------------------------------------ |
| BREAKPOINT_DEFAULT         | 0    | **List** or **Swiper** component: 1 column (SM or smaller), 2 columns (MD), 3 columns (LG or larger).<br> **Grid** or **WaterFlow** component: 2 columns (SM or smaller), 3 columns (MD), 5 columns (LG or larger).                                      |
| BREAKPOINT_SM1MD2LG3 | 1    | 1 column (SM or smaller), 2 columns (MD), 3 columns (LG or larger).|
| BREAKPOINT_SM2MD3LG5 | 2    | 2 columns (SM or smaller), 3 columns (MD), 5 columns (LG or larger).|

## RelateType

Sets the padding mode of a child component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Value  | Description            |
| ---- | ---- | -------------- |
| FILL | 0 | The current child component is scaled to fill the parent component.|
| FIT  | 1 | The current child component is scaled to adapt to the parent component.|

## ResponseRegionSupportedTool<sup>22+</sup>

Sets the type of the input tool applicable to the touch target.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Value| Description                            |
| ------ | -----|------------------------------- |
| ALL    | 0 | All input tool types.  |
| FINGER | 1 | Finger.  |
| PEN    | 2 | Stylus.|
| MOUSE  | 3 | Mouse.  |

## ResponseType<sup>8+</sup>

Sets how menu display is triggered.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Description           |
| ---------- | ------------- |
| LongPress  | The menu is displayed when the component is long-pressed.  |
| RightClick | Shows the shortcut menu by right-clicking the text.|

## RenderFit<sup>10+</sup>

Enumerates the modes in which the final state of the component's content is rendered during its width and height animation process.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                         | Value                         | Description                                                                             |
| --------------------------- | -- | ---------------------------------------------------------------------------------- |
| CENTER                      | 0                           | The component's content stays at the final size and always aligned with the center of the component.               ![renderfit_center](figures/renderfit_center.png) |
| TOP                         | 1                           | The component's content stays at the final size and always aligned with the top center of the component.             ![renderfit_top](figures/renderfit_top.png) |
| BOTTOM                      | 2                           | The component's content stays at the final size and always aligned with the bottom center of the component.             ![renderfit_bottom](figures/renderfit_bottom.png) |
| LEFT                        | 3                           | The component's content stays at the final size and always aligned with the left of the component.               ![renderfit_left](figures/renderfit_left.png) |
| RIGHT                       | 4                           | The component's content stays at the final size and always aligned with the right of the component.              ![renderfit_right](figures/renderfit_right.png) |
| TOP_LEFT                    | 5                           | The component's content stays at the final size and always aligned with the upper left corner of the component.              ![renderfit_top_left](figures/renderfit_top_left.png) |
| TOP_RIGHT                   | 6                           | The component's content stays at the final size and always aligned with the upper right corner of the component.             ![renderfit_top_right](figures/renderfit_top_right.png) |
| BOTTOM_LEFT                 | 7                           | The component's content stays at the final size and always aligned with the lower left corner of the component.              ![renderfit_bottom_left](figures/renderfit_bottom_left.png) |
| BOTTOM_RIGHT                | 8                           | The component's content stays at the final size and always aligned with the lower right corner of the component.              ![renderfit_bottom_right](figures/renderfit_bottom_right.png) |
| RESIZE_FILL                 | 9                           | The component's content is always resized to fill the component's content box, without considering its aspect ratio in the final state.              ![renderfit_resize_fill](figures/renderfit_resize_fill.png) |
| RESIZE_CONTAIN              | 10                          | While maintaining its aspect ratio in the final state, the component's content is scaled to fit within the component's content box. It is always aligned with the center of the component.   ![renderfit_resize_contain](figures/renderfit_resize_contain.png) |
| RESIZE_CONTAIN_TOP_LEFT     | 11                          | While maintaining its aspect ratio in the final state, the component's content is scaled to fit within the component's content box. When there is remaining space in the width direction of the component, the content is left-aligned with the component. When there is remaining space in the height direction of the component, the content is top-aligned with the component.   ![renderfit_resize_contain_top_left](figures/renderfit_resize_contain_top_left.png) |
| RESIZE_CONTAIN_BOTTOM_RIGHT | 12                          | While maintaining its aspect ratio in the final state, the component's content is scaled to fit within the component's content box. When there is remaining space in the width direction of the component, the content is right-aligned with the component. When there is remaining space in the height direction of the component, the content is bottom-aligned with the component.   ![renderfit_resize_contain_bottom_right](figures/renderfit_resize_contain_bottom_right.png) |
| RESIZE_COVER                | 13                          | While maintaining its aspect ratio in the final state, the component's content is scaled to cover the component's entire content box. It is always aligned with the center of the component, so that its middle part is displayed.   ![renderfit_resize_cover](figures/renderfit_resize_cover.png) |
| RESIZE_COVER_TOP_LEFT       | 14                          | While maintaining its aspect ratio in the final state, the component's content is scaled to cover the component's entire content box. When there is remaining space in the width direction, the content is left-aligned with the component, so that its left part is displayed. When there is remaining space in the height direction, the content is top-aligned with the component, so that its top part is displayed.   ![renderfit_resize_cover_top_left](figures/renderfit_resize_cover_top_left.png) |
| RESIZE_COVER_BOTTOM_RIGHT   | 15                          | While maintaining its aspect ratio in the final state, the component's content is scaled to cover the component's entire content box. When there is remaining space in the width direction, the content is right-aligned with the component, so that its right part is displayed. When there is remaining space in the height direction, the content is bottom-aligned with the component, so that its bottom part is displayed.   ![renderfit_resize_cover_bottom_right](figures/renderfit_resize_cover_bottom_right.png) |


> **NOTE**
>
> - In the illustrative diagrams, the blue area indicates the content, and the orange area indicates the component content box.
> - Different render fit modes create different effects during the width and height animation process. Choose the one that best fits your need.

## RenderStrategy<sup>22+</sup>

Enumerates rendering strategies for drawing rounded corners.

**Atomic service API**: This API can be used in atomic services since API version 22.

**Widget capability**: This API can be used in ArkTS widgets since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                                | Value| Description                                      |
| ---------------------------------- | --- | ---------------------------------------- |
| FAST | 0 | Online rendering mode. The content to be rendered is clipped with rounded corners and directly rendered to the main canvas.<br> Note: Online rendering may cause display anomalies in certain scenarios. For example, when blur effects are applied within rounded corner components, background colors may interact and create gradient overlay effects. For detailed behavior, see [Example 3: Configuring Offscreen Rounded Corners](./ts-universal-attributes-border.md#example-3-configuring-offscreen-rounded-corners).|
| OFFSCREEN | 1 | Offscreen rendering mode. The content to be rendered is first rendered to the offscreen canvas without rounded corners, and then clipped with rounded corners and rendered to the main canvas.<br> **NOTE**<br>1. Compared with online rendering, offscreen rendering requires additional performance overhead.<br>2. In offscreen rendering, the content is first rendered on an additional canvas, and then rendered on the main canvas.<br>3. Use offscreen rendering primarily for multi-layer components requiring rounded corners. For single components, it has effect only when the [clip](./ts-universal-attributes-sharp-clipping.md#clip12) attribute, [background color](./ts-universal-attributes-background.md), or [foreground color](./ts-universal-attributes-foreground-color.md) is configured. |

## ScrollSource<sup>12+</sup>

Enumerates the sources of scroll operations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    |  Value | Description                                      |
| ------ | ------ | ---------------------------------------- |
| DRAG   |  0  | Drag event.|
| FLING |  1  | Inertia scrolling after the drag ends.|
| EDGE_EFFECT  |  2  | Edge scrolling effect with **EdgeEffect.Spring**.|
| OTHER_USER_INPUT  |  3  | Other user inputs aside from dragging, such as those from the mouse wheel and keyboard events.|
| SCROLL_BAR  |  4  | Drag event from the scrollbar.|
| SCROLL_BAR_FLING  |  5  | Inertia scrolling with velocity after the scrollbar is released.|
| SCROLLER  |  6  | Non-animated methods of the **Scroller** object.|
| SCROLLER_ANIMATION  |  7  | Animated methods of the **Scroller** object.|

## SharedTransitionEffectType

Sets the animation type.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Description                                      |
| -------- | ---------------------------------------- |
| Static   | The target page element remains in a fixed position, with configurable opacity animation.<br>Currently, this effect only takes effect when configured for redirection to the target page.|
| Exchange | The source page element moves to the position of the target page element and scales accordingly.                 |

## TouchType

Sets the trigger status type of a touch operation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Value  | Description                              |
| ------- | ---- | ---------------------------------- |
| Down   | -    | A finger is pressed.<br>**Atomic service API**: This API can be used in atomic services since API version 11.       |
| Up     | -    | A finger is lifted.<br>**Atomic service API**: This API can be used in atomic services since API version 11.       |
| Move   | -    | A finger moves on the screen in pressed state.<br>**Atomic service API**: This API can be used in atomic services since API version 11.       |
| Cancel | -    | A touch event is canceled. Examples: 1. touching the home button to return to the home screen while keeping a finger on the screen; 2. folding a foldable phone to switch to the external screen while keeping a finger on the screen.<br>**Atomic service API**: This API can be used in atomic services since API version 11.     |
| HOVER_ENTER<sup>20+</sup> | 9    | A finger is pressed in accessibility mode.<br>**Atomic service API**: This API can be used in atomic services since API version 20.       |
| HOVER_MOVE<sup>20+</sup>   | 10    | The mouse pointer moves in accessibility mode.<br>**Atomic service API**: This API can be used in atomic services since API version 20.       |
| HOVER_EXIT<sup>20+</sup> | 11    | The mouse pointer exits the component in accessibility mode.<br>**Atomic service API**: This API can be used in atomic services since API version 20.       |
| HOVER_CANCEL<sup>20+</sup> | 12    | The triggered event is canceled in accessibility mode.<br>**Atomic service API**: This API can be used in atomic services since API version 20.       |

## TitleHeight<sup>9+</sup>

Sets the recommended height of the title bar.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Description                        |
| ----------- | -------------------------- |
| MainOnly    | Recommended height (56 vp) of the title bar when only the main title is available.     |
| MainWithSub | Recommended height (82 vp) of the title bar when both the main title and subtitle exist.|

## TransitionType

Sets the transition type.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value| Description                            |
| ------ | ----- | ------------------------- |
| All    | 0 | The transition takes effect in all scenarios.|
| Insert | 1 | The transition takes effect when a component is inserted or displayed.|
| Delete | 2 | The transition takes effect when a component is deleted or hidden.|

## TextAlign

Sets the horizontal alignment of the text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    |  Value | Description                                      |
| ------ | ------ | ---------------------------------------- |
| Start                     |  0  | Aligned with the start.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| Center                    |  1  | Horizontally centered.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| End                       |  2  | Aligned with the end.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| JUSTIFY<sup>10+</sup>     |  3  | Aligned with both margins.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 10.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| LEFT<sup>23+</sup>        |  4  | Left aligned.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 23.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|
| RIGHT<sup>23+</sup>       |  5  | Right aligned.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 23.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|

## TextOverflow

Sets the display mode when the text is too long.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                   | Value| Description                 |
| --------------------- | ------------ | ------------------- |
| None                  | 0 | Overflowing content is clipped at the limit of the maximum line width.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.|
| Clip                  | 1 | Overflowing content is clipped at the limit of the maximum line width. Same effect as **None**.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.|
| Ellipsis              | 2 | An ellipsis (...) is used to represent text overflow.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.|
| MARQUEE<sup>10+</sup> | 3 | Text continuously scrolls when text overflow occurs.|

## TextDecorationType

Sets the text decoration type.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Value| Description       |
| ----------- | ----------- | --------- |
| None        | 0 | No text decorations.|
| Underline   | 1 | Line below the text. |
| Overline    | 2 | Line above the text. |
| LineThrough | 3 | Line through the text.|

## TextCase

Sets the text case.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Value| Description        |
| --------- | ----------- | ---------- |
| Normal    | 0 | The original case of the text is retained.|
| LowerCase | 1 | All letters in the text are in lowercase.  |
| UpperCase | 2 | All letters in the text are in uppercase.  |

## TextHeightAdaptivePolicy<sup>10+</sup>

Sets the mode of adjusting the text font size to adapt to the layout.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                     | Value| Description                      |
| ----------------------- | ----------- | ------------------------ |
| MAX_LINES_FIRST         | 0 | Sets the text height adaptation mode to [maxLines](ts-basic-components-textarea.md#maxlines10) first.|
| MIN_FONT_SIZE_FIRST     | 1 | Prioritize the **minFontSize** settings.    |
| LAYOUT_CONSTRAINT_FIRST | 2 | Prioritize the layout constraint settings in terms of height.|

## TextContentStyle<sup>10+</sup>

Sets the polymorphic style of the text box.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Value| Description                                                        |
| ------- | ----------- | ------------------------------------------------------------ |
| DEFAULT | - | Default style. The caret width is fixed at 1.5 vp, and the caret height is subject to the background height and font size of the selected text.|
| INLINE  | - | Inline input style. The background height of the selected text is the same as the height of the text box.<br>This style is used in scenarios where editing and non-editing states are obvious, for example, renaming in the file list view.<br>The **showError** attribute is not supported for this style.<br>This style does not allow for text dragging and dropping.|

## TextSelectableMode<sup>12+</sup>

Sets whether text can be selected and focused on.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Value| Description                                                        |
| ------------ | --- | ------------------------------------------------------------ |
| SELECTABLE_UNFOCUSABLE  | 0 | The text is selectable, but not focusable. Setting the **selection**, **bindSelectionMenu**, or **copyOption** attribute does not affect the behavior.|
| SELECTABLE_FOCUSABLE | 1 | The text is selectable and focusable. It obtains focus when touched.|
| UNSELECTABLE     | 2 | The text is not selectable nor focusable. The **selection**, **bindSelectionMenu**, and **copyOption** attributes do not work in this case. |

## TextDecorationStyle<sup>12+</sup>

Sets the style of the text decoration.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Value| Description       |
| ----------- | --- | --------- |
| SOLID   | 0 | Single solid line (default value). |
| DOUBLE | 1 | Double solid line.|
| DOTTED    | 2 | Dotted line. |
| DASHED        | 3 | Dashed line.|
| WAVY        | 4 | Wavy line.|

## TipsAnchorType<sup>20+</sup>

Enumerates anchor types of the tooltip.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   |  Description                  |
| ------  | -------------------- |
| TARGET | The tooltip follows the target component.|
| CURSOR | The tooltip follows the cursor position.|

## VerticalAlign

Sets the vertical alignment mode of child components.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Description          |
| ------ | ------------ |
| Top    | Top aligned.       |
| Center | Center aligned. This is the default alignment mode.|
| Bottom | Bottom aligned.       |

## Visibility

Defines the visibility and layout placeholder status of the component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Value| Description              |
| ------- | ---------------- | ---------------- |
| Hidden  | 1 | The component is hidden, and a placeholder is used for it in the layout.   |
| Visible | 0 | The component is visible.             |
| None    | 2 | The component is hidden. It is not involved in the layout, and no placeholder is used for it.|

## Week

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Description  |
| ---- | ---- |
| Mon  | Monday. |
| Tue  | Tuesday. |
| Wed  | Wednesday. |
| Thur | Thursday. |
| Fri  | Friday. |
| Sat  | Saturday. |
| Sun  | Sunday. |

## WidthBreakpoint<sup>13+</sup>

Enumerates the width breakpoint values corresponding to different window width thresholds. The values are returned through [getWindowWidthBreakpoint](../arkts-apis-uicontext-uicontext.md#getwindowwidthbreakpoint13).

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

The following table lists default width breakpoint thresholds for typical devices, serving as a reference for responsive layout design based on window width breakpoints. Device manufacturers may customize these thresholds through product-specific configurations when needed.

| Name    | Value  | Description                  |
| -------- | ---- | ---------------------- |
| WIDTH_XS | 0   | The window width is less than 320 vp.|
| WIDTH_SM | 1   | The window width is greater than or equal to 320 vp and less than 600 vp.|
| WIDTH_MD | 2   | The window width is greater than or equal to 600 vp and less than 840 vp.|
| WIDTH_LG | 3   | The window width is greater than or equal to 840 vp and less than 1440 vp.|
| WIDTH_XL | 4   | The window width is greater than or equal to 1440 vp.|

## WordBreak<sup>11+</sup>

Sets the word break rule.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Value| Description                                  |
| ----- | --- | -------------------------------------- |
| NORMAL  | 0 | Word breaks can occur between any two characters for Chinese, Japanese, and Korean (CJK) text, but can occur only at a space character for non-CJK text (such as English).<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| BREAK_ALL | 1 | Line breaks can occur between any two characters for non-CJK text. For CJK text, the effect is the same as that of **NORMAL**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| BREAK_WORD | 2 | This option has the same effect as **BREAK_ALL** for non-CJK text, except that it preferentially wraps lines at appropriate characters (for example, spaces) If no breakpoints are found, it breaks between any two characters. For CJK text, the effect is the same as that of **NORMAL**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| HYPHENATION<sup>18+</sup> | 3 | Attempts are made to hyphenate words at the end of each line using a hyphen. If a hyphen cannot be added, this option behaves like **BREAK_WORD**.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|

## XComponentType<sup>10+</sup>

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                            | Description                                                        |
| -------------------------------- | ------------------------------------------------------------ |
| SURFACE                          | The **XComponent** component is used for EGL/OpenGLES and media data input, where the custom content is displayed individually on the screen. When the background color is set to black, the display subsystem (DSS) is used.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| COMPONENT<sup>(deprecated)</sup> | The **XComponent** component is used as a container where non-UI logic can be executed to dynamically load the display content.<br>**NOTE**<br>This component is supported since API version 10 and deprecated since API version 12. You are advised to use other container components instead.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| TEXTURE                          | Supports EGL/OpenGLES and media data rendering. Custom drawing content is composited with XComponent's native content before display. Key features: 1. Maintains frame synchronization between GPU textures and ArkUI drawing commands. 2. Supports unified animation with built-in components. 3. Utilizes GPU composition, which may have higher power consumption than the SURFACE type using the display subsystem (DSS).<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| NODE<sup>(deprecated)</sup>      | Serves as a container for native UI nodes, enabling display of natively developed page components.<br>**NOTE**<br>This component is supported since API version 12 and deprecated since API version 20. You are advised to use the [ContentSlot](../../../ui/rendering-control/arkts-rendering-control-contentslot.md) component.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
