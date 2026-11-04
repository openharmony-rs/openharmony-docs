# Proxy Channel Management Error Codes
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @jzy_123-->
<!--Designer: @yangjun044-->
<!--Tester: @Ytt-test-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=94fc4a21f9702eb1ba2d07ab5a2331165601b011 translatedAt=2026-11-03T12:58:35.756Z pushedAt=2026-11-04T08:47:59.643Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 32390001 Bluetooth Disabled

**Error Message**

BR is disabled.

**Description**

This error code is reported if Bluetooth is disabled on the local device.

**Possible Causes**

Bluetooth is disabled on the local device.

**Solution**

Enable Bluetooth on the local device and try again.

## 32390002 Device Not Paired

**Error Message**

Device not paired.

**Description**

This error code is reported if the local device has not established a Bluetooth pairing.

**Possible Causes**

1. The local device has not established a Bluetooth pairing with the target device.

2. The target device has not started service listening.

3. An invalid MAC or UUID is used.

**Solution**

1. Use the Sports Health app to add and pair the device.

2. Check whether the Bluetooth service on the peer device has enabled listening for pairing requests.

3. Check the validity of the entered MAC and UUID. The MAC should be a Bluetooth MAC address string in the XX:XX:XX:XX:XX:XX format, and the UUID should be a standard UUID format string, such as xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx.

## 32390004 Invalid or Unavailable Channel ID

**Error Message**

ChannelId is invalid or unavailable.

**Description**

The channel ID passed when calling the proxy channel API does not meet the requirements or the channel has become invalid, causing the operation to fail.

**Possible Causes**

1. An invalid channelId is passed. The channelId should be the number-type channel identifier returned by openProxyChannel.

2. The channel corresponding to this channelId has been closed through closeProxyChannel, and the channelId is no longer available after closure.

**Solution**

1. Review the code logic to determine if **channelId** is the one returned by **openProxyChannel**.

2. Check the code logic to confirm whether the channel corresponding to this channelId has been closed. If it has been closed, do not continue to use this channelId. If communication needs to continue, call openProxyChannel again to establish a new channel.

## 32390006 Parameter Verification Error

**Error Message**

Parameter error.

**Description**

The parameters passed when calling the proxy channel API do not meet the requirements, such as an abnormal MAC or UUID format or an incorrect input parameter type, causing the API call to fail.

**Possible Causes**

1. The input MAC or UUID is in an invalid format. The MAC should be a Bluetooth MAC address string in the XX:XX:XX:XX:XX:XX format, and the UUID should be a standard UUID string, for example, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx.

2. The type of the input parameters is incorrect.

**Solution**

1. Check the code logic to ensure that the MAC is a Bluetooth MAC address string in the XX:XX:XX:XX:XX:XX format and the UUID is a standard UUID string, for example, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx.

2. Check the code logic to ensure that the input parameter types are consistent with the API definition.

## 32390100 Internal Error

**Error Message**

Internal error.

**Description**

An internal system exception occurs, which may cause the current operation to fail or the service to become unavailable.

**Possible Causes**

System errors, such as null pointer, insufficient memory, unexpected distributed service restart, IPC exception, and JS engine exception.

**Solution**

1. Retry the operation.

2. If the problem persists, restart the application.

3. If restarting does not work, upgrade the application or the device version.

## 32390101 Call Restricted

**Error Message**

Call is restricted.

**Description**

The call is unauthorized and restricted.

**Possible Causes**

The caller is not authorized to perform the operation.

**Solution**

Apply for the permission required for proxy channel management (confirm the specific permission name from the proxy channel management API reference), declare the corresponding permission in the application configuration, and try again.

## 32390102 Operation Failed or Connection Timed Out

**Error Message**

Operation failed or Connection timed out.

**Description**

A Bluetooth underlying fault causes the proxy channel operation to fail, or the connection times out because it is not established within the specified time.

**Possible Causes**

The underlying Bluetooth is faulty, leading to a connection failure or timeout.

**Solution**

1. Turn off and then turn on Bluetooth on the local device and the target device.

2. Restart the local device and the target device, and then enable Bluetooth on the devices.

## 32390103 Data Too Long

**Error Message**

Data too long.

**Description**

The length of the data sent through the proxy channel exceeds the maximum limit (4096 bytes), causing the sending to fail.

**Possible Causes**

The length of the data to be sent exceeds 4096 bytes.

**Solution**

Ensure that the length of the data to be sent does not exceed 4096 bytes. If the data is too long, send it in segments.

## 32390104 Data Sending Failed

**Error Message**

Send failed.

**Description**

When data is sent through the proxy channel, a Bluetooth fault prevents the data from being successfully delivered to the target device.

**Possible Causes**

The underlying Bluetooth connection is faulty or the protocol is abnormal.

**Solution**

1. Restart Bluetooth on the local device and the target device.

2. Restart the local device and the target device.