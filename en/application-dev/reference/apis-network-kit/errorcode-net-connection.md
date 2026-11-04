# Network Connection Management Error Codes

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c8d611da517c0df9bbfb2e4952764bf8397e713e translatedAt=2026-11-04T06:35:53.728Z pushedAt=2026-11-04T08:04:44.865Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 2100001 Invalid Parameter Value

**Error Message**

Invalid parameter value.

**Description**

This error code is reported if the parameter value is invalid.

**Cause**

The input parameter value is not within the valid value range.

**Procedure**

Check whether the input parameter value is within the valid value range.

## 2100002 Service Connection Failure

**Error Message**

Failed to connect to the service.

**Description**

This error code is reported if a service connection failure occurs.

**Cause**

The service is abnormal.

**Procedure**

Check whether system services are running properly.

## 2100003 System Internal Error

**Error Message**

System internal error.

**Description**

This error code is reported if a system internal error occurs.

**Cause**

1. Memory exception.

2. Null pointer.

**Procedure**

1. Check whether the memory space is sufficient, and clear the memory and try again.

2. The system is abnormal. Try again later or restart the device.

## 2101007 Callback Not Exist

**Error Message**

The callback does not exist.

**Description**

This error code is reported if a **callback** object to be unregistered does not exist.

**Cause**

The **callback** object has not been registered for activating a network or listening to network status changes.

**Procedure**

Before unregistering a **callback** object, make sure that it has been registered for activating a network or listening to network status changes.

## 2101008 Callback Already Exists

**Error Message**

The callback already exists.

**Description**

This error code is reported if the same callback already exists.

**Cause**

The **callback** object has been registered for activating a network or listening to network status changes.

**Procedure**

1. Ensure that the callback object to be registered has not been registered before.

2. If the callback object has already been registered, perform the existing registration.


## 2101022 Number of Requests Exceeding the Maximum

**Error Message**

The number of requests exceeded the maximum allowed.

**Description**

This error code is reported if the number of network requests exceeds the maximum.

**Cause**

1. The number of network requests with specified properties that are activated and listened for exceeds the maximum.

2. The NetConnection.register API exceeds the maximum number of registrations.

**Procedure**

1. Locate the problem based on the log message "Over the max request number".

2. After using the NetConnection.register API, call the unregister API in a timely manner to cancel the registration.

## 2100301 Failed to Authenticate the Caller (Non-VPN Application)

**Error Message**

Incorrect usage in non-VPN application.

**Description**

The API caller is not a VPN application.

**Cause**

The API caller is not a VPN application.

**Procedure**

Ensure that the API is called in a VPN application.

## 2100400 Incorrect NIC Name (Non-Ethernet)

**Error Message**

The input network interface is incorrect.

**Description**

The NIC name passed in the API call is incorrect.

**Cause**

The NIC name passed in the API call is not an Ethernet NIC name such as **eth0**.

**Procedure**

Ensure that the NIC name is an Ethernet NIC name such as **eth0**.

## 2100401 No IP Address Configured on the VLAN Is Found

**Error Message**

The input ip address not found.

**Description**

The input IP address is not found.

**Cause**

The input IP address is not found on the VLAN.

**Procedure**

Ensure that the input IP address is configured on the VLAN.