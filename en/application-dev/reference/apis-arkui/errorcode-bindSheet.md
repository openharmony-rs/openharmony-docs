# Sheet Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=39ca26def5c22dc659f3dc0b76ef62a29421e77a translatedAt=2026-08-29T09:18:47.109Z pushedAt=2026-08-31T02:27:15.680Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 120001 Incorrect bindSheetContent

**Error Message**

The bindSheetContent is incorrect.

**Description**

This error code is reported when the input parameter **bindSheetContent** is incorrect. Ensure that **bindSheetContent** provides valid content node definition (for the value rules, see the **bindSheetContent** parameter description in the corresponding API document).

**Possible Causes**

**bindSheetContent** is empty or its type does not meet the requirements.

**Solution**

1. Check whether the input parameter **bindSheetContent** is correct.
2. Ensure that the input content node is a valid **Builder** or **CustomBuilder** instance.
3. Ensure that the content node has been correctly registered and constructed.

## 120002 Modal for bindSheetContent Already Exists

**Error Message**

The bindSheetContent already exists.

**Description**

This error code is reported in the following scenario: When calling sheet-related APIs such as **bindSheet**, the half-modal page corresponding to the content node already exists.

**Possible Causes**

The modal corresponding to the provided **bindSheetContent** is already displayed.

**Solution**

To open the modal corresponding to the same **bindSheetContent**, close the currently displayed modal and then open it again.

## 120003 No Matching Modal Found

**Error Message**

The bindSheetContent cannot be found.

**Description**

This error code is reported when an API is called to close or update the modal that is not open.

**Possible Causes**

The half-modal page corresponding to the content node is not currently displayed. If an API is called to close or update the half-modal page at this time, this error code is reported. You must open the half-modal page before calling the close or update API.

**Solution**

Ensure that the half-modal page corresponding to the content node is already open before calling the close or update API, and check whether the input **bindSheetContent** exists and has been correctly registered.

## 120004 Specified targetId Does Not Exist

**Error Message**

The targetId does not exist.

**Description**

This error code is reported when the corresponding node cannot be found through **targetId**, because **targetId** is not a valid non-negative node identifier and its corresponding node is not in a valid lifecycle.

**Possible Causes**

**targetId** is invalid (The value must be a non-negative integer), or its corresponding node has been destroyed.

**Solution**

1. Check whether the value of **targetId** is a non-negative number. If it is negative, use a valid **targetId** component identifier.
2. Check whether the node specified by **targetId** is valid. If the node has been destroyed, recreate it or replace it with another valid node. It is recommended that you use the component lifecycle callbacks (such as **onAppear**/**onDisappear**) to confirm that the node has not been destroyed before using **targetId** to call sheet-related APIs.

## 120005 Node Specified by targetId Is Not Mounted on the Component Tree

**Error Message**

The node of targetId is not in the component tree.

**Description**

This error code is reported when the node specified by **targetId** is not mounted on the component tree if the half-modal page mode is set to **EMBEDDED** mode.

**Possible Causes**

When the **EMBEDDED** mode is specified for the modal, the node corresponding to the specified **targetId** is not mounted to the component tree.

**Solution**

Wait until the node specified by **targetId** is mounted on the tree before calling the API, or set **SheetMode** to **OVERLAY**. The **EMBEDDED** mode requires that the node specified by **targetId** be mounted on the node tree and be a child node of a page node or NavDestination node; the **OVERLAY** mode has no such restriction.

## 120006 Node Specified by targetId Is Not a Child of a Page Node or NavDestination Node

**Error Message**

The node of targetId is not a child of the page node or NavDestination node.

**Description**

This error code is reported in the following scenario: When the half-modal page mode is set to the **EMBEDDED** mode, the node specified by **targetId** is not a child node of a page node or NavDestination node.

**Possible Causes**

When the half-modal page mode is set to the **EMBEDDED** mode (that is, the half-modal page is embedded in the parent component layout for display, and the page node or NavDestination node needs to be found upward from the parent node), the page node or NavDestination node cannot be found upward from the node specified by **targetId**.

**Solution**

Select a different **targetId** that is a child of a page or **NavDestination** node; or use the OVERLAY mode for the modal.
