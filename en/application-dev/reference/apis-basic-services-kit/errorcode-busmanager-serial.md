# Serial Port Management Error Codes

<!--Kit: Basic Services Kit-->
<!--Subsystem: BusManager-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @hwymlgitcode-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=56506b565e102af3594819f598d20151e20779d3 translatedAt=2026-11-10T03:59:31.950Z pushedAt=2026-11-10T06:04:46.552Z nl=1 -->

> **NOTE**
> The parameter descriptions in the API reference are consistent with the comments in the @ohos.busManager.serial.d.ts file in the SDK.
>
> The initial APIs of this module are supported since API version 19. Newly added APIs in later versions are marked with a superscript to indicate their initial API version.
>
> This document provides error code descriptions for serial communication API calls, helping developers quickly locate and resolve serial communication issues. It applies to scenarios such as developing serial communication applications and debugging serial communication exceptions. Only the error codes specific to this module are described below. For general error codes, see [Universal Error Codes](../errorcode-universal.md).

## Error Code Summary
| ID | Error Message | Triggering Interface |
| --- | --- | --- |
| 35700001 | Service error. | getSerialPortList, open, close, write, onDataRead, offDataRead, flush, drain, setRts, getCts, getDsr, sendBrk, onDisconnect, offDisconnect, setDtr, addPortAuthorization |
| 35700002 | Invalid parameter. | open, write, addPortAuthorization |
| 35700003 | Virtual serial port disconnected. |open, write, onDataRead, flush, drain, setRts, getCts, sendBrk, getDsr, setDtr |
| 35700004 | Port already in use. | open |
| 35700005 | Port not open. | close, write, onDataRead, offDataRead, flush, drain, setRts, getCts, sendBrk, getDsr, setDtr, onDisconnect, offDisconnect |
| 35700006 | Transmission timeout. | write |
| 35700007 | User authorization required. | open |
| 35700008 | Permission denied. | addPortAuthorization |

## 35700001 Abnormal Service

**Error Message**

Service error.

**Description**

An internal exception (such as a service crash or insufficient resources) occurs in the serial port communication service when a serial communication-related interface is called.

**Possible Causes**

1. The serial port communication service is not started.

2. The serial port communication service process crashes or system resources are insufficient.

**Solution**

1. Check whether the serial port function of the device is normal.

2. Restart the device and try again.

## 35700002 Parameter Error

**Error Message**

Invalid parameter.

**Description**

The input parameter is invalid when the serial port communication API is called.

**Possible Causes**

1. The baud rate is not within the supported range (a common baud rate such as 9600/19200/38400/57600/115200, or a positive integer in the range [1, 115200], in baud).

2. The length of the data to be written exceeds the range (0, 4096] (in bytes).

3. The timeout exceeds the range [0, 300000] (in ms).

4. The parameter type does not match the interface definition, for example, a string is passed when a number is expected.

**Solution**

1. Check whether the baud rate is a supported common baud rate (such as 9600/19200/38400/57600/115200) or a positive integer in the range [1, 115200], in baud.

2. Check whether the length of the data to be written is within the range (0, 4096] (in bytes).

3. Check whether the timeout parameter is within the range [0, 300000] (unit: ms).

4. Check whether the parameter types are correct.

## 35700003 Virtual Serial Port Disconnected

**Error Message**

Virtual serial port disconnected.

**Description**

When a serial port communication API is called, the USB virtual serial port device is disconnected.

**Possible Causes**

1. The USB-to-serial port cable is removed.

2. The USB virtual serial port is disconnected abnormally.

**Solution**

1. Check whether the USB-to-serial cable is properly connected and ensure that the device connection is stable.

2. After re-plugging the USB device, call [getSerialPortList](js-apis-busmanager-serial.md#serialgetserialportlist) again to obtain the device list, and then call [open](js-apis-busmanager-serial.md#open) to open the device, so as to restore the serial communication function.

## 35700004 Port in Use

**Error Message**

Port already in use.

**Description**

When calling [open](js-apis-busmanager-serial.md#open) to open a serial port, ensure that the serial port is not occupied by other applications or processes. Otherwise, an error is reported because the port is already in use.

**Paired call description**
- After open() is called to open the serial port, close() must be called to close the serial port and release resources after use.
- If the serial port is not closed properly, the port may remain occupied, affecting subsequent use.
- It is recommended that close() be called in a finally block to ensure resource release.

**Possible Causes**

1. The same serial port is opened by another application.

2. The serial port is not properly disabled in the previous operation.

**Solution**

1. Close other applications that occupy the serial port.

2. Call [close](js-apis-busmanager-serial.md#close) to close the serial port and then open it again.

## 35700005 Port Not Opened

**Error Message**

Port not open.

**Description**

The serial port is not opened when a serial port communication API is called.

**State transition description**
- After open() is called, the serial port is in the open state, and APIs such as [onDataRead](js-apis-busmanager-serial.md#ondataread) and [write](js-apis-busmanager-serial.md#write) can be called. onDataRead must be called in pair with offDataRead, and onDisconnect must be called in pair with offDisconnect. Before close() is called, offDataRead and offDisconnect should be called first to cancel the subscription.
- After close() is called, the serial port is in the closed state, and the preceding interfaces cannot be used.
- Read and write operations can be performed only when the serial port is in the open state.

**Possible Causes**

1. The [open](js-apis-busmanager-serial.md#open) interface is not called to open the serial port.

2. The serial port has been closed.

**Solution**

1. Call the [open](js-apis-busmanager-serial.md#open) interface to open the serial port first.

2. Check whether the serial port is closed. If so, open it again.

## 35700006 Transmission Timeout

**Error Message**

Transmission timeout.

**Description**

When the [write](js-apis-busmanager-serial.md#write) interface is called to write data (ensure that the serial port is open), this error is reported if data transmission times out.

**Prerequisites**
- The [open](js-apis-busmanager-serial.md#open) interface must be called to open the serial port before the write() interface can be called.
- The write() interface depends on the serial port being in the open state.

**Possible Causes**

1. The waiting time of the write operation exceeds the configured timeout limit.

2. The receiving device does not respond.

3. The serial port communication parameters do not match.

4. Write requests are too frequent, causing congestion in the hardware buffer.

**Solution**

1. Check whether the receiving device is properly connected.

2. Increase the timeout parameter appropriately (unit: ms).

3. Check whether the serial port communication parameters (such as the baud rate) are consistent with those of the peer end.

4. When the serial port is open, reduce the write frequency or call the [drain](js-apis-busmanager-serial.md#drain) API between writes to wait until the previous data is sent before sending more data, so as to avoid congestion of the hardware buffer.

**Using write and drain together**
- drain() waits until all data in the serial port transmit buffer has been sent.
- When writing a large amount of data continuously, call drain() between write() calls to ensure that data is sent completely and in order.
- Typical call flow: write() → drain() → write() → drain() → ...

## 35700007 User Authorization Required

**Error Message**

User authorization required.

**Description**

When the [open](js-apis-busmanager-serial.md#open) API is called to open a serial port, the system checks whether the user has authorized the application to access the target serial port. If not, this error code is returned.

**Possible Causes**

1. The user rejects the application's request to access the target serial port in the authorization dialog box.

**Solution**

1. Instruct the user to allow the application to access the target serial port in the authorization dialog box.

## 35700008 Permission Denied

**Error Message**

Permission denied.

**Description**

When the serial.addPortAuthorization API is called, this API can be called only by the serial port authorization pop-up application (a preset application designated by the system to handle serial port device authorization pop-ups). If the current application is not the serial port authorization pop-up application, a permission denied error is reported.

**Possible Causes**

1. The caller is not an application that displays a pop-up window for serial port authorization. The **serial.addPortAuthorization** API can be called only by applications that display a pop-up window for serial port authorization.

**Solution**

1. Check whether the current application is an application that displays a pop-up window for serial port authorization. This API can be called only by applications that display a pop-up window for serial port authorization.
