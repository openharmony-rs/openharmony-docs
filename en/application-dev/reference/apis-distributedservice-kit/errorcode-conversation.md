# Cross-Device Wakeup and Message Transfer Error Codes
<!--Kit: Distributed Service Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wangrui7-->
<!--Designer: @yangyang2-->
<!--Tester: @Ytt-test-->
<!--Adviser: @hu-zhiqiong-->
> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 2000001 Internal Error

**Error Message**

Internal error.

**Description**

An internal error occurs in the API.

**Possible Causes**

An internal error occurs.

**Solution**

Restart the device and try again.

## 2004001 Unsupported Peer Version

**Error Message**

Remote not supported.

**Description**

The peer version is not supported.

**Possible Causes**

This function is not supported because the peer version is outdated.

**Solution**

Update the peer version and try again.

## 2004002 Duplicate Calls

**Error Message**

Duplicate calls, previous call still in progress.

**Description**

The API is called when the previous request is still being processed. Wait until the previous call is complete and try again.

**Possible Causes**

The previous request has not been processed yet.

**Solution**

Wait until the previous call is complete and try again.

## 2004003 Failure to Send Data

**Error Message**

Send data failed.

**Description**

This error code is reported if data fails to be sent.

**Possible Causes**

The network is not connected, or the network connection is poor.

**Solution**

Connect to the network or connect to another network and try again.

## 2004004 Request Timeout

**Error Message**

Wait remote ack timeout.

**Description**

Waiting for a response from the peer end times out.

**Possible Causes**

The peer end is not connected to the network or is powered off.

**Solution**

Ensure that the Internet connection of the peer end is normal and try again.
