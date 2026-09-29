# DialogSheet

```TypeScript
declare interface DialogSheet
```

The information of sheet item for action sheet style.

**Since:** 26.0.1

<!--Device-dialog-declare interface DialogSheet--><!--Device-dialog-declare interface DialogSheet-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { dialog, DialogBaseAlignment, DialogButtonOrientation, DialogState, DialogResult, DialogDismissal, DialogBaseController } from '@kit.ArkUI';
```

## action

```TypeScript
action: VoidCallback
```

Callback executed when the sheet item is clicked.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogSheet-action: VoidCallback--><!--Device-DialogSheet-action: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Icon of the sheet item.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogSheet-icon?: ResourceStr--><!--Device-DialogSheet-icon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: ResourceStr
```

Title of the sheet item.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogSheet-title: ResourceStr--><!--Device-DialogSheet-title: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
