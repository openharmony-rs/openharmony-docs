# ShowDialogOptions

```TypeScript
interface ShowDialogOptions
```

Describes the options for showing the dialog box.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## alignment

```TypeScript
alignment?: DialogAlignment
```

Alignment mode of the dialog box in the vertical direction.<br> Default value: **DialogAlignment.Default**<br> **NOTE:** <br> If **showInSubWindow** is set to **true** in **UIExtension**, the dialog box is aligned with the host window based on **UIExtension**.

**Type:** [DialogAlignment](arkts-arkui-dialogalignment-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur style of the dialog box. <br>Default value: **BlurStyle.COMPONENT_ULTRA_THICK** <br>**NOTE:** <br>Setting this parameter to **BlurStyle.NONE** disables the background blur. When **backgroundBlurStyle** is set to a value other than **NONE**, do not set **backgroundColor**. If you do, the color display may not produce the expected visual effect.

**Type:** [BlurStyle](../arkts-components/arkts-arkui-common-comp-blurstyle-e.md)

**Default:** BlurStyle.COMPONENT_ULTRA_THICK

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Background color of the dialog box. <br>Default value: **Color.Transparent**. <br>**NOTE:** <br>The background color will be visually combined with the blur effect when both properties are set. If the resulting effect does not match your design requirements, you can disable the blur effect entirely by explicitly setting the **backgroundBlurStyle** property to **BlurStyle.NONE**.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Default:** Color.Transparent

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttons

```TypeScript
buttons?: Array<Button>
```

Array of buttons in the dialog box. The array structure is {text:'button',&nbsp;color:&nbsp;'\#666666'}. More than one button is supported.

**Type:** Array&lt;[Button](arkts-arkui-promptaction-button-i.md)&gt;

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Whether to respond when the device is in semi-folded mode. The value **true** means to respond when the device is in semi-folded mode. <br>Default value: **false**, meaning not to respond when the device is in semi-folded mode. <br>**NOTE:** <br>For a PC or 2-in-1 device, the prompt is displayed on the upper half of the screen by default when **enableHoverMode** is set to **true**. You can set **hoverModeArea** to display the prompt on the lower half of the screen. For other devices, the prompt is displayed on the lower half of the screen by default when **enableHoverMode** is set to **true**. You can set **hoverModeArea** to display the prompt on the upper half of the screen.

**Type:** boolean

**Default:** false

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

Default display area of the dialog box in semi-folded mode. <br>Default value: **HoverModeAreaType.BOTTOM_SCREEN**

**Type:** [HoverModeAreaType](../arkts-components/arkts-arkui-common-comp-hovermodeareatype-e.md)

**Default:** HoverModeAreaType.BOTTOM_SCREEN

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## immersiveMode

```TypeScript
immersiveMode?: ImmersiveMode
```

Overlay effect for the page-level dialog box. <br>**NOTE:** <br>- Default value: **ImmersiveMode.DEFAULT** <br>- This parameter takes effect only when **levelMode** is set to **LevelMode.EMBEDDED**.

**Type:** [ImmersiveMode](arkts-arkui-promptaction-immersivemode-e.md)

**Default:** ImmersiveMode.DEFAULT

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isModal

```TypeScript
isModal?: boolean
```

Whether the dialog box is a modal, which has a mask applied and does not allow for interaction with other components around the dialog box. <br>**true**: The dialog box is a modal. <br>**false**: The dialog box is not a modal. <br>Default value: **true**.

**Type:** boolean

**Default:** true

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## levelMode

```TypeScript
levelMode?: LevelMode
```

Display level of the dialog box. <br>**NOTE:** <br>- Default value: **LevelMode.OVERLAY** <br>- This parameter takes effect only when **showInSubWindow** is set to **false**.

**Type:** [LevelMode](arkts-arkui-promptaction-levelmode-e.md)

**Default:** LevelMode.OVERLAY

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## levelOrder

```TypeScript
levelOrder?: LevelOrder
```

Display order of the dialog box. <br>**NOTE:** <br>- Default value: **LevelOrder.clamp(0)** <br>- Dynamic updating is not supported.

**Type:** [LevelOrder](arkts-arkui-promptaction-levelorder-c.md)

**Default:** The value returned by LevelOrder.clamp(0)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## levelUniqueId

```TypeScript
levelUniqueId?: number
```

Unique ID of the node under the display level for the page-level dialog box. <br>Value range: a number no less than 0<br>**NOTE:** <br>- This parameter takes effect only when **levelMode** is set to **LevelMode.EMBEDDED**.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

Mask area of the dialog box. Events within the mask area are blocked, while events outside the mask area are transmitted.<br> Default value: **{ x: 0, y: 0, width: '100%', height: '100%' }**<br> **NOTE:** <br> **maskRect** does not take effect when **showInSubWindow** is set to **true**.<br> If only some properties in [Rectangle](../arkui-ts/ts-methods-alert-dialog-box.md#rectangle8) are set, the unset properties default to 0.

**Type:** [Rectangle](../arkts-components/arkts-arkui-common-comp-rectangle-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message?: string | Resource
```

Text body.<br>Default value: **undefined**, which indicates that no content is displayed by default.

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

Offset of the dialog box relative to the alignment position.<br> Default value: **{&nbsp;dx:&nbsp;0&nbsp;,&nbsp;dy:&nbsp;0&nbsp;}**

**Type:** Offset

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: Callback<void>
```

Callback invoked after the dialog box appears. <br>**NOTE:** <br>1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; onWillDisappear &gt; onDidDisappear. <br>2. You can set the callback event for changing the dialog box display effect in **onDidAppear**. The settings take effect next time the dialog box appears. <br>3. When a dialog box is dismissed immediately after being shown, **onWillDisappear** may be triggered before **onDidAppear**. <br>4. If the dialog box is dismissed before its appearance animation is finished, the animation will be interrupted, and **onDidAppear** will not be invoked.

**Type:** Callback&lt;void&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: Callback<void>
```

Callback invoked after the dialog box disappears. <br>**NOTE:** <br>1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; onWillDisappear &gt; onDidDisappear.

**Type:** Callback&lt;void&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: Callback<void>
```

Callback invoked before the dialog box appearance animation. <br>**NOTE:** <br>1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; onWillDisappear &gt; onDidDisappear. <br>2. You can set the callback event for changing the dialog box display effect in **onWillAppear**. The settings take effect next time the dialog box appears.

**Type:** Callback&lt;void&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: Callback<void>
```

Callback invoked before the dialog box disappearance animation. <br>**NOTE:** <br>1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; onWillDisappear &gt; onDidDisappear.

**Type:** Callback&lt;void&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

Shadow of the dialog box. <br> Default value on 2-in-1 devices: **ShadowStyle.OUTER_FLOATING_MD** when the dialog box is focused and **ShadowStyle.OUTER_FLOATING_SM** otherwise On other devices, the dialog box has no shadow by default.

**Type:** [ShadowOptions](../arkts-components/arkts-arkui-common-comp-shadowoptions-i.md) &#124; [ShadowStyle](../arkts-components/arkts-arkui-common-comp-shadowstyle-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

Whether to show the dialog box in a subwindow when the dialog box needs to be displayed outside the main window. <br>**true**: The dialog box is shown in a subwindow. <br>**false** (default): The dialog box is displayed within the application, not in a separate subwindow. <br>Note: A dialog box whose **showInSubWindow** attribute is **true** cannot trigger the display of another dialog box whose **showInSubWindow** attribute is also **true**.

**Type:** boolean

**Default:** false

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

System material of the dialog box. Different materials have different effects and can affect visual attributes such as the background color, border, and shadow of the dialog box.

**Type:** [SystemUiMaterial](../arkts-components/arkts-arkui-common-comp-systemuimaterial-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: string | Resource
```

Title of the dialog box.<br>Default value: **undefined**, which indicates that no title is not displayed by default.

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
