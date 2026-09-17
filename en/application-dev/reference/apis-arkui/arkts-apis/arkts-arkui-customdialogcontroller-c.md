# CustomDialogController

Defines the controller of the custom dialog box.

## Objects to Import

```ts
dialogController : CustomDialogController | null = new CustomDialogController(CustomDialogControllerOptions)
```

> **NOTE:** 
> 
> - **CustomDialogController** is effective only when it is a member variable of the @CustomDialog and @Component decorated struct and is defined in the @Component decorated struct. For details, see the following example.
> 
> - You can pass in multiple other controllers in the CustomDialog to open one or more other CustomDialogs in the CustomDialog. In this case, you must place the controller pointing to the self behind all controllers. For details,see [Example 1: Opening Nested Dialog Boxes](../../../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#example-1-opening-nested-dialog-boxes). &gt;

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## close

```TypeScript
close()
```

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: CustomDialogControllerOptions)
```

Constructor for a custom dialog box.

> **NOTE:** 
> 
> Custom dialog box parameters do not support dynamic updates. However, by setting **customStyle** to **true** and
> configuring attributes such as background color,
> background blur,
> and width/height on the custom component, dynamic updates can be achieved through state variables
> bound to these attributes.
> 
> If **CustomDialogController** is used as a global variable to implement global custom dialog boxes, the previous
> dialog box cannot be closed after a new value is assigned to the controller. You are advised to close the dialog
> box before reassigning the value.
> 
> When a custom dialog box is started within another custom dialog box, you are advised not to close the latter
> custom dialog box directly.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

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
> windows. For details, see the constraints in
> [createPanel](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethodengine-inputmethodability-i.md#createpanel)
> of the input method framework documentation.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
