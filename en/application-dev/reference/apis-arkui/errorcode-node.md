# Custom Node Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangchensu1-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=f9f86808d6457a0596524236c4fda040b8986571 translatedAt=2026-08-29T09:23:08.027Z pushedAt=2026-08-31T03:36:16.568Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 100021 FrameNode Not Modifiable

**Error Message**

The FrameNode is not modifiable.

**Description**

This error code is reported when the current FrameNode is unmodifiable, preventing the requested operation, for example, setting properties, adding or removing child nodes, or binding controllers.

**Possible Causes**

An attempt is made to modify a declarative node.

**Solution**

Avoid performing modification operations on a non-modifiable node. You can use try-catch to catch and handle the error to avoid affecting other logic.

## 100022 Component Type of the FrameNode Does Not Support Adjusting the Cross-Language Common Attribute Configuration Permission

**Error Message**

The FrameNode cannot be set whether to support cross-language common attribute setting.

**Description**

This error code is reported when the component type of the current FrameNode does not support adjusting the cross-language common attribute configuration permission.

**Possible Causes**

You attempt to adjust the cross-language common attribute configuration permission of the target FrameNode.

**Solution**

Avoid calling [setCrossLanguageOptions](./js-apis-arkui-frameNode.md#setcrosslanguageoptions15) to adjust the cross-language access permission on a FrameNode that does not support setting cross-ArkTS language access options. You can refer to the description of **setCrossLanguageOptions** to check whether the target node type supports setting cross-ArkTS language access options.

## 100023 Parameter Error

**Error Message**

Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined.

**Description**

This error code is reported when the parameters passed to the API are incorrect.

**Possible Causes**

1. The component type of the provided node is incorrect.
2. The provided node is null or undefined.
3. The provided controller is null or undefined.

**Solution**

Confirm that the component type of the passed node parameter is correct, and check whether the node parameter or controller parameter is null or undefined before calling the API.

## 100024 No Common Ancestor Node Between Nodes

**Error Message**

The current FrameNode and the target FrameNode do not have a common ancestor node.

**Description**

This error code is reported when the current node and the target node have no common ancestor node.

**Possible Causes**

No common ancestor node can be found between the current node and the target node.

**Solution**

Pass in a target node that has a common ancestor node with the current node.

## 100025 Invalid Parameter Value

**Error Message**

The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'targetNode' is invalid: it cannot be disposed."

**Description**

This error code is reported when the parameter is invalid. The error message contains detailed information about the invalid parameter and its cause. For example: "The parameter 'targetNode' is invalid: the node specified by the parameter cannot be a destroyed node."

**Possible Causes**

The value of the passed parameter is null, undefined, or another invalid value. For the specific cause, see the error message.

**Solution**

1. For **null** or **undefined** value errors: Provide a valid FrameNode instance.
2. When the error message indicates that no common ancestor node is found, check whether the target node is an offscreen node before passing it, and pass a target node that shares a common ancestor node with the current node.
3. Modify the corresponding parameter based on the invalid parameter and cause indicated in the error message.

## 100026 The Instance Object Used to Call the API Has Been Unbound from the Backend Entity Node

**Error Message**

The current FrameNode has been disposed.

**Description**

This error code is reported when the instance object used to call the API has been unbound from the backend entity node.

**Possible Causes**

Before calling the current API, you call the [dispose](./js-apis-arkui-frameNode.md#dispose12) API on this instance object, for example, **item.dispose()**.

**Solution**

1. To continue using this instance object, avoid performing the dispose operation on it.
2. To check whether the instance object is available, call the **isDisposed** API.

## 100027 The Current Node Has Been Adopted as a Child Node

**Error Message**

The current node has been adopted.

**Description**

This error code is reported when the current node has been adopted as a child node and does not support the requested operation.

**Possible Causes**

The current node has been adopted as a child node and does not support the requested operation.

**Solution**

Cancel the state in which the current node is adopted as a child node, and then perform the current operation.

## 100028 Current Node Is Not on the Main Node Tree

**Error Message**

The current FrameNode is not on the main tree.

**Description**

The current node is not on the main node tree.

**Possible Causes**

The current node is not on the main node tree.

**Solution**

Mount the current node to the main node tree before performing the operation.

## 100029 Component Reuse Not Yet Supported by State Management V2 in the BuilderNode

**Error Message**

Reuse/Recycle not implemented for ViewV2, yet.

**Description**

This error code is reported when [state management V2](../../ui/state-management/arkts-state-management-overview.md#state-management-v2) does not support [reuse](./js-apis-arkui-builderNode.md#reuse12) yet in the BuilderNode.

**Possible Causes**

In the BuilderNode, state management V2 does not support component reuse yet.

**Solution**

When using state management V2, do not use component reuse-related features on the BuilderNode. Since API version 26.0.0, custom components in the BuilderNode support V2 component reuse.


## 106103 Operation Not Allowed on Nodes Created by ArkTS

**Error Message**

The corresponding operation does not support nodes created by ArkTS.

**Description**

This error code is reported when the operation does not support nodes created by ArkTS.

**Possible Causes**

The current operation is incompatible with nodes created by ArkTS.

**Solution**

Pass nodes not created by ArkTS.

## 106203 Passed Node Not Mounted to Component Tree

**Error Message**

The node not mounted to component tree.

**Description**

This error code is reported when the passed node is not mounted to the component tree.

**Possible Causes**

The passed node is not mounted to the component tree when the API is called.

**Solution**

Adjust the API call timing to ensure the node is mounted to the component tree.

## 106204 Operations on the Provided Node Not Supported on Non-UI Threads

**Error Message**

Operations on the provided node are not supported on non-UI threads.

**Description**

This error code is reported when an attempt is made to manipulate nodes on a non-UI thread.

**Possible Causes**

1. The API can be called only on the UI thread.
2. The API supports multi-thread calling, but the node operated by the API is in the attached state.

**Solution**

1. Adjust the API call timing to ensure the API is called from the UI thread.
2. Ensure that the node is created by the multi-threaded [createNode](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#createnode) API.
3. Remove all non-convertible attached components from the component tree where the component is located by referring to [Multi-threaded NDK API Set Specifications](../../ui/ndk-build-on-multi-thread.md#multi-threaded-ndk-api-set-specifications).
