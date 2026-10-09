# Dialog Overview
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=2cc73d7d182d218c670a07a736f004753da3279f translatedAt=2026-09-21T02:37:39.125Z pushedAt=2026-09-21T09:33:12.907Z -->

A dialog is a modal window that temporarily displays information requiring user attention or pending operations while maintaining the current context. A dialog does not need to be bound to any component, and its content typically consists of multiple components such as text, lists, input boxes, and images to achieve the desired layout. ArkUI currently provides two categories of dialog components: **custom** and **fixed style**.

* **Custom dialog:** allows you to pass in custom components to populate the dialog based on your use case, enabling customized dialog content. Key APIs include the basic custom dialog (**CustomDialog**) and the global custom dialog (**openCustomDialog**), which does not depend on any UI component.
* **Fixed-style dialog:** offers a predefined structure for simple and standard interactions. Available APIs include **AlertDialog**, **ActionSheet**, **PickerDialog**, **showDialog**, and **showActionMenu**.

## Use Cases

| Item| Description|
| --- | --- |
|[Global custom dialog independent of UI components (openCustomDialog)](arkts-uicontext-custom-dialog.md)| Used to dynamically update the attributes of the custom dialog.|
|[Basic custom dialog (CustomDialog)](arkts-common-components-custom-dialog.md)| Used to customize the components and content within the dialog.|
| [Alert dialog (AlertDialog)](arkts-fixes-style-dialog.md#alert-dialog-box-alertdialog)| Used to display critical information or operations requiring user focus. Suitable for sensitive action confirmations.|
| [List selection dialog (ActionSheet)](arkts-fixes-style-dialog.md#action-sheet-actionsheet) | Fixed-style dialog, used when the information that the user needs to focus on or confirm involves list selection. |
|[Picker dialog (PickerDialog)](arkts-fixes-style-dialog.md#picker-dialog-box-pickerdialog)| Fixed-style dialog, used to allow users to select dates, time, or text.|
| [Common dialog (showDialog)](arkts-fixes-style-dialog.md#common-dialog-box-showdialog)| Fixed-style dialog, used to handle asynchronous responses after dialog interactions.|
| [Action menu (showActionMenu)](arkts-fixes-style-dialog.md#action-menu-showactionmenu)| Fixed-style dialog, used to handle asynchronous responses after action menu interactions.|
| [Page-level dialog](arkts-embedded-dialog.md)| Used when the dialog needs to switch with navigation page changes.|
| [Dialog layer management](arkts-dialog-levelorder.md)| Used to manage the dialog display sequence using the [levelOrder](../reference/apis-arkui/js-apis-promptAction.md#basedialogoptions11) parameter, available since API version 18.|
| [Dialog controller](arkts-dialog-controller.md)| Used to bind the [DialogController](../reference/apis-arkui/js-apis-promptAction.md#dialogcontroller18) using the **controller** parameter, available since API version 18.|
| [Dialog focus policy](arkts-dialog-focusable.md)| Used to control dialog focus acquisition using the [focusable](../reference/apis-arkui/js-apis-promptAction.md#basedialogoptions11) parameter, available since API version 19.|
| [Dialog mask control](arkts-dialog-mask.md)| Used to customize the dialog mask by setting parameters such as **maskColor** and **maskRect**.|

## Constraints

* It is recommended that you use the dialog APIs provided by [UIContext](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md)<!--Del-->, except for UI-less scenarios such as [ServiceExtensionAbility](../../application-dev/application-models/serviceextensionability-sys.md)<!--DelEnd-->.
* You can use the [getPromptAction](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getpromptaction) API in **UIContext** to obtain the [PromptAction](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md) object associated with the current UI context.
* Due to system security policies, custom dialogs cannot be displayed while system permission dialogs are active.


