# State Management Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 130000 Invalid Target Object for addMonitor/clearMonitor

**Error Message**

The target is not a custom component instance or V2 class instance.

**Description**

This error code is reported when the target object parameter for [addMonitor](./js-apis-StateManagement.md#addmonitor20) or [clearMonitor](./js-apis-StateManagement.md#clearmonitor20) is invalid.

**Possible Causes**

The target object does not meet the following requirements:
- A class decorated with [\@ObservedV2](../../ui/state-management/arkts-new-observedV2-and-trace.md) (must have at least one variable decorated with [\@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md))
- An instance of a custom component decorated with [\@ComponentV2](../../ui/state-management/arkts-create-custom-components.md#componentv2)

**Solution**

Ensure that the target object for **addMonitor** or **clearMonitor** is valid. For details, see [addMonitor and clearMonitor APIs: Dynamically Adding or Removing Listeners](../../ui/state-management/arkts-new-addMonitor-clearMonitor.md#constraints).

## 130001 Invalid Path for addMonitor/clearMonitor

**Error Message**

The path is invalid.

**Description**

This error code is reported when the path parameter for **addMonitor** or **clearMonitor** is invalid.

**Possible Causes**

The path is not a string or not an array type.

**Solution**

Ensure that the path for **addMonitor** or **clearMonitor** is valid. For details, see [addMonitor and clearMonitor APIs: Dynamically Adding or Removing Listeners](../../ui/state-management/arkts-new-addMonitor-clearMonitor.md#constraints).

## 130002 Invalid Callback for addMonitor/clearMonitor

**Error Message**

monitorCallback is not a function or an anonymous function.

**Description**

This error code is reported when the callback parameter for **addMonitor** or **clearMonitor** is invalid.

**Possible Causes**

The callback is not of function type, or is an anonymous function.

**Solution**

Ensure that the callback for **addMonitor** or **clearMonitor** is valid. For details, see [addMonitor and clearMonitor APIs: Dynamically Adding or Removing Listeners](../../ui/state-management/arkts-new-addMonitor-clearMonitor.md#constraints).

## 140001 Invalid Invocation of applySync, flushUpdates, or flushUIUpdates

**Error Message**

The function is not allowed to be called in @Computed.

**Description**

This error code is reported when the **applySync**, **flushUpdates**, or **flushUIUpdates** API is called in a getter method decorated with @Computed.

**Possible Causes**

The **applySync**, **flushUpdates**, or **flushUIUpdates** API is called in a getter method decorated with @Computed.

**Solution**

Ensure that the **applySync**, **flushUpdates**, and **flushUIUpdates** APIs are not called within getter methods decorated with @Computed.

## 140002 Invalid Invocation of flushUpdates or flushUIUpdates

**Error Message**

The function is not allowed to be called in @Monitor.

**Description**

This error code is reported when the **flushUpdates** or **flushUIUpdates** API is called in an @Monitor callback method.

**Possible Causes**

The **flushUpdates** or **flushUIUpdates** API is called in an @Monitor callback method.

**Solution**

Ensure that the **flushUpdates** and **flushUIUpdates** APIs are not called in @Monitor callback methods.
