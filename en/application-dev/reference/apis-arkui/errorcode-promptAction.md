# Popup Window Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=c48e99653addcebc1ddb3fe176c39e9f27289a83 translatedAt=2026-08-29T09:23:17.804Z pushedAt=2026-08-31T03:57:42.425Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 103301 Dialog Content Error

**Error Message**

The ComponentContent is incorrect.

> **NOTE**
>
> When the called API is [openCustomDialog](arkts-apis-uicontext-promptaction.md#opencustomdialog12), [openCustomDialogWithController](arkts-apis-uicontext-promptaction.md#opencustomdialogwithcontroller18), [closeCustomDialog](arkts-apis-uicontext-promptaction.md#closecustomdialog12), or [updateCustomDialog](arkts-apis-uicontext-promptaction.md#updatecustomdialog12), the returned error is "Dialog content error."The ComponentContent is incorrect.

**Description**

This error code is reported when there is an issue with the content node of the custom dialog box, which prevents the node from being rendered.

**Possible Causes**

The custom content node passed to the dialog box is empty or incorrect.

**Solution**

1. Check whether the content node of the custom dialog box exists. You can do so using the [getFrameNodeById()](./arkts-apis-uicontext-uicontext.md#getframenodebyid12) API.

2. Ensure that the content node can be rendered properly.

## 103302 Custom Dialog Box Already Exists

**Error Message**

The ComponentContent already exists.

**Description**

This error code is reported when an attempt is made to open a custom dialog box that is already open.

**Possible Causes**

The custom dialog box associated with the content node is currently displayed.

**Solution**

Reinitialize and bind a content node that can be rendered properly to the dialog box.

## 103303 Custom Dialog Box Not Found

**Error Message**

The ComponentContent cannot be found.

> **NOTE**
>
> When the called API is [closeCustomDialog](arkts-apis-uicontext-promptaction.md#closecustomdialog12) or [updateCustomDialog](arkts-apis-uicontext-promptaction.md#updatecustomdialog12), the returned error is "Dialog content not found."The ComponentContent cannot be found.

**Description**

This error code is reported when an attempt is made to close or update a custom dialog box that is not open.

**Possible Causes**

The custom dialog box associated with the content node is not open.

**Solution**

1. Ensure that the custom dialog box associated with the content node is open.

2. Ensure that the content node of the custom dialog box is the target content node that needs to be updated or closed.

## 103304 Target ID Not Found

**Error Message**

The targetId does not exist.

**Description**

This error code is reported when no node can be found based on the provided **targetId**.

**Possible Causes**

The provided **targetId** is invalid, or the node corresponding to the **targetId** has been destroyed.

**Solution**

Check whether the node corresponding to the provided **targetId** exists. You can query the node using the [getFrameNodeById()](./arkts-apis-uicontext-uicontext.md#getframenodebyid12) API.

## 103305 Node Specified by targetId Not Mounted on the Component Tree

**Error Message**

The node of targetId is not in the component tree.

**Description**

This error code is reported when the node specified by **targetId** is not mounted on the component tree.

**Possible Causes**

The node specified by **targetId** is not mounted on the component tree.

**Solution**

1. Check whether the node specified by **targetId** exists. You can query the node using the [getFrameNodeById()](./arkts-apis-uicontext-uicontext.md#getframenodebyid12) API.

2. Confirm that the node specified by **targetId** is mounted on the main component tree. You can call the [isAttached()](./js-apis-arkui-frameNode.md#isattached12) API of the content node to check whether it is mounted on the main component tree.

## 103306 Node Mount Failure Causes Dialog Box to Fail to Open

**Error Message**

The dialog cannot be opened due to node mount failure.

**Description**

This error code is reported when the dialog box cannot be opened because the node fails to be mounted.

**Possible Causes**

The content node of the dialog box fails to be mounted, so it cannot be mounted to the node tree for normal rendering and display.

**Solution**

1. Check whether the dialog box content can be rendered and displayed normally.

2. When **levelMode** in [DialogBaseOptions](js-apis-dialog.md#dialogbaseoptions) is set to **LevelMode.EMBEDDED**, verify that the page node corresponding to **levelUniqueId** has been mounted to the node tree before calling the [present](arkts-apis-uicontext-dialogpresenter.md#present) API.

## 103307 Failed to Open the Overlay Due to a System Pop-up Window

**Error Message**

The overlay cannot be opened due to the system pop-up window.

**Description**

This error code is reported when the overlay cannot be opened due to a system pop-up window.

**Possible Causes**

A system pop-up window exists on the current page, blocking the display of the overlay.

**Solution**

Wait until the user closes the system pop-up window and try to open the overlay again.

## 103308 Dialog Box Cannot Be Opened Due to Subwindow Creation Failure

**Error Message**

The dialog cannot be opened due to subwindow create failure.

**Description**

This error code is reported when the dialog box cannot be opened because subwindow creation failed.

**Possible Causes**

1. A system popup window exists on the current page, blocking the display of the overlay and causing the subwindow creation of the dialog box to fail.

2. When the dialog box needs to be displayed in a subwindow (**showInSubWindow** in [DialogBaseOptions](js-apis-dialog.md#dialogbaseoptions) is set to **true**), the subwindow creation fails.

**Solution**

1. Wait for the user to close the system popup window, and then try to open the overlay again.

2. Confirm that the current environment supports subwindow creation, and then try to call the [present](arkts-apis-uicontext-dialogpresenter.md#present) API again.

## 103401 Toast Not Found

**Error Message**

Cannot find the toast. 

**Description**

This error code is reported when an attempt is made to close a toast that is not being displayed.

**Possible Causes**

The toast has not been displayed or has already been closed.

**Solution**

Ensure that the toast is being displayed.

<!--no_check-->