# PromptAction

Provides APIs to create and display toasts, dialog boxes, action menus, and custom popups.

> **NOTE:** 
> 
> - The initial APIs of this class are supported since API version 10.
> 
> - In the following API examples, you must first use [getPromptAction()](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) in
> **UIContext** to obtain a **PromptAction** instance, and then call the APIs using the obtained instance.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## closeCustomDialog

```TypeScript
closeCustomDialog<T extends Object>(dialogContent: ComponentContent<T>): Promise<void>
```

Closes a custom dialog box corresponding to **dialogContent**. This API uses a promise to return the result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dialogContent | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content of the custom dialog box. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | Dialog content error. The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-custom-dialog-box-not-found) | Dialog content not found. The ComponentContent cannot be found. |

## closeCustomDialog

```TypeScript
closeCustomDialog(dialogId: number): void
```

Closes the specified custom dialog box.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dialogId | number | Yes | ID of the custom dialog box to close. It is returned from **openCustomDialog**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

## closeMenu

```TypeScript
closeMenu<T extends Object>(content: ComponentContent<T>): Promise<void>
```

Closes the menu corresponding to the provided content. This API uses a promise to return the result.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content displayed in the menu. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-custom-dialog-box-not-found) | The ComponentContent cannot be found. |

## closePopup

```TypeScript
closePopup<T extends Object>(content: ComponentContent<T>): Promise<void>
```

Closes the popup corresponding to the provided **content**. This API uses a promise to return the result.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content displayed in the popup. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-custom-dialog-box-not-found) | The ComponentContent cannot be found. |

## closeToast

```TypeScript
closeToast(toastId: number): void
```

Closes the specified toast.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| toastId | number | Yes | Toast ID returned from **openToast**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |
| [103401](../errorcode-promptAction.md#103401-toast-not-found) | Cannot find the toast. |

## getBottomOrder

```TypeScript
getBottomOrder(): LevelOrder
```

This API returns the order of the dialog box currently at the bottom layer. This information can be used to specify the desired order for subsequent dialog boxes.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [LevelOrder](arkts-arkui-promptaction-levelorder-c.md) | Order of the topmost dialog box. |

## getTopOrder

```TypeScript
getTopOrder(): LevelOrder
```

Obtains the order of the topmost dialog box.

This API returns the order of the dialog box currently at the top layer. This information can be used to specify the desired order for subsequent dialog boxes.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [LevelOrder](arkts-arkui-promptaction-levelorder-c.md) | Order of the topmost dialog box. |

## openCustomDialog

```TypeScript
openCustomDialog<T extends Object>(dialogContent: ComponentContent<T>, options?: promptAction.BaseDialogOptions): Promise<void>
```

Opens a custom dialog box corresponding to **dialogContent**. This API uses a promise to return the result. The dialog box displayed through this API has its content fully following style settings of **dialogContent**. It is displayed in the same way where **customStyle** is set to **true**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dialogContent | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content of the custom dialog box. |
| options | [promptAction.BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md) | No | Dialog box style.<br> Note: If both [isModal](arkts-arkui-promptaction-basedialogoptions-i.md) and [showInSubWindow](arkts-arkui-promptaction-basedialogoptions-i.md) in **BaseDialogOptions** are set to **true**, only **showInSubWindow** takes effect. In this case, the non-modal dialog box is displayed without mask in the subwindow. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | Dialog content error. The ComponentContent is incorrect. |
| [103302](../errorcode-promptAction.md#103302-custom-dialog-box-already-exists) | Dialog content already exist. The ComponentContent has already been opened. |

## openCustomDialog

```TypeScript
openCustomDialog(options: promptAction.CustomDialogOptions): Promise<number>
```

Creates and displays a custom dialog box. This API uses a promise to return the dialog box ID for use with **closeCustomDialog**.

+ *

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [promptAction.CustomDialogOptions](arkts-arkui-promptaction-customdialogoptions-i.md) | Yes | Content of the custom dialog box.<br> + * Note: If both [isModal](arkts-arkui-promptaction-basedialogoptions-i.md) + * and [showInSubWindow](arkts-arkui-promptaction-basedialogoptions-i.md) in **BaseDialogOptions** are set to **true**, + * only **showInSubWindow** takes effect. In this case, the non-modal dialog box is displayed without mask in the subwindow. + |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise that returns the dialog box ID for use with **closeCustomDialog**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

## openCustomDialogWithController

```TypeScript
openCustomDialogWithController<T extends Object>(dialogContent: ComponentContent<T>, controller: promptAction.DialogController,
    options?: promptAction.BaseDialogOptions): Promise<void>
```

Opens a custom dialog box corresponding to **dialogContent**. This API uses a promise to return the result. A dialog box controller can be bound to the custom dialog box, allowing for subsequent control of the dialog box through the controller.

The dialog box displayed through this API has its content fully following style settings of **dialogContent**. It is displayed in the same way where **customStyle** is set to **true**.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dialogContent | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content of the custom dialog box. |
| controller | [promptAction.DialogController](arkts-arkui-promptaction-dialogcontroller-c.md) | Yes | Controller of the custom dialog box. |
| options | [promptAction.BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md) | No | Style of the custom dialog box.<br> Note: If both [isModal](arkts-arkui-promptaction-basedialogoptions-i.md) and [showInSubWindow](arkts-arkui-promptaction-basedialogoptions-i.md) in **BaseDialogOptions** are set to **true**, only **showInSubWindow** takes effect. In this case, the non-modal dialog box is displayed without mask in the subwindow. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | Dialog content error. The ComponentContent is incorrect. |
| [103302](../errorcode-promptAction.md#103302-custom-dialog-box-already-exists) | Dialog content already exist. The ComponentContent has already been opened. |

## openMenu

```TypeScript
openMenu<T extends Object>(content: ComponentContent<T>, target: TargetInfo, options?: MenuOptions): Promise<void>
```

Opens a menu with the specified content. This API uses a promise to return the result.

> **NOTE:** 
> 
> - If an invalid **target** is provided, the menu will not be displayed.
> 
> - You must maintain the provided **content**, on which [updateMenu](#updatemenu) and [closeMenu](#closemenu) rely to identify the target menu.
> 
> - If your **wrapBuilder** includes other components (such as Popup or Chip), the [ComponentContent](arkts-arkui-componentcontent-c.md)constructor must include four parameters, and the **options** parameter must be
> **{ nestingBuilderSupported: true }**.
> 
> - Nested subwindow dialog boxes are not supported. For example, when [openMenu](#openmenu) has
> **showInSubWindow** set to **true**, another dialog box with **showInSubWindow=true** cannot be displayed.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content displayed in the menu. |
| target | [TargetInfo](arkts-arkui-arkui-uicontext-targetinfo-i.md) | Yes | Information about the target component to bind. |
| options | [MenuOptions](../arkts-components/arkts-arkui-menuoptions-i.md) | No | Style of the menu.<br>**NOTE:** <br>The **title** property is not effective.<br> The **preview** parameter supports only the **MenuPreviewMode** type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | The ComponentContent is incorrect. |
| [103302](../errorcode-promptAction.md#103302-custom-dialog-box-already-exists) | The ComponentContent already exists. |
| [103304](../errorcode-promptAction.md#103304-target-id-not-found) | The targetId does not exist. |
| [103305](../errorcode-promptAction.md#103305-node-specified-by-targetid-not-mounted-on-the-component-tree) | The node of targetId is not in the component tree. |

## openPopup

```TypeScript
openPopup<T extends Object>(content: ComponentContent<T>, target: TargetInfo, options?: PopupCommonOptions): Promise<void>
```

Creates and displays a popup with the specified content. This API uses a promise to return the result.

> **NOTE:** 
> 
> - If an invalid **target** is provided, the popup will not be displayed.
> 
> - You must maintain the provided **content**, on which [updatePopup](#updatepopup) and [closePopup](#closepopup) rely to identify the target popup.
> 
> - If your **wrapBuilder** includes other components (such as Popup or Chip), the [ComponentContent](arkts-arkui-componentcontent-c.md)constructor must include four parameters, and the **options** parameter must be
> **{ nestingBuilderSupported: true }**.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content displayed in the popup. |
| target | [TargetInfo](arkts-arkui-arkui-uicontext-targetinfo-i.md) | Yes | Information about the target component to bind. |
| options | [PopupCommonOptions](../arkts-components/arkts-arkui-popupcommonoptions-i.md) | No | Style of the popup. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | The ComponentContent is incorrect. |
| [103302](../errorcode-promptAction.md#103302-custom-dialog-box-already-exists) | The ComponentContent already exists. |
| [103304](../errorcode-promptAction.md#103304-target-id-not-found) | The targetId does not exist. |
| [103305](../errorcode-promptAction.md#103305-node-specified-by-targetid-not-mounted-on-the-component-tree) | The node of targetId is not in the component tree. |

## openToast

```TypeScript
openToast(options: promptAction.ShowToastOptions): Promise<number>
```

Displays a toast. This API uses a promise to return the toast ID for use with **closeToast**.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [promptAction.ShowToastOptions](arkts-arkui-promptaction-showtoastoptions-i.md) | Yes | Toast configuration options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise that returns the toast ID for use with **closeToast**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

## presentCustomDialog

```TypeScript
presentCustomDialog(builder: CustomBuilder | CustomBuilderWithId, controller?: promptAction.DialogController,
    options?: promptAction.DialogOptions): Promise<number>
```

Creates and displays a custom dialog box. This API uses a promise to return the dialog box ID for use with **closeCustomDialog**.

The dialog box ID can be included in the dialog box content for related operations. A dialog box controller can be bound to the custom dialog box, allowing for subsequent control of the dialog box through the controller.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) &#124; [CustomBuilderWithId](arkts-arkui-custombuilderwithid-t.md) | Yes | Content of the custom dialog box. |
| controller | [promptAction.DialogController](arkts-arkui-promptaction-dialogcontroller-c.md) | No | Controller of the custom dialog box. |
| options | [promptAction.DialogOptions](arkts-arkui-promptaction-dialogoptions-i.md) | No | Style of the custom dialog box.<br> Note: If both [isModal](arkts-arkui-promptaction-basedialogoptions-i.md) and [showInSubWindow](arkts-arkui-promptaction-basedialogoptions-i.md) in **BaseDialogOptions** are set to **true**, only **showInSubWindow** takes effect. In this case, the non-modal dialog box is displayed without mask in the subwindow. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise Promise used to return the custom dialog box ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

## showActionMenu

```TypeScript
showActionMenu(options: promptAction.ActionMenuOptions, callback: promptAction.ActionMenuSuccessResponse): void
```

Shows an action menu in the given settings. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [showActionMenu](#showactionmenu)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [promptAction.ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i.md) | Yes | Action menu options. |
| callback | [promptAction.ActionMenuSuccessResponse](arkts-arkui-promptaction-actionmenusuccessresponse-i.md) | Yes | Callback used to return the action menu response result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

## showActionMenu

```TypeScript
showActionMenu(options: promptAction.ActionMenuOptions, callback: AsyncCallback<promptAction.ActionMenuSuccessResponse>): void
```

Creates and displays an action menu. This API uses an asynchronous callback to return the result.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [promptAction.ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i.md) | Yes | Action menu options. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[promptAction.ActionMenuSuccessResponse](arkts-arkui-promptaction-actionmenusuccessresponse-i.md)&gt; | Yes | Callback used to return the result. On success, **err** is **undefined** and **data** contains the action menu response. On failure, **err** provides error details. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

## showActionMenu

```TypeScript
showActionMenu(options: promptAction.ActionMenuOptions): Promise<promptAction.ActionMenuSuccessResponse>
```

Creates and displays an action menu. This API uses a promise to return the result.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [promptAction.ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i.md) | Yes | Action menu options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[promptAction.ActionMenuSuccessResponse](arkts-arkui-promptaction-actionmenusuccessresponse-i.md)&gt; | callback - Promise that returns the action menu response. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

## showDialog

```TypeScript
showDialog(options: promptAction.ShowDialogOptions, callback: AsyncCallback<promptAction.ShowDialogSuccessResponse>): void
```

Creates and displays a dialog box. This API uses an asynchronous callback to return the result.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [promptAction.ShowDialogOptions](arkts-arkui-promptaction-showdialogoptions-i.md) | Yes | Dialog box configuration options. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[promptAction.ShowDialogSuccessResponse](arkts-arkui-promptaction-showdialogsuccessresponse-i.md)&gt; | Yes | Callback used to return the result. On success, **err** is **undefined** and **data** contains the dialog box response. On failure, **err** provides error details. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

## showDialog

```TypeScript
showDialog(options: promptAction.ShowDialogOptions): Promise<promptAction.ShowDialogSuccessResponse>
```

Creates and displays a dialog box. This API uses a promise to return the result.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [promptAction.ShowDialogOptions](arkts-arkui-promptaction-showdialogoptions-i.md) | Yes | Dialog box configuration options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[promptAction.ShowDialogSuccessResponse](arkts-arkui-promptaction-showdialogsuccessresponse-i.md)&gt; | Promise that returns the dialog box response. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

## showToast

```TypeScript
showToast(options: promptAction.ShowToastOptions): void
```

Creates and displays a toast.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [promptAction.ShowToastOptions](arkts-arkui-promptaction-showtoastoptions-i.md) | Yes | Toast configuration options |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

## updateCustomDialog

```TypeScript
updateCustomDialog<T extends Object>(dialogContent: ComponentContent<T>, options: promptAction.BaseDialogOptions): Promise<void>
```

Updates a custom dialog box corresponding to **dialogContent**. This API uses a promise to return the result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dialogContent | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content of the custom dialog box. |
| options | [promptAction.BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md) | Yes | Dialog box style. Currently, only **alignment**, **offset**, **autoCancel**, and **maskColor** can be updated. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | Dialog content error. The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-custom-dialog-box-not-found) | Dialog content not found. The ComponentContent cannot be found. |

## updateMenu

```TypeScript
updateMenu<T extends Object>(content: ComponentContent<T>, options: MenuOptions, partialUpdate?: boolean): Promise<void>
```

Updates the style of the menu corresponding to the provided **content**. This API uses a promise to return the result.

> **NOTE:** 
> 
> - Updating for the following is not supported: **showInSubWindow**, **preview**, **previewAnimationOptions**,
> **transition**, **onAppear**, **aboutToAppear**, **onDisappear**, **aboutToDisappear**, **onWillAppear**,
> **onDidAppear**, **onWillDisappear**, and **onDidDisappear**.
> 
> - The mask style can be updated by configuring [MenuMaskType](../arkts-components/arkts-arkui-menumasktype-i.md). However, this API does not support mask presence toggling (that is, switching the mask from non-existent to existent or vice versa) by setting a boolean value.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content displayed in the menu. |
| options | [MenuOptions](../arkts-components/arkts-arkui-menuoptions-i.md) | Yes | Style of the menu.<br>**NOTE:** <br>1. Updating for the following is not supported: **showInSubWindow**, **preview**, **previewAnimationOptions**, **transition**, **onAppear**, **aboutToAppear**, **onDisappear**, **aboutToDisappear**, **onWillAppear**, **onDidAppear**, **onWillDisappear**, and **onDidDisappear**.<br>2. The mask style can be updated by configuring [MenuMaskType](../arkts-components/arkts-arkui-menumasktype-i.md). However, this API does not support mask presence toggling (that is, switching the mask from non-existent to existent or vice versa) by setting a boolean value. |
| partialUpdate | boolean | No | Whether to update the menu in incremental mode. Default value: **false**.<br> **NOTE:** <br>1. **true**: incremental update, where the specified properties in **options** are updated, and other properties stay at their current value.<br>2. **false**: full update, where all properties except those specified in **options** are restored to default values. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-custom-dialog-box-not-found) | The ComponentContent cannot be found. |

## updatePopup

```TypeScript
updatePopup<T extends Object>(content: ComponentContent<T>, options: PopupCommonOptions, partialUpdate?: boolean): Promise<void>
```

Updates the style of the popup corresponding to the provided **content**. This API uses a promise to return the result.

> **NOTE:** 
> 
> Updating the following properties is not supported: **showInSubWindow**, **focusable**, **onStateChange**, **onWillDismiss**, and **transition**.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content displayed in the popup. |
| options | [PopupCommonOptions](../arkts-components/arkts-arkui-popupcommonoptions-i.md) | Yes | Style of the popup.<br> **NOTE:** <br> Updating the following properties is not supported: **showInSubWindow**, **focusable**, **onStateChange**, **onWillDismiss**, and **transition**. |
| partialUpdate | boolean | No | Whether to update the popup in incremental mode.<br> Default value: **false**<br> **NOTE:** <br> **true**: Incremental update. Only specified attributes in **options** are updated, and the other attributes retain their current values. If the attribute value passed in **options** is invalid or **undefined**, the attribute is not updated.<br> **false**: Full update. Specified attributes in **options** are updated, and the other attributes are restored to their default values. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-custom-dialog-box-not-found) | The ComponentContent cannot be found. |
