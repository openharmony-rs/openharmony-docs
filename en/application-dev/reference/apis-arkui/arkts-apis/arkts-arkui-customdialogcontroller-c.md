# CustomDialogController

```TypeScript
declare class CustomDialogController
```

Defines the controller of the custom dialog box.

**Since:** 7

<!--Device-unnamed-declare class CustomDialogController--><!--Device-unnamed-declare class CustomDialogController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Objects to Import

```ts
dialogController : CustomDialogController | null = new CustomDialogController(CustomDialogControllerOptions)
```



> **NOTE:** 
> 
> - **CustomDialogController** is effective only when it is a member variable of the @CustomDialog and @Component decorated struct and is defined in the @Component decorated struct. For details, see the following example.
> 
> - You can pass in multiple other controllers in the CustomDialog to open one or more other CustomDialogs in the CustomDialog. In this case, you must place the controller pointing to the self behind all controllers.

## close

```TypeScript
close()
```

Close the dialog box.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomDialogController-close()--><!--Device-CustomDialogController-close()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: CustomDialogControllerOptions)
```

Constructor for a custom dialog box.

> **NOTE:** 
> 
> Custom dialog box parameters do not support dynamic updates. However, by setting **customStyle** to **true** and
> configuring [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor1),
> [backgroundBlurStyle](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundblurstyle1),
> and [size](../arkts-components/arkts-arkui-common-comp.md)-related attributes on the custom component, you can implement dynamic updates via
> state variables bound to these attributes.
> 
> If **CustomDialogController** is used as a global variable to implement global custom dialog boxes, the previous
> dialog box cannot be closed after a new value is assigned to the controller. You are advised to close the dialog
> box before reassigning the value.
> 
> When a custom dialog box is started within another custom dialog box, you are advised not to close the latter
> custom dialog box directly.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomDialogController-constructor(value: CustomDialogControllerOptions)--><!--Device-CustomDialogController-constructor(value: CustomDialogControllerOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CustomDialogControllerOptions](arkts-arkui-customdialogcontrolleroptions-i.md) | Yes | Parameters of the custom dialog box. |

## getState

```TypeScript
getState(): PromptActionCommonState
```

Obtains the state of the custom dialog box.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-CustomDialogController-getState(): PromptActionCommonState--><!--Device-CustomDialogController-getState(): PromptActionCommonState-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [PromptActionCommonState](arkts-arkui-promptactioncommonstate-t.md) | State of the custom dialog box. |

## open

```TypeScript
open()
```

Opens the content of the custom dialog box. This API can be called multiple times. If the dialog box is displayed in a subwindow, no new subwindow is allowed.

> **NOTE:** 
> 
> **CustomDialog** with subwindow display (**showInSubwindow** set to **true**) is not supported in input method
> windows.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomDialogController-open()--><!--Device-CustomDialogController-open()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
