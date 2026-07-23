# NodeAdapter Error Codes

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiaxiaguang-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e98b791a1f57fab5012a75ce7d9ff0a0466dd410 translatedAt=2026-07-17T07:01:28.910Z pushedAt=2026-07-17T07:10:50.082Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 106104 NodeAdapter Not Bound

**Error Message**

The lazy loading adapter is not bound to the component.

**Description**

This error code is reported when no NodeAdapter is bound to the component.

**Possible Causes**

The component does not have a NodeAdapter set. The NodeAdapter must be bound to the component before node operations can be performed.

**Solution**

Set a **NodeAdapter** for the component.

## 106105 NodeAdapter Already Exists

**Error Message**

The adapter already exists.

**Description**

This error code is reported when an attempt is made to create a duplicate NodeAdapter instance.

**Possible Causes**

The NodeAdapter already exists and does not support adding or deleting child nodes.

**Solution**

Remove the NodeAdapter or perform child node adding or deletion elsewhere.

## 106106 Child Node Exists

**Error Message**

The corresponding node already has a child node and cannot add an adapter.

**Description**

This error code is reported when the component already has a child node.

**Possible Causes**

The component already has a child node, and the NodeAdapter cannot be applied to non-empty components.

**Solution**

Remove the existing child node or select a parent component for the NodeAdapter.

## 106107 Index Out of Range

**Error Message**

The parameter length in the parameter event exceeds the limit.

**Description**

This error code is reported when the **index** parameter in a component event exceeds the array length limit.

**Possible Causes**

The **index** parameter passed exceeds the array length limit.

**Solution**

Make sure the index parameter does not exceed the length limit of the input array.

## 106108 Data Not Found

**Error Message**

The data does not exist in the component event.

**Description**

This error code is reported when the specified data does not exist in the component event.

**Possible Causes**

The data to access is not included in the event.

**Solution**

Check whether the current event contains the data to be queried.

## 106109 Return Value Not Supported

**Error Message**

The component event does not support return values.

**Description**

This error code is reported when an attempt is made to obtain a return value from a component event that does not support return values.

**Possible Causes**

The component event does not support return values.

**Solution**

Remove the code related to obtaining the event return value.

## 106110 Unsupported Event Type

**Error Message**

The event type is not supported.

**Description**

This error code is reported when the event type passed when registering a universal event is not supported.

**Possible Causes**

The passed event type is not among the supported event types.

**Solution**

Check whether the event type value of the function input parameter falls within the range of supported event types.