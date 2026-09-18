# DialogStyleOptions

Options for the fixed-style dialog.

**Inheritance/Implementation:** DialogStyleOptions extends [DialogBaseOptions](arkts-arkui-dialog-dialogbaseoptions-i.md)

**Since:** 26.1.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { dialog, DialogBaseAlignment, DialogButtonOrientation, DialogState, DialogResult, DialogDismissal, DialogBaseController } from '@kit.ArkUI';
```

## buttonDirection

```TypeScript
buttonDirection?: DialogButtonOrientation
```

The arrangement of buttons.

**Type:** [DialogButtonOrientation](arkts-arkui-arkui-dialog-dialogbuttonorientation-e.md)

**Default:** DialogButtonOrientation.AUTO

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttons

```TypeScript
buttons?: Array<DialogButton>
```

Array of buttons in the dialog box. When provided, the dialog displays as an alert-style dialog with buttons. When used together with sheets, buttons are displayed below the sheet list.

**Type:** Array&lt;[DialogButton](arkts-arkui-dialog-dialogbutton-i.md)&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## gridCount

```TypeScript
gridCount?: number
```

Grid count of dialog. The value should be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message?: DialogMessage
```

Message content and text style of the dialog box.

**Type:** [DialogMessage](arkts-arkui-dialog-dialogmessage-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sheets

```TypeScript
sheets?: Array<DialogSheet>
```

Array of sheet items for action-sheet style. When provided, the dialog displays sheet items for user selection.

**Type:** Array&lt;[DialogSheet](arkts-arkui-dialog-dialogsheet-i.md)&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## subtitle

```TypeScript
subtitle?: ResourceStr
```

Subtitle of the dialog box.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: ResourceStr
```

Title of the dialog box.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
