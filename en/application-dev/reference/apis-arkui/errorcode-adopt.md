# Auxiliary Node Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 106206 The Node Has Been Accepted as an Auxiliary Node

**Error Message**

The node has already been adopted.

**Description**

This error code is reported when the node has been accepted as an auxiliary node and cannot be mounted as a child node.<br>

**Possible Causes**

The node has been accepted as an auxiliary node and cannot be mounted as a child node.

**Solution**

Cancel the acceptance of the node and then mount it as a child node.

## 106207 The Auxiliary Node to Accept Has a Parent Node

**Error Message**

This node already has a parent node.

**Description**

This error code is reported when the node already has a parent node and cannot be accepted by other nodes.<br>

**Possible Causes**

The node already has a parent node and cannot be accepted by other nodes.

**Solution**

Remove the node from its parent node and then accept the node.

## 106208 The Node Cannot Be Accepted as an Auxiliary Node

**Error Message**

The node cannot be adopted.

**Description**

This error code is reported when the node cannot be accepted as an auxiliary node.<br>

**Possible Causes**

1. The node is a null pointer.
2. The node does not meet the acceptance criteria. Only the following node types are supported for acceptance:
    - Command node created using the ArkTS language.
    - Command node created using the C language.
    - Root node of BuilderNode.

**Solution**

Ensure that the node is not a null pointer and meets the acceptance criteria before attempting to accept it.

## 106209 The Node Cannot Accept Other Nodes

**Error Message**

The node cannot adopt children.

**Description**

This error code is reported when the node cannot accept other auxiliary nodes.<br>

**Possible Causes**

1. The node is a null pointer.
2. The node cannot be accepted. Only the following nodes can be accepted:
    - Command node created using the ArkTS language.
    - Command node created using the C language.

**Solution**

Ensure that the node is not a null pointer and meets the acceptance criteria before attempting to accept it.

## 106210 The Node Is Not an Affiliated Node Accepted by the Target Node

**Error Message**

This child is not adopted by the parent node.

**Description**

This error code is reported when the child node is not accepted by the target parent node.<br>

**Possible Causes**

1. The child node has not been accepted by any parent node.
2. The child node has been accepted, but the accepting parent node is not the current target node.

**Solution**

If the node is not accepted as an affiliated node by the target node, there is no need to perform the removal operation for this node.
