# @ohos.usbManager.serial(Serial Port Management)

This module provides APIs for managing the access and communication of serial port devices. It provides functions such as opening and closing devices, reading and writing data, setting parameters, and managing permissions. It addresses issues such as permission request, device configuration, and data transfer during communication between apps and serial port devices. This module simplifies the process of accessing serial port devices and improves development efficiency.

**Process**![SerialManager](../../../reference/figures/SerialManager.png)

**Use scenarios**

- **Embedded device communication**: exchanges data with various embedded devices, such as sensor data  
collection and device status monitoring.  
- **Industrial device debugging**: connects to industrial control devices to perform debugging operations  
such as parameter configuration, command delivery, and log output.  
- **Data exchange with serial port peripherals**: communicates with serial port peripherals, such as  
printers, scanners, and modems, for data transmission and reception.

**Since:** 19

**System capability:** SystemCapability.USB.USBManager.Serial

## Modules to Import

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [cancelSerialRight](arkts-basicservices-serialmanager-cancelserialright-f.md) | Cancels the permission to access the serial port device when the application is running. This API is used to close the enabled serial port device. Generally, this API is called to proactively release the permission, access another device, or for security purposes. |
| [close](arkts-basicservices-serialmanager-close-f.md) | Closes the serial port device. Call [requestSerialRight](arkts-basicservices-serialmanager-requestserialright-f.md) to request the permission and then call [open](arkts-basicservices-serialmanager-open-f.md) to open the serial port. Generally, this API is called when the application exits, the device is disconnected, or serial port resources need to be released. Closing the serial port does not remove the access permission. To remove the permission, call **cancelSerialRight**. |
| [getAttribute](arkts-basicservices-serialmanager-getattribute-f.md) | Obtains the configuration parameters of a specified serial port. You need to call [open](arkts-basicservices-serialmanager-open-f.md) to open the serial port to obtain the configuration. Generally, this API is called to check the current communication parameter configuration and debug serial port communication issues after the device is initialized. |
| [getPortList](arkts-basicservices-serialmanager-getportlist-f.md) | Obtains the serial port device list, including the device name and port number. Generally, this API is called when the application is started, a device is connected, or available serial port devices need to be detected. |
| [hasSerialRight](arkts-basicservices-serialmanager-hasserialright-f.md) | Checks whether the app has the permission to access the serial port device. When an app is restarted after exiting, permission needs to be requested again. Generally, this API is called to check the permission status before a serial port device is opened or a serial port operation is performed. |
| [open](arkts-basicservices-serialmanager-open-f.md) | Opens a serial port device. Before calling this API, you need to call [requestSerialRight](arkts-basicservices-serialmanager-requestserialright-f.md) to request the permission. After calling this API, you need to call [close](arkts-basicservices-serialmanager-close-f.md) to close the serial port. After the API is successfully called, you can perform operations such as read/write and parameter configuration on the serial port. |
| [read](arkts-basicservices-serialmanager-read-f.md) | Reads data from the serial port device asynchronously. The read data is stored in the **buffer** parameter. Before calling this API, call [open](arkts-basicservices-serialmanager-open-f.md) to open the serial port device first. This API uses a promise to return the length of the data that is actually read. This API can be used to receive data reported by sensors, read response data returned by devices, and receive device status information. |
| [readSync](arkts-basicservices-serialmanager-readsync-f.md) | Reads data from the serial port device synchronously. The read data is stored in the **buffer** parameter. The actual length of the data read is returned. Before calling this API, call [open](arkts-basicservices-serialmanager-open-f.md) to open the serial port device first. This method is applicable to simple communication scenarios where data needs to be read in blocking mode, the read sequence must be strictly followed, or there is no high requirement on real-time performance. |
| [requestSerialRight](arkts-basicservices-serialmanager-requestserialright-f.md) | Requests the permission for the app to access the serial port device. After the app exits, the access permission on the serial port device is automatically removed. After the app is restarted, the app needs to request the permission again. This API uses a promise to return the result. Generally, this API is called to request authorization from the user when the application attempts to access the serial port for the first time and detects that it does not have the permission. You can call [cancelSerialRight](arkts-basicservices-serialmanager-cancelserialright-f.md) to remove the permission. |
| [setAttribute](arkts-basicservices-serialmanager-setattribute-f.md) | Sets the parameters of the specified serial port. You need to call [open](arkts-basicservices-serialmanager-open-f.md) to open the serial port to set parameters. The configuration parameters include **baudRate** (mandatory), **dataBits** (optional) whose default value is **8**, **parity** (optional) whose default value is **PARITY_NONE**, and **stopBits** (optional) whose default value is 1. Generally, this API is called when the device is initialized, the communication protocol is switched, or the device requires non-default configuration parameters. |
| [write](arkts-basicservices-serialmanager-write-f.md) | Writes data to the serial port device asynchronously. Before calling this API, call [open](arkts-basicservices-serialmanager-open-f.md) to open the serial port first. The length of data written each time cannot exceed 4 KB; otherwise, data loss may occur. You are advised to write long data in multiple packets. This API uses a promise to return the result. This API is applicable to scenarios such as sending control commands to devices, delivering configuration parameters, and transferring the collected data. |
| [writeSync](arkts-basicservices-serialmanager-writesync-f.md) | Writes data to the serial port device synchronously. Before calling this API, call [open](arkts-basicservices-serialmanager-open-f.md) to open the serial port device first. The length of data written each time cannot exceed 4 KB. Otherwise, data loss may occur. You are advised to write long data in multiple packets. This API is applicable to scenarios where data needs to be written in blocking mode, important commands need to be sent, or the write sequence must be strictly followed. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addSerialRight](arkts-basicservices-serialmanager-addserialright-f-sys.md) | Adds the permission to an app for accessing the serial port device. Before using this method, you need to call [getPortList](arkts-basicservices-serialmanager-getportlist-f.md) to obtain the serial port list and obtain a valid port ID from the list. If the call is successful, the app obtains the permission to access the specified serial port device and can perform operations such as opening, reading data, and writing data. If the call fails, an error code is returned, and the app cannot access the serial port device. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [SerialAttribute](arkts-basicservices-serialmanager-serialattribute-i.md) | Represents the configuration parameters of a serial port. |
| [SerialPort](arkts-basicservices-serialmanager-serialport-i.md) | Represents the parameters of a serial port. |

### Enums

| Name | Description |
| --- | --- |
| [BaudRates](arkts-basicservices-serialmanager-baudrates-e.md) | Enumerates the baud rates, in bit/s. |
| [DataBits](arkts-basicservices-serialmanager-databits-e.md) | Enumerates the number of data bits, in bits. |
| [Parity](arkts-basicservices-serialmanager-parity-e.md) | Enumerates the parity check modes. |
| [StopBits](arkts-basicservices-serialmanager-stopbits-e.md) | Enumerates the number of stop bits, in bits. |
