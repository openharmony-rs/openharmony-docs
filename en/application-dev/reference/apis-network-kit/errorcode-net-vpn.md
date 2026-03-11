# VPN Error Codes

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 2200001 Invalid Parameter Value

**Error Information**

Invalid parameter value.

**Description**

Invalid parameter value.

**Possible Causes**

The input parameter value is not within the valid value range.

**Solution**

Check whether the input parameter value is within the valid value range.

## 2200002 Service Connection Failure

**Error Information**

Failed to connect to the service.

**Description**

This error code is reported if a service connection failure occurs.

**Possible Causes**

The service is abnormal.

**Solution**

Check whether system services are running properly.

## 2200003 System Internal Error

**Error Information**

System internal error.

**Description**

Internal system error.

**Possible Causes**

1. The memory is abnormal.

2. A null pointer is present.

**Solution**

1. Check whether the memory space is sufficient. If not, clear the memory and try again.

2. Check whether the system is normal. If not, try again later or restart the device.

## 2203001 Failed to Create a VPN

**Error Information**

VPN creation denied, please check the user type.

**Description**

This error code is reported if a VPN fails to be created.

**Possible Causes**

The login user does not have the operation permission. Specifically, the GUEST user does not have the permission to call the **setUp** API.

**Solution**

Check the type of the login user.


## 2203002 VPN Already Exists

**Error Information**

VPN exist already, please execute destroy first.

**Description**

This error code is reported if a VPN already exists.

**Possible Causes**

The VPN has been created.

**Solution**

Call the **destroy** API to destroy the existing VPN, and then call the **setUp** API.


## 2203004 Invalid Descriptor

**Error Information**

Invalid socket file descriptor.

**Description**

This error code is reported if the socket file descriptor is invalid.

**Possible Causes**

A TCP socket connection fails to be established.

**Solution**

Check whether a TCP socket connection is set up successfully.

## 19900001 Invalid Parameter

**Error Information**

Invalid parameter value.

**Description**

This error code is reported if one or more parameters are invalid.

**Possible Causes**

The type or number of parameters is incorrect.

**Solution**

Check the type and number of parameters.

## 19900002 System Internal Error

**Error Information**

System internal error.

**Description**

This error code is reported if an internal system error occurs.

**Possible Causes**

An internal error is probably due to a null pointer, memory allocation error, or IPC communication error.

**Solution**

Check whether the VPN service is normal.
