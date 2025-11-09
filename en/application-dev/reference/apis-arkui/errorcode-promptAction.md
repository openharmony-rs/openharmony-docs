# promptAction Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @HelloCrease-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 100001 Internal Error

**Error Message**

Internal error.

**Description**

This error code is reported when an internal system issue that cannot be resolved through application-level changes. The specific internal error type is provided in the error details.

**Possible Causes**

The operation for obtaining the rendering engine or parsing parameters fails.

**Solution**

N/A

## 103301 Dialog Content Error

**Error Message**

The ComponentContent is incorrect.

> **NOTE**
>
> When the called API is [openCustomDialog](arkts-apis-uicontext-promptaction.md#opencustomdialog12), [openCustomDialogWithController](arkts-apis-uicontext-promptaction.md#opencustomdialogwithcontroller18), [closeCustomDialog](arkts-apis-uicontext-promptaction.md#closecustomdialog12), or [updateCustomDialog](arkts-apis-uicontext-promptaction.md#updatecustomdialog12), the returned error is "Dialog content error."The ComponentContent is incorrect.

**Description**

This error code is reported when there is an issue with the content node of the custom dialog box, which prevents the node from being rendered.

**Possible Causes**

The custom component node passed to the dialog box is empty or incorrect.

**Solution**

N/A

## 103302 Custom Dialog Box Already Exists

**Error Message**

The ComponentContent already exists.

**Description**

This error code is reported when an attempt is made to open a custom dialog box that is already open.

**Possible Causes**

The custom dialog box associated with the content node is currently displayed.

**Solution**

N/A

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

N/A

## 103304 Target ID Not Found

**Error Message**

The targetId does not exist.

**Description**

This error code is reported when no node can be found based on the provided **targetId**.

**Possible Causes**

The provided **targetId** is invalid, or the node corresponding to the **targetId** has been destroyed.

**Solution**

N/A

## 103305 Node Not Mounted

**Error Message**

The node of targetId is not in the component tree.

**Description**

This error code is reported when the node corresponding to the provided **targetId** is not mounted in the component tree.

**Possible Causes**

The node with the specified **targetId** is not mounted in the component tree.

**Solution**

N/A

## 103401 Toast Not Found

**Error Message**

Cannot find the toast. 

**Description**

This error code is reported when an attempt is made to close a toast that is not being displayed.

**Possible Causes**

The toast has not been displayed or has already been closed.

**Solution**

N/A
