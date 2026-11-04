# Link Enhancement Error Codes
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @wangJE-->
<!--Designer: @yangjun044-->
<!--Tester: @Ytt-test-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=abc070d087941bbce389e111810c120cfdf1eab7 translatedAt=2026-11-03T12:58:04.533Z pushedAt=2026-11-04T08:47:59.642Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 32390200 Client Connection Timeout

**Error Message**

Connect timeout.

**Description**

This error code is reported if a client connection fails due to a timeout.

**Possible Causes**

The server does not respond before the timeout.

**Solution**

Try again after the timeout. If a connection to the remote device exists, disconnect the connection and try again.

## 32390201 Server Service Not Started

**Error Message**

Peer server is not started.

**Description**

This error code is reported if the corresponding service on the server is not started.

**Possible Causes**

The server application failed to start the corresponding service.

**Solution**

Check whether the corresponding service is started on the target device. If not, start the service and then initiate a connection.

## 32390202 Number of Services Exceeding the Limit

**Error Message**

The number of servers exceeds the limit.

**Description**

This error code is reported if the number of services exceeds the limit.

**Possible Causes**

The number of requested service resources exceeds 10.

**Solution**

The number of Server resources requested by the application exceeds the maximum allowed number (10). Call the close() method to release these resources.

## 32390203 Duplicate Service Name

**Error Message**

Duplicate server name.

**Description**

This error code is reported if a service with the same name is registered repeatedly.

**Possible Causes**

The name of the service being created already exists.

**Solution**

Check whether a service with the same name already exists. If yes, register the service with a different name.

## 32390204 Number of Connections Exceeding the Limit

**Error Message**

The number of connections exceeds the limit.

**Description**

This error code is reported if the number of connections exceeds the limit.

**Possible Causes**

The number of requested connection resources exceeds 10.

**Solution**

The number of Connection resources requested by the application exceeds the maximum allowed number (10). Call the close() method to release these resources.

## 32390205 Connection Unavailable

**Error Message**

Connection is not ready.

**Description**

This error code is reported if a connection is unavailable.

**Possible Causes**

The client or server application attempts to perform an operation using a disconnected connection, for example, a connection state change caused by an abnormal interruption after the connection is established.

**Solution**

Check whether the connection is successfully established or disconnected, and perform the operation using a connection that is successfully established and not disconnected.

## 32390206 Invalid Parameter

**Error Message**

Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.

**Description**

Invalid parameter.

**Possible Causes**

1. A mandatory parameter is not passed.

2. The parameter type is incorrect.

3. The number of parameters is incorrect.

4. A parameter is left empty.

**Solution**

Check whether the required parameters are passed in and whether the types of the passed parameters are correct. If parameter validation fails, refer to the API reference and check the four possible causes above one by one.

## 32390300 Internal Error

**Error Message**

Internal error.

**Description**

An internal error occurs.

**Possible Causes**
1. Invalid input device ID.

2. Invalid input name.

3. Abnormal internal state.

4. Incorrect API usage.

5. System errors, such as null pointer, insufficient memory, unexpected distributed service restart, IPC exception, and JS engine exception.

**Solution**

View the error log to identify the error cause. Take appropriate based on the actual cause:

1. Check whether the deviceId passed in is the same as that obtained from the Bluetooth system API, and check whether the peer device is broadcasting.

2. If the name passed from the client to the server is the same as that passed from the server to the client, check whether the name is correct by referring to the API reference.

3. Check whether objects are used after being closed.

4. Check whether the API is correctly used by referring to the API reference.

5. If the problem persists, restart or update the application or upgrade the device version.