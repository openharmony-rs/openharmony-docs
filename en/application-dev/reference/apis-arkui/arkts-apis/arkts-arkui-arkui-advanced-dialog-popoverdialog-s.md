# PopoverDialog

```TypeScript
export declare struct PopoverDialog
```

Defines a follow-hand dialog box that pops up based on the position of the target component. The aforementioned **TipsDialog**, **SelectDialog**, **ConfirmDialog**, **AlertDialog**, **LoadingDialog**, and **CustomContentDialog** can all serve as the content of the dialog box.

**Since:** 14

**Decorator:** @Component

<!--Device-unnamed-export declare struct PopoverDialog--><!--Device-unnamed-export declare struct PopoverDialog-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AlertDialog, ButtonOptions, ConfirmDialog, LoadingDialog, SelectDialog, TipsDialog, CustomContentDialog, PopoverDialog, PopoverOptions } from '@kit.ArkUI';
```

## popover

```TypeScript
popover: PopoverOptions
```

Parameters of the follow-hand dialog box, including the dialog box content, position, and other attributes. For details, see **PopoverOptions** type description.

**Type:** [PopoverOptions](arkts-arkui-arkui-advanced-dialog-popoveroptions-i.md)

**Since:** 14

**Decorator:** @Require, @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-PopoverDialog-popover: PopoverOptions--><!--Device-PopoverDialog-popover: PopoverOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## targetBuilder

```TypeScript
targetBuilder: Callback<void>
```

Builder function of the target component on which the follow-hand dialog box is based, used to define the reference position component for displaying the dialog box.

**Type:** Callback&lt;void&gt;

**Since:** 14

**Decorator:** @Require, @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-PopoverDialog-targetBuilder: Callback<void>--><!--Device-PopoverDialog-targetBuilder: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## visible

```TypeScript
visible: boolean
```

Whether to show the follow-hand dialog box. The value **true** means to show the dialog box, and **false** means to hide it.

The default value is **false**.

**Type:** boolean

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-PopoverDialog-visible: boolean--><!--Device-PopoverDialog-visible: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
