# Dialog Box Overview
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

A dialog box is a modal window designed to temporarily display information or pending operations that require user attention without disrupting the user's current context. Users are required to address the dialog box's content before they can return to their previous tasks. The dialog box may not be bound to any specific component and typically contains a variety of elements such as text, lists, text boxes, and images to create a comprehensive layout. ArkUI offers two types of dialog box components to suit different needs: custom and fixed-style.

* Custom dialog box: allows you to pass in custom components to define the appearance and behavior of the dialog box. Available APIs include **CustomDialog** and **openCustomDialog**.
* Fixed-style dialog box: offers a predefined structure for simple and standard interactions. Available APIs include **AlertDialog**, **ActionSheet**, **PickerDialog**, **showDialog**, and **showActionMenu**.

## Use Cases

| Item| Description|
| --- | --- |
|[Global custom dialog box independent of UI components (openCustomDialog)](arkts-uicontext-custom-dialog.md)| Use to dynamically update the attributes of the custom dialog box.|
|[Basic custom dialog box (CustomDialog)](arkts-common-components-custom-dialog.md)| Customize the components and content within the dialog box.|
| [Alert dialog box (AlertDialog)](arkts-fixes-style-dialog.md#alert-dialog-box-alertdialog)| Use to display critical information or operations requiring user focus. Suitable for sensitive action confirmations.|
| [Action sheet (ActionSheet)](arkts-fixes-style-dialog.md#action-sheet-actionsheet)| Use to present lists that require user attention or confirmation.|
|[Picker dialog box (PickerDialog)](arkts-fixes-style-dialog.md#picker-dialog-box-pickerdialog)| Use to allow users to select dates, time, or text.|
| [Common dialog box (showDialog)](arkts-fixes-style-dialog.md#common-dialog-box-showdialog)| Use to handle asynchronous responses after dialog box interactions.|
| [Action menu (showActionMenu)](arkts-fixes-style-dialog.md#action-menu-showactionmenu)| Used to handle asynchronous responses after action menu interactions.|
| [Page-level dialog box](arkts-embedded-dialog.md)| Use when the dialog box needs to switch with navigation page changes.|
| [Dialog box layer management](arkts-dialog-levelorder.md)| Manage the dialog box display sequence using the [levelOrder](../reference/apis-arkui/js-apis-promptAction.md#basedialogoptions11) parameter, available since API version 18.|
| [Dialog controller](arkts-dialog-controller.md)| Bind the [DialogController](../reference/apis-arkui/js-apis-promptAction.md#dialogcontroller18) using the **controller** parameter, available since API version 18.|
| [Dialog box focus policy](arkts-dialog-focusable.md)| Control dialog box focus acquisition using the [focusable](../reference/apis-arkui/js-apis-promptAction.md#basedialogoptions11) parameter, available since API version 19.|
| [Popup mask control](arkts-dialog-mask.md)| Customize the popup mask by setting parameters such as **maskColor** and **maskRect**.|

## Constraints

* It is recommended that you use the dialog box APIs provided by [UIContext](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md)<!--Del-->, except for UI-less scenarios such as [ServiceExtensionAbility](../../application-dev/application-models/serviceextensionability-sys.md)<!--DelEnd-->.
* You can use the [getPromptAction](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getpromptaction) API in **UIContext** to obtain the [PromptAction](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md) object associated with the current UI context.
* Due to system security policies, custom dialog boxes cannot be displayed while system permission dialog boxes are active.
