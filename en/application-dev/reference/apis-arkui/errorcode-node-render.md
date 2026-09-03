# Render Node Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=f9f86808d6457a0596524236c4fda040b8986571 translatedAt=2026-08-29T09:22:40.108Z pushedAt=2026-08-31T03:35:47.086Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 106401 Current Node Is Not a Custom Node

**Error Message**

The node type is not custom node.

**Description**

This error code is reported when the operation is attempted on a node that is not a custom node created on the NDK side.

**Possible Causes**

The provided **ArkUI_NodeHandle** pointer references a node that is not of type **ARKUI_NODE_CUSTOM**.

**Solution**

When integrating a render node process, create an NDK node of the **ARKUI_NODE_CUSTOM** type as the root node of the render node.

## 106402 Current Node Already Has Child Nodes

**Error Message**

Node already has children.

**Description**

This error code is reported when the target custom node already contains child nodes.

**Possible Causes**

During render tree construction, the custom node designated as the root node has already mounted child FrameNodes or RenderNodes.

**Solution**

When integrating a render node, check whether the custom node being used already has child nodes. If yes, remove the child nodes first.

## 106403 Current Render Node Has a Parent Node

**Error Message**

RenderNode parent is existed.

**Description**

This error code is reported when the target render node already has a parent node and cannot be mounted under the specified custom component.

**Possible Causes**

The provided **ArkUI_RenderNodeHandle** pointer references a node that is already mounted under another component.

**Solution**

When integrating a render node, use the RenderNode that has not been mounted under another component. If the RenderNode already has a parent node, remove it from the parent node first.

## 106404 Corresponding Render Child Node Not Found

**Error Message**

RenderNode child is not exist.

**Description**

This error code is reported when the corresponding render child node cannot be located.

**Possible Causes**

The render node referenced by the provided **ArkUI_RenderNodeHandle** pointer does not contain a child node at the specified index.

**Solution**

Verify that the render node referenced by the **ArkUI_RenderNodeHandle** pointer has child nodes, and adjust the provided index to fall within the valid child node index range of that node.

## 106405 Parameter Value Out of Range

**Error Message**

Param is out of range.

**Description**

This error code is reported when an input parameter value exceeds the acceptable range for the API.

**Possible Causes**

The provided parameter exceeds the boundary limits defined for the API being called.

**Solution**

Check the valid parameter range for the API and adjust the parameter value to fall within this range.

## 106406 Current Render Node Is Obtained from FrameNode

**Error Message**

The RenderNode is obtained from a FrameNode.

**Description**

This error code is reported when the operation is attempted on the RenderNode that is obtained from a FrameNode.

**Possible Causes**

The RenderNode is obtained from a FrameNode. Such nodes only support mounting and unmounting as child nodes; other operations are prohibited.

**Solution**

The current node can only be mounted or unmounted as a child node. Skip this node when performing other operations.

## 106407 Current Render Node Is Obtained from FrameNode and the FrameNode Is Disposed or No Longer Adopted

**Error Message**

The RenderNode is obtained from a FrameNode, and its corresponding FrameNode is no longer in the adopted state.

**Description**

This error code is reported when the FrameNode from which the RenderNode is obtained has been disposed of or is no longer adopted.

**Possible Causes**

After the RenderNode is obtained from the adopted FrameNode, the FrameNode is no longer adopted or is destructed.

**Solution**

If the adopted FrameNode is removed from adoption through [OH_ArkUI_NativeModule_RemoveAdoptedChild](./capi-native-node-h.md#oh_arkui_nativemodule_removeadoptedchild), or the FrameNode is destroyed, call [OH_ArkUI_RenderNodeUtils_DisposeNode](./capi-native-render-h.md#oh_arkui_rendernodeutils_disposenode) to release the RenderNode previously obtained through [OH_ArkUI_RenderNodeUtils_GetRenderNode](./capi-native-render-h.md#oh_arkui_rendernodeutils_getrendernode).

## 106408 Current Node Is Not in Adopted State

**Error Message**

The node is not adopted.

**Description**

This error code is reported when the node is not adopted, making its RenderNode inaccessible.

**Possible Causes**

Before calling **OH_ArkUI_RenderNodeUtils_GetRenderNode**, the node is not adopted as a child node through **OH_ArkUI_NativeModule_AdoptChild**.

**Solution**

Use the [OH_ArkUI_NativeModule_AdoptChild](./capi-native-node-h.md#oh_arkui_nativemodule_adoptchild) API to have the node adopted by another node before obtaining its RenderNode.
