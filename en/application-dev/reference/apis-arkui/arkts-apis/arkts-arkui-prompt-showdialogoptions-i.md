# ShowDialogOptions

```TypeScript
interface ShowDialogOptions
```

Describes the options for showing the dialog box.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [ShowDialogOptions](arkts-arkui-promptaction-showdialogoptions-i.md)

<!--Device-prompt-interface ShowDialogOptions--><!--Device-prompt-interface ShowDialogOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { prompt } from '@kit.ArkUI';
```

## buttons

```TypeScript
buttons?: [Button, Button?, Button?]
```

Array of buttons in the dialog box. The array structure is **{text:'button', color: '#666666'}**. Up to three buttons are supported. The first button is of the **positiveButton** type, the second is of the **negativeButton** type, and the third is of the **neutralButton** type.

**Type:** [Button, Button?, Button?]

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [buttons](arkts-arkui-promptaction-showdialogoptions-i.md#buttons)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ShowDialogOptions-buttons?: [Button, Button?, Button?]--><!--Device-ShowDialogOptions-buttons?: [Button, Button?, Button?]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message?: string
```

Text body.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [message](arkts-arkui-promptaction-showdialogoptions-i.md#message)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ShowDialogOptions-message?: string--><!--Device-ShowDialogOptions-message?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: string
```

Title of the dialog box.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [title](arkts-arkui-promptaction-showdialogoptions-i.md#title)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ShowDialogOptions-title?: string--><!--Device-ShowDialogOptions-title?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
