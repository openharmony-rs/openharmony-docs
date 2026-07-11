# Serial Port Management Error Codes

<!--Kit: Basic Services Kit-->
<!--Subsystem: BusManager-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @hwymlgitcode-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

> **NOTE**
> 
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 35700001 Abnormal Service

**Error Message**

Service error.

**Description**

An internal error occurs in the serial port communication service when a serial port communication API is called.

**Possible Causes**

1. The serial port communication service is not started.

2. An internal error occurs in the serial port communication service.

**Solution**

1. Check whether the serial port function of the device is normal.

2. Restart the device and try again.

## 35700002 Parameter Error

**Error Message**

Invalid parameter.

**Description**

The input parameter is invalid when the serial port communication API is called.

**Possible Causes**

1. The baud rate is not a positive integer.

2. The length of the written data is out of range.

3. The timeout interval is out of the range.

4. The parameter type is incorrect.

**Solution**

1. Check whether the baud rate is a positive integer.

2. Check whether the length of the written data is within the range of (0, 4096].

3. Check whether the timeout interval is within the range of [0, 300000].

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

1. Check whether the USB-to-serial port cable is properly connected.

2. Remove and insert the USB device, call [getSerialPortList](js-apis-busmanager-serial.md#serialgetserialportlist) to obtain the device list, and then call [open](js-apis-busmanager-serial.md#open) to open the device.

## 35700004 Port in Use

**Error Message**

Port already in use.

**Description**

When the [open](js-apis-busmanager-serial.md#open) API is called to open a serial port, the serial port has been occupied by another application or process.

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

**Possible Causes**

1. The [open](js-apis-busmanager-serial.md#open) API is not called to open the serial port.

2. The serial port has been closed.

**Solution**

1. Call the [open](js-apis-busmanager-serial.md#open) API to open the serial port.

2. Check whether the serial port is closed. If so, open it again.

## 35700006 Transmission Timeout

**Error Message**

Transmission timeout.

**Description**

Data transmission times out when the [write](js-apis-busmanager-serial.md#write) API is called to write data.

**Possible Causes**

1. Data fails to be written to the serial port within the specified period.

2. The receiving device does not respond.

3. The serial port communication parameters do not match.

4. Data cannot be sent in time due to frequent write requests and congestion of the send buffer.

**Solution**

1. Check whether the receiving device is properly connected.

2. Increase the timeout interval.

3. Check whether the serial port communication parameters (such as the baud rate) are consistent with those of the peer end.

4. Reduce the write frequency or call the [drain](js-apis-busmanager-serial.md#drain) API between writes to wait until the previous data transmission is complete before sending new data.

## 35700007 User Authorization Rejected

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

The current application does not display a pop-up window for serial port authorization, so it does not have the permission to call the **serial.addPortAuthorization** API.

**Possible Causes**

1. The caller is not an application that displays a pop-up window for serial port authorization. The **serial.addPortAuthorization** API can be called only by applications that display a pop-up window for serial port authorization.

**Solution**

1. Check whether the current application is an application that displays a pop-up window for serial port authorization. This API can be called only by applications that display a pop-up window for serial port authorization.
