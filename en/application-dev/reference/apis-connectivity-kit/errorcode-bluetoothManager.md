# Bluetooth Error Codes

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=b624ad84978226f7613c417ef899bd55e420e452 translatedAt=2026-10-29T12:21:45.502Z pushedAt=2026-10-30T07:26:21.060Z nl=1 -->

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

Bluetooth is manually disabled by the user, or the Bluetooth service is automatically disabled due to a system exception.

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

Check the number of paired devices. If the number exceeds the threshold, disconnect some connected devices and try again.

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

Turn on Bluetooth again to start the pairing process, and then call the related API.

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

Call the corresponding resource release API to release resources. For example, call the API for stopping scanning or disconnect the established connection, and try again.

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

The user does not complete the preprocessing operation within the specified timeout period. As a result, the preprocessing operation times out.

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

## 2900015 Parameter Format Inconsistent with Specifications

**Error Message**

Parameter format mismatch with specification.

**Description**

The parameter format is inconsistent with the specifications.

**Possible Causes**

For example, the parameter length does not meet the specifications, or lowercase letters are passed for a parameter that should use uppercase letters.

**Solution**

Check whether the parameter format complies with the specifications.

## 2900016 Device Not Paired

**Error Message**

Device unpaired.

**Description**

The device is not paired.

**Possible Causes**

The queried address is not paired with the device.

**Solution**

On the Bluetooth settings screen, check whether the device is paired.

<!--Del-->
## 2900017 No BLE Address Associated with the Input BR Address

**Error Message**

No BLE address is associated with the input BR address.

**Description**

When **connection.getBleMacByBrMac** is called to query the BLE address based on the BR address of the paired peer device, the input BR address is not associated with any BLE address.

**Possible Causes**

1. The peer device corresponding to the BR address does not support BLE (not a dual-mode device).
2. The system has not recorded the BLE address of the peer device.

**Solution**

1. Confirm that the actual BR address of the paired peer device is input.
2. Confirm that the peer device is a dual-mode device that supports BLE.<!--DelEnd-->

## 2900099

Different error messages are reported depending on the actual cause of the error, as described below.

### Operation Failed
**Error Message**

Operation failed.

**Description**

The operation failed. An internal system error occurred, such as an SA or IPC exception.

**Possible Causes**

Common error code for Bluetooth API calling failures. The possible causes are as follows:
1. The prerequisites for calling the API are not met.
2. The specified virtual address does not exist.

**Solution**

Check the prerequisites for calling the API.

### Invalid Parameter
**Error Message**

Operation failed. Invalid parameter.

**Description**

The input parameter is invalid.

**Possible Causes**

The function input parameter is not within the valid range.

**Solution**

Check whether the parameters passed in the API call comply with the interface description or protocol specification.

### GATT Characteristic Is Null
**Error Message**

Operation failed. GATT character is nullptr.

**Description**

The Generic Attribute Profile ([GATT](../../connectivity/bluetooth/terminology.md#gatt)) characteristic is null.

**Possible Causes**

The characteristic value is null.

**Solution**

Check the input parameters passed to the API.

### API Called Before the Previous Call Is Complete
**Error Message**

Operation failed. Please call the interface only after the previous callback has been completed.

**Description**

Call this API after the previous API callback is complete.

**Possible Causes**

The callback of the previous API is not complete.

**Solution**

Wait until the previous API callback is complete.

### Peer Device Not Discovered or Recorded
**Error Message**

Operation failed. Address has not been discovered or recorded.

**Description**

The device has not been discovered or recorded.

**Possible Causes**

The paired peer device has not been discovered or recorded.

**Solution**

Pair a peer device that has been discovered or recorded.

### Bluetooth Enabled
**Error Message**

Operation failed. Bluetooth switch state is turn on.

**Description**

Bluetooth is enabled.

**Possible Causes**

Bluetooth is enabled.

**Solution**

Check the Bluetooth status. If the status is correct, try again.

### Bluetooth Status Being Switched
**Error Message**

Operation failed. Bluetooth switch state is turning state.

**Description**

The Bluetooth status is being switched.

**Possible Causes**

The Bluetooth status is being switched.

**Solution**

Wait until the Bluetooth status switch is complete, and try again.

### Bluetooth Restricted
**Error Message**

Operation failed. In restrict bluetooth state.

**Description**

Bluetooth is in the restricted state.

**Possible Causes**

Bluetooth is in the restricted state.

**Solution**

Wait until Bluetooth exits the restricted state, and try again.

### Linking Cloud Device
**Error Message**

Operation failed. Cloud device is bonding.

**Description**

The cloud device is being linked.

**Possible Causes**

The cloud device is being linked.

**Solution**

Wait until the cloud device is linked, and try again.

### Device Being Discovered or Discovered
**Error Message**

Operation failed. In DISCOVERYING or DISCOVERY_STARTED state.

**Description**

The device is being discovered or has been discovered.

**Possible Causes**

The device is being discovered or has been discovered.

**Solution**

Do not initiate Bluetooth scanning repeatedly.

### Failed to Start Scanning Due to Insufficient Hardware Resources
**Error Message**

Operation failed. Fails to start scan as it is out of hardware resources.

**Description**

Starting a scan fails due to insufficient hardware resources.

**Possible Causes**

An excessive number of scan channels have been activated by this application or other applications, resulting in insufficient hardware resources.

**Solution**

1. If this application has never started a scan, you can turn Bluetooth off and then back on to release the scanning resources occupied by other applications.
2. If this application has already started a scan on another channel, you can call the **stopScan** API to halt the scan. After the hardware resources are released, restart the current scan.

### GATT Disconnected
**Error Message**

Operation failed. GATT not in connected state.

**Description**

The GATT is not connected.

**Possible Causes**

This error code is reported if the GATT connection is not established.

**Solution**

Connect to the GATT first, and try again.

### Connections Not Allowed During Service Scanning
**Error Message**

Operation failed. Not allowed to connect during scanning.

**Description**

Connections are not allowed during scanning.

**Possible Causes**

Connections are not allowed during service scanning.

**Solution**

Complete the service scanning and then initiate a connection.

### Invalid Bluetooth Address or Transmission Type
**Error Message**

Operation failed. Invalid bluetooth addr or transport type.

**Description**

The Bluetooth address or transmission type is invalid.

**Possible Causes**

The input parameter contains an invalid Bluetooth address or transmission type.

**Solution**

Check whether the input parameters meet the protocol requirements.

### IPC Data Transmission Failed
**Error Message**

Operation failed. IPC trans failed.

**Description**

IPC data transmission failed.

**Possible Causes**

Data transmission is abnormal.

**Solution**

Check the input data and try again.

### Maximum Connections Reached
**Error Message**

Operation failed. Max connections has reached.

**Description**

The maximum number of connections has been reached.

**Possible Causes**

The maximum number of connections has been reached.

**Solution**

Clear the connected devices and try to initiate a new connection.

### Device Connected
**Error Message**

Operation failed. This device has connected.

**Description**

The device is connected.

**Possible Causes**

The device is connected.

**Solution**

The device is connected. Do not repeat the operation.

### Device Not Connected
**Error Message**

Operation failed. This device isn't connected.

**Description**

The device is not connected.

**Possible Causes**

The device is not connected.

**Solution**

The device is not connected. The current operation is invalid. Connect the device first.

### Prepare Write Queue Full on the GATT Server
**Error Message**

Operation failed. The prepare write queue of GATT server is full.

**Description**

The prepare write queue on the GATT server is full.

**Possible Causes**

The prepare write queue on the GATT server is full, and the GATT client writes a large amount of data.

**Solution**

The GATT client writes a large amount of data. You are advised to write data in fragments.

### Incorrect Behavior of the Peer Device
**Error Message**

Operation failed. Remote device has an error.

**Description**

An error occurs on the peer device.

**Possible Causes**

The peer device has incorrect behavior.

**Solution**

Ensure that the peer device is used correctly, and try again.

### Battery Service Listener Not Registered
**Error Message**

Operation failed. Unregistered bas observer.

**Description**

The caller has not registered a battery service listener.

**Possible Causes**

The caller has not registered a battery service listener.

**Solution**

Ensure that a battery service listener is properly registered, and try again.

### Maximum Number of Battery Service Listeners Reached
**Error Message**

Operation failed. Bas observers exceeds the limit.

**Description**

The number of battery service listeners has reached the maximum.

**Possible Causes**

The number of battery service listeners has reached the maximum.

**Solution**

Cancel the listening of some services on the battery service and try again.

### Battery Service Request Busy
**Error Message**

Operation failed. Bas request busy.

**Description**

The battery service request is busy.

**Possible Causes**

The battery service request is busy.

**Solution**

Wait until the battery service finishes processing the current request before performing the operation.

The following are common cases when the BLE service returns error code 2900099.

### Failed to Call setCharacteristicChangeNotification – No Descriptor Write Listener Created on the Server

If error code 2900099 is returned when [setCharacteristicChangeNotification](js-apis-bluetooth-ble.md#setcharacteristicchangenotification) is called, locate the fault based on the following scenarios.

No [on('descriptorWrite')](js-apis-bluetooth-ble.md#ondescriptorwrite) listener is created on the server, and the **setCharacteristicChangeNotification** API on the client is blocked by continuous requests.

**Possible Causes**

No **on('descriptorWrite')** listener is created on the server, and descriptor requests from the client cannot be received.

**Solution**

Create an [on('descriptorWrite')](js-apis-bluetooth-ble.md#ondescriptorwrite) listener on the server.

### Failed to Call setCharacteristicChangeNotification – No Response from the Server in a Timely Manner

After receiving the descriptor request from the client, the server does not call the [sendResponse](js-apis-bluetooth-ble.md#sendresponse) API in a timely manner (check whether the log contains the keyword **OnSetNotifyCharacteristic**). The **setCharacteristicChangeNotification** API on the client is blocked due to continuous requests.

**Typical log information**

```text
bta gattc enqueue: already has a pending command
```

**Possible Causes**

The server does not call the **sendResponse** API in a timely manner after receiving the descriptor request from the client.

**Solution**

After receiving the descriptor request from the client, the server calls the [sendResponse](js-apis-bluetooth-ble.md#sendresponse) API to return data to the client in a timely manner.

### Failed to Call setCharacteristicChangeNotification – Previous Asynchronous API Call Not Completed

When the **setCharacteristicChangeNotification** API is called, another asynchronous API is still being called. As a result, the **setCharacteristicChangeNotification** API call is blocked. The troubleshooting method is as follows:

- Set log printing in the API callback to view the complete sequence of API calls. The sequence of calling APIs on the BLE client from object instance creation to data transmission is as follows:
  - Call [createGattClientDevice](js-apis-bluetooth-ble.md#blecreategattclientdevice) to create a client instance.
  - Create APIs for listening for the BLE connection status, MTU changes, and characteristic value changes.
  - Call the [connect](js-apis-bluetooth-ble.md#connect) API to connect to BLE.
  - Call [setBLEMtuSize](js-apis-bluetooth-ble.md#setblemtusize) to negotiate the MTU.
  - Call [getServices](js-apis-bluetooth-ble.md#getservices) to obtain all service capabilities supported by the server.
  - Call the **setCharacteristicChangeNotification** API to set the capability of notifying the server of characteristic value content changes.
  - Call [writeCharacteristicValue](js-apis-bluetooth-ble.md#writecharacteristicvalue) to write characteristic value data to the server.
- Check the system log output. After the issue is reproduced, generate a HiLog log and check the timestamps of the system log output when each API call starts and completes, so as to determine whether an API call is blocked. For example, when the **setCharacteristicChangeNotification** API call starts, the keyword **setCharacteristicChangeNotification** is printed in the system log. When the API call completes, you can determine the completion time based on the custom log in the callback of the **setCharacteristicChangeNotification** API.

**Possible Causes**

Before calling the **setCharacteristicChangeNotification** API, you generally call the **setBLEMtuSize** asynchronous API  to negotiate the MTU data transmission size with the server first, and then call **getServices** to obtain the characteristic service list of the server. If these previous asynchronous API calls are not completed, the **setCharacteristicChangeNotification** API call is blocked.

**Solution**

After the **setBLEMtuSize** and **getServices** APIs are called successfully in sequence, call **setCharacteristicChangeNotification** to set the capability of receiving notifications of characteristic content changes from the server. For the complete call sequence, see [GATT-based Connection and Data Transmission](../../connectivity/bluetooth/gatt-development-guide.md).

### Failure to Call writeCharacteristicValue - Previous API Call Incomplete

When data is written before the callback of the previous non-listening BLE API (**setBLEMtuSize**, **getServices**, and **setCharacteristicChangeNotification**) returns, error code 2900099 is reported, causing the data write to fail.

**Possible Causes**

The previous non-listening BLE API call is incomplete.

**Solution**

Ensure that the callbacks of other non-listening BLE APIs have been triggered and completed before calling [writeCharacteristicValue](js-apis-bluetooth-ble.md#writecharacteristicvalue) to write data.

### API Call Failed After GATT Device Reconnection - gattClient Object Not Destroyed in Time

Each time a GATT device is reconnected, a new **gattClient** object is created and a new GATT connection is established. After each connection is closed, the [close](js-apis-bluetooth-ble.md#close) API is not called in time to destroy the **gattClient** instance.

**Possible Causes**

The **gattClient** instance is not destroyed in time, causing **setCharacteristicChangeNotification** and **getServices** to be called repeatedly on each reconnection, resulting in a busy state and consequently error 2900099.

**Solution**

After each connection is closed, call the [close](js-apis-bluetooth-ble.md#close) API to destroy the **gattClient** object in a timely manner.

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

This error code is reported if characteristic or descriptor read and write operations requiring authentication are performed when the GATT connection is not authenticated. Whether authentication is required for the operation is subject to the permission of the characteristic or descriptor on the server.

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

## 2901008

**Error Message**

GATT service is not found.

**Description**

The GATT service does not exist. Before obtaining the specified GATT service, ensure that the service has been added.

**Possible Causes**

The GATT service has not been added.

**Solution**

Call [addService](js-apis-bluetooth-ble.md#addservice) to add the service.

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

BLE scanning has been enabled by the application.

**Solution**

Check whether scanning has been enabled. If so, call the API for stopping the scan to stop the current scan, and then start the scan again.

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

## 2903050 HID Is Not in the Foreground

**Error Message**

HID application is not in the foreground.

**Description**

The application that registers the HID device is not in the foreground.

**Possible Causes**

The application that registers the HID device is in the background.

**Solution**

Check whether the application that registers the HID device is in the foreground.

## 2903051 HID Has Been Registered

**Error Message**

Another HID application has been registered.

**Description**

The HID device has been registered by another application.

**Possible Causes**

Only one application can register the HID device.

**Solution**

Check whether the HID device has been registered by another application.

## 2903052 HID Not Registered

**Error Message**

HID application does not register.

**Description**

The application has not registered the HID device.

**Possible Causes**

An application can connect to and exchange data with the HID host only after registering the HID device.

**Solution**

Check whether the application successfully registers the HID device.

## 2903053 HID Not Connected

**Error Message**

HID device is not connected.

**Description**

The HID device has not connected to the HID host.

**Possible Causes**

The HID device can exchange data with the HID host only after the connection is successful.

**Solution**

Check whether the application successfully registers the HID device and connects to the HID host.

