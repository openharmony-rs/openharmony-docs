# DialogBaseController

```TypeScript
export class DialogBaseController
```

The class used to control dialog.

**Since:** 26.0.1

<!--Device-unnamed-export class DialogBaseController--><!--Device-unnamed-export class DialogBaseController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { dialog, DialogBaseAlignment, DialogButtonOrientation, DialogState, DialogResult, DialogDismissal, DialogBaseController } from '@kit.ArkUI';
```

## close

```TypeScript
close(): void
```

Close the corresponding dialog.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseController-close(): void--><!--Device-DialogBaseController-close(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

The constructor.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseController-constructor()--><!--Device-DialogBaseController-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getState

```TypeScript
getState(): DialogState
```

Get the state.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseController-getState(): DialogState--><!--Device-DialogBaseController-getState(): DialogState-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DialogState](arkts-arkui-arkui-dialog-dialogstate-e.md) | return the state. |
