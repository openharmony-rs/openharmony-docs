# PopoverDialogV2

Declare struct PopoverDialogV2

@struct { PopoverDialogV2 }

**Since:** 18

**Decorator:** @ComponentV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## $visible

```TypeScript
$visible?: PopoverDialogV2OnVisibleChange
```

Sets the callback when visibility changed.

**Since:** 18

**Decorator:** @Event

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## popover

```TypeScript
popover: PopoverDialogV2Options
```

Sets the PopoverDialogV2 options.

**Type:** [PopoverDialogV2Options](arkts-arkui-arkui-advanced-dialogv2-popoverdialogv2options-i.md)

**Since:** 18

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## targetBuilder

```TypeScript
targetBuilder: CustomBuilder
```

Sets the targetBuilder content.

**Type:** [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md)

**Since:** 18

**Decorator:** @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## visible

```TypeScript
visible: boolean
```

Sets the PopoverDialogV2 Visible Status.

**Type:** boolean

**Since:** 18

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
