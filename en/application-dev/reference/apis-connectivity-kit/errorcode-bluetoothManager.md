# Bluetooth Error Codes

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 2900001

**Error Message**

Service stopped.

**Description**

The Bluetooth service is stopped, and the APIs related to the Bluetooth service cannot be called.

**Possible Causes**

The Bluetooth service fails to start.

**Solution**

Start the Bluetooth service.

## 2900003

**Error Message**

Bluetooth disabled.

**Description**

Bluetooth is disabled.

**Possible Causes**

Bluetooth is disabled.

**Solution**

Enable Bluetooth.

## 2900004

**Error Message**

Profile not supported.

**Description**

The profile is not supported.

**Possible Causes**

The profile is not supported by the device.

**Solution**

Check whether the device supports the profile. Use a profile supported by the device.

## 2900005

**Error Message**

Device not connected.

**Description**

The device is not connected to Bluetooth.

**Possible Causes**

The device pairing fails.

**Solution**

Turn on Bluetooth again to start the pairing process.

## 2900006

**Error Message**

The maximum number of connections has been reached.

**Description**

The number of connections reaches the maximum.

**Possible Causes**

The number of connections reaches the limit.

**Solution**

Check whether the number of paired devices exceeds the threshold.

## 2900007

**Error Message**

Asynchronous interface invoking timeout.

**Description**

The asynchronous call timed out.

**Possible Causes**

The remote device does not respond.

**Solution**

Try again after the timeout. If the local and remote devices are connected, disconnect them and try again.

## 2900008

**Error Message**

The value of proxy is a null pointer.

**Description**

**pimpl** or **proxy** is null.

**Possible Causes**

The device pairing fails.

**Solution**

Turn on Bluetooth again to start the pairing process.

## 2900009

**Error Message**

Fails to start scan as it is out of hardware resources.

**Description**

Starting a scan fails due to insufficient hardware resources.

**Possible Causes**

An excessive number of scan channels have been activated by this application or other applications, resulting in insufficient hardware resources.

**Solution**

If this application has never started a scan, you can turn Bluetooth off and then back on to release the scanning resources occupied by other applications.
If this application has already started a scan on another channel, you can call the **stopScan** API to halt the scan. After the hardware resources are released, restart the current scan.

## 2900010

**Error Message**

Resources have reached the upper limit.

**Description**

This error code is reported if resource usage reaches the upper limit.

**Possible Causes**

The application applies for too many resources.

**Solution**

Call the corresponding API to release resources.

## 2900011

**Error Message**

The operation is busy. The last operation is not complete.

**Description**

This error code is reported if the previous operation is not complete.

**Possible Causes**

The current operation is executed before the previous operation is complete. For example, the [readCharacteristicValue](js-apis-bluetooth-ble.md#readcharacteristicvalue) API is called when the current API call is still in progress.
Other involved APIs are [writeCharacteristicValue](js-apis-bluetooth-ble.md#writecharacteristicvalue), [readDescriptorValue](js-apis-bluetooth-ble.md#readdescriptorvalue), [writeDescriptorValue](js-apis-bluetooth-ble.md#writedescriptorvalue), [getRssiValue](js-apis-bluetooth-ble.md#getrssivalue), [setCharacteristicChangeNotification](js-apis-bluetooth-ble.md#setcharacteristicchangenotification) and [setCharacteristicChangeIndication](js-apis-bluetooth-ble.md#setcharacteristicchangeindication). A new API call will be blocked if the current API call is not yet complete.

**Solution**

A new call of an asynchronous API is permitted only after the callback or promise of the previous API call is received.

## 2900013

**Error Message**

The user does not respond.

**Description**

This error code is reported if the user does not respond to the preprocessing operation.

**Possible Causes**

The user does not perform the required operation within a specified period of time. As a result, the preprocessing operation times out.

**Solution**

Perform the preprocessing operation again.

## 2900014

**Error Message**

User refuse the action.

**Description**

This error code is reported if the user rejects the preprocessing operation.

**Possible Causes**

The user rejects the preprocessing operation.

**Solution**

Perform the preprocessing operation again.

## 2900099

**Error Message**

Operation failed.

**Description**

The operation failed.

**Possible Causes**

The profile is not supported by the device.

**Solution**

Perform this operation again.

## 2900100

**Error Message**

IPC failed.

**Description**

IPC data transmission fails.

**Possible Causes**

The input data is incorrect.

**Solution**

Check the input data.

## 2901000

**Error Message**

Read forbidden.

**Description**

The read operation is not allowed.

**Possible Causes**

The caller does not have the read permission.

**Solution**

Check whether the caller has the read permission.

## 2901001

**Error Message**

Write forbidden.

**Description**

The write operation is not allowed.

**Possible Causes**

The caller does not have the write permission.

**Solution**

Check whether the caller has the write permission.

## 2901003

**Error Message**

The connection is not established.

**Description**

This error code is reported if the GATT connection is not established.

**Possible Causes**

An API call is invoked when the GATT connection is not established, for example, [getServices](js-apis-bluetooth-ble.md#getservices) or [readCharacteristicValue](js-apis-bluetooth-ble.md#readcharacteristicvalue) is called.

**Solution**

Ensure that the GATT connection is established.

## 2901004

**Error Message**

The connection is congested.

**Description**

This error code is reported if the GATT connection is congested.

**Possible Causes**

Characteristic or descriptor read and write operations are performed frequently, causing congestion in underlying data transmission. For example, if the [writeCharacteristicValue](js-apis-bluetooth-ble.md#writecharacteristicvalue) API is frequently called with [GattWriteType](js-apis-bluetooth-ble.md#gattwritetype) being set as **WRITE_NO_RESPONSE**, congestion may occur.

**Solution**

Reduce the frequency of read and write operations. If **GattWriteType** is set to **WRITE_NO_RESPONSE**, the recommended interval is greater than 50 ms.

## 2901005

**Error Message**

The connection is not encrypted.

**Description**

This error code is reported if characteristic or descriptor read and write operations requiring the encryption permission is performed when the GATT connection is not encrypted. Whether encryption is required for the operation is subject to the permission of the characteristic or descriptor on the server.

**Possible Causes**

The GATT encryption permission is not available.

**Solution**

Check whether the encryption permission is available for the GATT connection.

## 2901006

**Error Message**

The connection is not authenticated.

**Description**

This error code is reported if characteristic or descriptor read and write operations requiring authentication is performed when the GATT connection is not authenticated. Whether authentication is required for the operation is subject to the permission of the characteristic or descriptor on the server.

**Possible Causes**

The GATT connection is not authenticated.

**Solution**

Check whether the device is paired with the peer device and whether the GATT connection is authenticated.

## 2901007

**Error Message**

The connection is not authorized.

**Description**

This error code is reported if characteristic or descriptor read and write operations requiring authorization is performed when the GATT connection is not authorized. Whether authorization is required for the operation is subject to the permission of the characteristic or descriptor on the server.

**Possible Causes**

The GATT connection is not authorized.

**Solution**

Check whether the GATT connection is authorized.

## 2901054

**Error Message**

IO error.

**Description**

The I/O operation failed.

**Possible Causes**

The I/O transmission is abnormal.

**Solution**

Perform this operation again.

## 2902050

**Error Message**

Failed to start scan as Ble scan is already started by the app.

**Description**

This error code is reported if the attempt to enable scanning fails.

**Possible Causes**

BLE scanning has been enabled.

**Solution**

Check whether scanning is enabled.

## 2902054

**Error Message**

The length of the advertising data exceeds the upper limit.

**Description**

This error code is reported if the length of the advertising data exceeds the upper limit.

**Possible Causes**

The maximum length of traditional advertising packets is 31 bytes. If the maximum length is exceeded, an exception is returned. Currently, this length limit applies only to traditional advertising but not extended advertising.

**Solution**

Check whether the length of the advertising packet exceeds the upper limit.

## 2902055

**Error Message**

Invalid advertising id.

**Description**

This error code is reported if the advertising ID is invalid.

**Possible Causes**

The input advertising ID must be the value returned by [startAdvertising](js-apis-bluetooth-ble.md#blestartadvertising11). The invalid advertising ID is **0xFF** by default.

**Solution**

Check whether the input advertising ID is a valid advertising ID returned by [startAdvertising](js-apis-bluetooth-ble.md#blestartadvertising11).
