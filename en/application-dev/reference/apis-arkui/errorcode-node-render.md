# Render Node Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 106401 Current Node Is Not a Custom Node

**Error Message**

The node type is not custom node.

**Description**

This error code is reported when the operation is attempted on a node that is not a custom node created on the NDK side.

**Possible Causes**

The provided **ArkUI_NodeHandle** pointer references a node that is not of type ARKUI_NODE_CUSTOM.

**Solution**

When integrating a render node, ensure that you create an NDK node of type ARKUI_NODE_CUSTOM as the root node for the render node.

## 106402 Current Node Already Has Child Nodes

**Error Message**

Node already has children.

**Description**

This error code is reported when the target custom node already contains child nodes.

**Possible Causes**

During render tree construction, the custom node designated as the root node has already mounted child FrameNodes or RenderNodes.

**Solution**

When integrating a render node, verify whether the custom node being used already has child nodes.

## 106403 Current Render Node Has a Parent Component

**Error Message**

RenderNode parent is existed.

**Description**

This error code is reported when the target render node already has a parent node and cannot be mounted under the specified custom component.

**Possible Causes**

The provided **ArkUI_RenderNodeHandle** pointer references a node that is already mounted under another component.

**Solution**

When integrating a render node, verify whether the render node designated as the root is already mounted under another component.

## 106404 Corresponding Render Child Node Not Found

**Error Message**

RenderNode child is not exist.

**Description**

This error code is reported when the corresponding render child node cannot be located.

**Possible Causes**

The render node referenced by the provided **ArkUI_RenderNodeHandle** pointer does not contain a child node at the specified index.

**Solution**

Verify whether the provided index exceeds the node's range, or whether the render node referenced by the pointer contains any child nodes.

## 106405 Parameter Value Out of Range

**Error Message**

Param is out of range.

**Description**

This error code is reported when an input parameter value exceeds the acceptable range for the API.

**Possible Causes**

The provided parameter exceeds the boundary limits defined for the API being called.

**Solution**

Check the valid parameter range for the API being called.

## 106406 Current Render Node Is Obtained from FrameNode

**Error Message**

The RenderNode is obtained from a FrameNode.

**Description**

This error code is reported when an attempt is made to perform unsupported operations on a RenderNode obtained from a FrameNode.

**Possible Causes**

The RenderNode is obtained from a FrameNode. Such nodes only support mounting and unmounting as child nodes; other operations are prohibited.

**Solution**

Skip the node during execution if operations other than mounting and unmounting are attempted.

## 106407 Current Render Node Is Obtained from FrameNode and the FrameNode Is Disposed or No Longer Adopted

**Error Message**

The RenderNode is obtained from a FrameNode, and its corresponding FrameNode is no longer in the adopted state.

**Description**

This error code is reported when the RenderNode is obtained from a FrameNode and its corresponding FrameNode has been unadopted or disposed.
Adoption: establishes a parent-child-like relationship where the parent node provides lifecycle callbacks to the child without actually adding it as a regular child node. The adopted node does not receive events from the parent or respond to events like normal child nodes.

**Possible Causes**

The FrameNode from which the RenderNode is obtained has been unadopted or disposed, making all operations except release invalid.

**Solution**

Release the RenderNode when its source FrameNode is unadopted.

## 106408 Current Node Is Not in Adopted State

**Error Message**

The node is not adopted.

**Description**

This error code is reported when an attempt is made to obtain a RenderNode from a node that is not in the adopted state.
Adoption: establishes a parent-child-like relationship where the parent node provides lifecycle callbacks to the child without actually adding it as a regular child node. The adopted node does not receive events from the parent or respond to events like normal child nodes.

**Possible Causes**

The node is not adopted, making its RenderNode inaccessible.

**Solution**

Use the **adoptChild** API to have the node adopted by another node before obtaining its RenderNode.
