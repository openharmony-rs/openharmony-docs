# hid_ddk_api.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5a54ccb5a7574325a4204c5dd79658747dfa0872 translatedAt=2026-11-04T03:53:59.524Z pushedAt=2026-11-04T10:12:50.026Z nl=1 -->

## Overview

Declares the HID DDK (Driver Development Kit) APIs for accessing input devices on the host side. This module provides the capabilities of creating, opening, reading from, and writing to HID devices, and supports device management and event injection. It supports two usage modes: one is the creation of virtual HID devices and event injection, applicable to scenarios such as simulating keyboard, mouse, and touchscreen input; the other is the access to and communication with real HID devices, supporting opening devices, reading and writing device reports, and obtaining device information, applicable to scenarios of data interaction with HID devices.

**File to include**: <hid/hid_ddk_api.h>

**Library**: libhid.z.so

**System capability**: SystemCapability.Driver.HID.Extension

**Since**: 11

**Related module**: [HidDdk](capi-hidddk.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [int32_t OH_Hid_CreateDevice(Hid_Device *hidDevice, Hid_EventProperties *hidEventProperties)](#oh_hid_createdevice) | Creates a device. Applicable to scenarios where a virtual HID input device needs to be simulated, such as simulating input devices like a keyboard and mouse for automated testing. Must be used in pairs with [OH_Hid_DestroyDevice()](#oh_hid_destroydevice). |
| [int32_t OH_Hid_EmitEvent(int32_t deviceId, const Hid_EmitItem items[], uint16_t length)](#oh_hid_emitevent) | Sends an event list to a specified device. The events are injected into the system through the virtual device created by [OH_Hid_CreateDevice()](#oh_hid_createdevice), and the system processes them as real input events. Applicable to scenarios where user input events are simulated, such as simulating key presses, mouse movement, and clicks for automated testing or remote control. |
| [int32_t OH_Hid_DestroyDevice(int32_t deviceId)](#oh_hid_destroydevice) | Destroys a device. Must be used in pairs with [OH_Hid_CreateDevice()](#oh_hid_createdevice). Only the device created by the current caller can be destroyed. |
| [int32_t OH_Hid_Init(void)](#oh_hid_init) | Initializes the HID DDK. This method must be called before using any other HID DDK method. When no HID DDK feature is used anymore, [OH_Hid_Release()](#oh_hid_release) must be called to release resources. |
| [int32_t OH_Hid_Release(void)](#oh_hid_release) | Releases the HID DDK. Must be used in pairs with [OH_Hid_Init()](#oh_hid_init). |
| [int32_t OH_Hid_Open(uint64_t deviceId, uint8_t interfaceIndex, Hid_DeviceHandle **dev)](#oh_hid_open) | Opens the device specified by deviceId and interfaceIndex. After use, call [OH_Hid_Close()](#oh_hid_close) to release device resources. |
| [int32_t OH_Hid_Close(Hid_DeviceHandle **dev)](#oh_hid_close) | Closes a device. Must be used in pairs with [OH_Hid_Open()](#oh_hid_open). Applicable to resource scenarios where device resources are released when communication with the HID device is no longer needed. |
| [int32_t OH_Hid_Write(Hid_DeviceHandle *dev, uint8_t *data, uint32_t length, uint32_t *bytesWritten)](#oh_hid_write) | Writes an HID report to the device. |
| [int32_t OH_Hid_ReadTimeout(Hid_DeviceHandle *dev, uint8_t *data, uint32_t bufSize, int timeout, uint32_t *bytesRead)](#oh_hid_readtimeout) | Reads a report from the HID device within the specified timeout interval.|
| [int32_t OH_Hid_Read(Hid_DeviceHandle *dev, uint8_t *data, uint32_t bufSize, uint32_t *bytesRead)](#oh_hid_read) | Reads a report from the HID device. The blocking mode (that is, blocking remains active until data can be read) is used by default. You can call [OH_Hid_SetNonBlocking](capi-hid-ddk-api-h.md#oh_hid_setnonblocking) to change the mode.|
| [int32_t OH_Hid_SetNonBlocking(Hid_DeviceHandle *dev, int nonBlock)](#oh_hid_setnonblocking) | Sets the device read mode to non-blocking mode.|
| [int32_t OH_Hid_GetRawInfo(Hid_DeviceHandle *dev, Hid_RawDevInfo *rawDevInfo)](#oh_hid_getrawinfo) | Obtains the original device information.|
| [int32_t OH_Hid_GetRawName(Hid_DeviceHandle *dev, char *data, uint32_t bufSize)](#oh_hid_getrawname) | Obtains the original device name.|
| [int32_t OH_Hid_GetPhysicalAddress(Hid_DeviceHandle *dev, char *data, uint32_t bufSize)](#oh_hid_getphysicaladdress) | Obtains the physical address of the HID device.|
| [int32_t OH_Hid_GetRawUniqueId(Hid_DeviceHandle *dev, uint8_t *data, uint32_t bufSize)](#oh_hid_getrawuniqueid) | Obtains the original unique identifier of a device.|
| [int32_t OH_Hid_SendReport(Hid_DeviceHandle *dev, Hid_ReportType reportType, const uint8_t *data, uint32_t length)](#oh_hid_sendreport) | Sends an HID report of a specified type to the device. |
| [int32_t OH_Hid_GetReport(Hid_DeviceHandle *dev, Hid_ReportType reportType, uint8_t *data, uint32_t bufSize)](#oh_hid_getreport) | Obtains an HID report of a specified type from the device. |
| [int32_t OH_Hid_GetReportDescriptor(Hid_DeviceHandle *dev, uint8_t *buf, uint32_t bufSize, uint32_t *bytesRead)](#oh_hid_getreportdescriptor) | Obtains the report descriptor of the HID device.|

## Function Description

### OH_Hid_CreateDevice()

```c
int32_t OH_Hid_CreateDevice(Hid_Device *hidDevice, Hid_EventProperties *hidEventProperties)
```

**Description**

Creates a device. Applicable to scenarios where a virtual HID input device needs to be simulated, such as simulating input devices like a keyboard or mouse for automated testing. It must be used in pairs with [OH_Hid_DestroyDevice()](#oh_hid_destroydevice).

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 11


**Parameters**

| Name                                                                          | Description|
|-------------------------------------------------------------------------------| -- |
| [Hid_Device](capi-hidddk-hid-device.md) *hidDevice                            | Pointer to the basic information about the device to create, including the device name, vendor ID, and product ID.|
| [Hid_EventProperties](capi-hidddk-hid-eventproperties.md) *hidEventProperties | Pointer to the event properties related to the device to create, including the event type, key event properties, absolute coordinate event properties, and relative coordinate event properties.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | deviceID (a non-negative integer): ID of the successfully created device.<br>         Returns [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode) if permission verification fails. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         Returns [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode) if the connection to the HID DDK service fails. Possible cause: the DDK service is not initialized. Call OH_Hid_Init to complete initialization.<br>         Returns [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode) if parameter verification fails. Possible causes: 1. The input parameter hidDevice is a null pointer;<br>         2. The input parameter hidEventProperties is a null pointer; 3. The length of properties exceeds 7; 4. The length of hidEventTypes exceeds 5;<br>         5. The length of hidKeys exceeds 100; 6. The length of hidAbs exceeds 26; 7. The length of hidRelBits exceeds 13;<br>         8. The length of hidMiscellaneous exceeds 6.<br>         Returns [HID_DDK_FAILURE](capi-hid-ddk-types-h.md#hid_ddkerrcode) if the number of devices reaches the maximum of 200. |

### OH_Hid_EmitEvent()

```c
int32_t OH_Hid_EmitEvent(int32_t deviceId, const Hid_EmitItem items[], uint16_t length)
```

**Description**

Sends an event list to a specified device. The events are injected into the system through the virtual device created by [OH_Hid_CreateDevice()](#oh_hid_createdevice), and the system processes them as real input events. Applicable to scenarios of simulating user input events, such as simulating key presses, mouse movement, and clicks for automated testing or remote control.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| int32_t deviceId | Device ID. It must be a device created by the current caller through [OH_Hid_CreateDevice()](#oh_hid_createdevice), and its value is a non-negative number. |
| const [Hid_EmitItem](capi-hidddk-hid-emititem.md) items[] | List of events to send. An event includes the type (whose value comes from the event type Hid_EventType), code (whose value comes from the synchronization event code Hid_SynEvent, key code Hid_KeyCode, absolute axis code Hid_AbsAxes, relative axis code Hid_RelAxes, or other input event code Hid_MscEvent), and value (determined by the actual device input). The sent events are injected into the specified device to simulate the corresponding input behavior of the device. |
| uint16_t length | Length of the event list to send (number of events sent at a time). The value range is [1, 7]. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode) Returns HID_DDK_SUCCESS if the API is called successfully.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode) Returns HID_DDK_NO_PERM if permission verification fails. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode) Returns HID_DDK_INVALID_OPERATION if the connection to the HID DDK service fails or the caller is not the creator of the device. Ensure that OH_Hid_Init is called to complete initialization and that the caller is the creator of the device.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode) Returns HID_DDK_INVALID_PARAMETER if parameter verification fails. Possible causes: 1. The device ID is less than 0; 2. The input parameter length exceeds 7; 3. The input parameter items is a null pointer. Check the parameter validity.<br>         [HID_DDK_NULL_PTR](capi-hid-ddk-types-h.md#hid_ddkerrcode) Returns HID_DDK_NULL_PTR if the injection of the corresponding device is empty. Ensure that a valid device ID returned by OH_Hid_CreateDevice is used and that the device has not been destroyed. |

### OH_Hid_DestroyDevice()

```c
int32_t OH_Hid_DestroyDevice(int32_t deviceId)
```

**Description**

Destroys a device. Applicable to scenarios where system resources need to be released when a virtual HID device is no longer needed. It must be used in pairs with [OH_Hid_CreateDevice()](#oh_hid_createdevice), and only the device created by the current caller can be destroyed.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| int32_t deviceId | Device ID. It must be a device created by the current caller, and the value is a non-negative number. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): Operation successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): Permission verification failed. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode): Failed to connect to the HID DDK service, or the caller is not the creator of the device. Ensure that OH_Hid_Init has been called to complete initialization, and the caller is the creator of the device.<br>         [HID_DDK_NULL_PTR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The device does not exist. Ensure that a valid device ID returned by OH_Hid_CreateDevice is used, and the device has not been destroyed. |

### OH_Hid_Init()

```c
int32_t OH_Hid_Init(void)
```

**Description**

Initializes the HID DDK. This method must be called before using any other HID DDK methods. When no HID DDK functionality is needed anymore, [OH_Hid_Release()](#oh_hid_release) must be called to release resources.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): Operation successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): Permission verification fails. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The DDK initialization fails.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible causes: internal service error. Check the current operation and device status. |

### OH_Hid_Release()

```c
int32_t OH_Hid_Release(void)
```

**Description**

Releases the HID DDK. It must be used in pairs with [OH_Hid_Init()](#oh_hid_init).

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode) Operation successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode) Permission verification failed. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode) The DDK is not initialized. Ensure that [OH_Hid_Init()](#oh_hid_init) has been called to complete initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode) Failed to communicate with the DDK service. Possible causes: internal service error. Check the current operation and device status. |

### OH_Hid_Open()

```c
int32_t OH_Hid_Open(uint64_t deviceId, uint8_t interfaceIndex, Hid_DeviceHandle **dev)
```

**Description**

Opens the device specified by deviceId and interfaceIndex. Applicable to scenarios where communication with a specific HID device is required. After use, call [OH_Hid_Close()](#oh_hid_close) to release the device resources.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name                       | Description|
|----------------------------| -- |
| uint64_t deviceId          | ID of the device to operate, which can be obtained by calling [OH_Usb_GetDevices](capi-usb-ddk-api-h.md#oh_usb_getdevices). |
| uint8_t interfaceIndex     | Interface index for the API of the HID device.|
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) **dev | Pointer to the device operation handle, which is an output parameter. After the API is successfully executed, it is assigned a value that represents the opened HID device. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The DDK is not initialized. Ensure that [OH_Hid_Init()](#oh_hid_init) has been called to complete initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: internal service error. Check the current operation and device status.<br>         [HID_DDK_MEMORY_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Memory allocation for the device fails.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: abnormal device status, data transfer error, etc. Check the device status and parameters.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The **dev** parameter is null or **\*dev** is null.<br>         [HID_DDK_DEVICE_NOT_FOUND](capi-hid-ddk-types-h.md#hid_ddkerrcode): No device is found based on **deviceId** and **interfaceIndex**. |

### OH_Hid_Close()

```c
int32_t OH_Hid_Close(Hid_DeviceHandle **dev)
```

**Description**

Closes a device. It must be used in pairs with [OH_Hid_Open()](#oh_hid_open). Applicable to scenarios where device resources need to be released when communication with the HID device is no longer needed.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) **dev | Device operation handle. It must be opened and obtained through [OH_Hid_Open()](#oh_hid_open). After the API is called successfully, the resources are released and the handle is set to null. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode) Operation successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode) Permission verification failed. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode) DDK not initialized. Ensure that [OH_Hid_Init()](#oh_hid_init) has been called to complete initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode) Service communication with the DDK service failed. Possible causes: internal service error. Check the current operation and device status.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode) I/O operation failed. Possible causes: abnormal device status, data transfer error, etc. Check the device status and parameters.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode) dev is a null pointer or *dev is a null pointer. |

### OH_Hid_Write()

```c
int32_t OH_Hid_Write(Hid_DeviceHandle *dev, uint8_t *data, uint32_t length, uint32_t *bytesWritten)
```

**Description**

Writes an HID report to a device.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be used before being opened and obtained through [OH_Hid_Open()](#oh_hid_open). |
| uint8_t *data | Data to be written.|
| uint32_t length | Byte length of the data to write, which is greater than 0 and the maximum does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros), otherwise it fails Parameter verification. |
| uint32_t *bytesWritten | Number of written bytes.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode) Operation successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode) Permission verification failed. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode) Parameter verification failed. Possible causes: 1. dev is null;<br>             2. data is null; 3. length is 0; 4. length exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros);<br>             5. bytesWritten is null.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode) The DDK is not initialized. Ensure that [OH_Hid_Init()](#oh_hid_init) has been called to complete initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode) Service communication with the DDK failed. Possible causes: internal service error. Check the current operation and device status.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode) I/O operation failed. Possible causes: abnormal device status, data transfer error, etc. Check the device status and parameters. |

### OH_Hid_ReadTimeout()

```c
int32_t OH_Hid_ReadTimeout(Hid_DeviceHandle *dev, uint8_t *data, uint32_t bufSize, int timeout, uint32_t *bytesRead)
```

**Description**

Reads a report from the HID device within the specified timeout interval.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be used before being opened and obtained through [OH_Hid_Open()](#oh_hid_open). |
| uint8_t *data | Buffer for storing the read data.|
| uint32_t bufSize | Size of the buffer for storing read data, which is greater than 0 and the maximum does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros), otherwise it fails parameter verification. |
| int timeout | Timeout duration (in milliseconds). Value description: a value greater than 0 indicates the number of milliseconds to wait in blocking mode; 0 indicates immediate return; -1 indicates blocking until data is read, without returning a timeout. |
| uint32_t *bytesRead | Number of bytes to read.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. **dev** is null.<br>             2. **data** is null. 3. The value of **bufSize** is **0**. 4. The value of **bufSize** exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros).<br>             5. **bytesRead** is null.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The DDK is not initialized. Ensure that [OH_Hid_Init()](#oh_hid_init) has been called to complete initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: internal service error. Check the current operation and device status.<br>         [HID_DDK_MEMORY_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The memory data copy fails.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: abnormal device status, data transfer error, etc. Check the device status and parameters.<br>         [HID_DDK_TIMEOUT](capi-hid-ddk-types-h.md#hid_ddkerrcode): The read operation times out. |

### OH_Hid_Read()

```c
int32_t OH_Hid_Read(Hid_DeviceHandle *dev, uint8_t *data, uint32_t bufSize, uint32_t *bytesRead)
```

**Description**

Reads a report from the HID device. The blocking mode (that is, blocking remains active until data can be read) is used by default. You can call [OH_Hid_SetNonBlocking](capi-hid-ddk-api-h.md#oh_hid_setnonblocking) to change the mode.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle. It must be used before being opened and obtained through [OH_Hid_Open()](#oh_hid_open). |
| uint8_t *data | Buffer for storing the read data.|
| uint32_t bufSize | Size of the buffer for storing read data. The value must be greater than 0 and the maximum does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros), otherwise the parameter verification fails. |
| uint32_t *bytesRead | Number of bytes to read.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. **dev** is null.<br>             2. **data** is null. 3. The value of **bufSize** is **0**. 4. The value of **bufSize** exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros).<br>             5. **bytesRead** is null.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The DDK is not initialized. Ensure that [OH_Hid_Init()](#oh_hid_init) has been called to complete initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: an internal service error. Check the current operation and device status.<br>         [HID_DDK_MEMORY_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The memory data copy fails.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: abnormal device status, data transfer error, and so on. Check the device status and parameters.<br>         [HID_DDK_TIMEOUT](capi-hid-ddk-types-h.md#hid_ddkerrcode): The read operation times out. |

### OH_Hid_SetNonBlocking()

```c
int32_t OH_Hid_SetNonBlocking(Hid_DeviceHandle *dev, int nonBlock)
```

**Description**

Sets the device read mode to non-blocking mode.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be used before [OH_Hid_Open()](#oh_hid_open) to open and obtain. |
| int nonBlock | Whether to enable the non-blocking mode for reading data. - **1**: The non-blocking mode is enabled. When [OH_Hid_Read](capi-hid-ddk-api-h.md#oh_hid_read) is called, if the device has readable data, [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode) is returned;<br>                 if the device has no readable data, [HID_DDK_TIMEOUT](capi-hid-ddk-types-h.md#hid_ddkerrcode) is returned. - **0**: The non-blocking mode is disabled, and the blocking mode is enabled. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The DDK is not initialized. Ensure that [OH_Hid_Init()](#oh_hid_init) has been called to complete initialization.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. **dev** is null.<br>             2. The value of **nonBlock** is not **1** or **0**.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible causes: Internal service error. Check the current operation and device status. |

### OH_Hid_GetRawInfo()

```c
int32_t OH_Hid_GetRawInfo(Hid_DeviceHandle *dev, Hid_RawDevInfo *rawDevInfo)
```

**Description**

Obtains the original device information.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name                                                        | Description|
|-------------------------------------------------------------| -- |
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be used before [OH_Hid_Open()](#oh_hid_open) to open and obtain. |
| [Hid_RawDevInfo](capi-hidddk-hid-rawdevinfo.md) *rawDevInfo | Original device information, including the vendor ID, product ID, and bus type.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. **dev** is null.<br>             2. **rawDevInfo** is null.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The DDK is not initialized. Ensure that [OH_Hid_Init()](#oh_hid_init) has been called to complete initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: internal service error. Check the current operation and device status.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: abnormal device status, data transfer error, and so on. Check the device status and parameters.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode): This operation is not supported. |

### OH_Hid_GetRawName()

```c
int32_t OH_Hid_GetRawName(Hid_DeviceHandle *dev, char *data, uint32_t bufSize)
```

**Description**

Obtains the original device name.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be used before being opened and obtained through [OH_Hid_Open()](#oh_hid_open). |
| char *data | Buffer for storing the read data.|
| uint32_t bufSize | Size of the buffer for storing read data, which is greater than 0 and the maximum does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros), otherwise it cannot pass parameter verification. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. **dev** is null.<br>             2. **data** is null. 3. The value of **bufSize** is **0**. 4. The value of **bufSize** exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros).<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The DDK is not initialized. Ensure that [OH_Hid_Init()](#oh_hid_init) has been called to complete initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: internal service error. Check the current operation and device status.<br>         [HID_DDK_MEMORY_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The memory data copy fails.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: abnormal device status, data transfer error, etc. Check the device status and parameters.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode): This operation is not supported. |

### OH_Hid_GetPhysicalAddress()

```c
int32_t OH_Hid_GetPhysicalAddress(Hid_DeviceHandle *dev, char *data, uint32_t bufSize)
```

**Description**

Obtains the physical address of the HID device.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be used before being opened and obtained through [OH_Hid_Open()](#oh_hid_open). |
| char *data | Buffer for storing the read data.|
| uint32_t bufSize | Size of the buffer for storing read data, which is greater than 0 and the maximum does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros), otherwise it cannot pass parameter verification. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter verification fails. Possible causes: 1. **dev** is null.<br>             2. **data** is null. 3. The value of **bufSize** is **0**. 4. The value of **bufSize** exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros).<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The DDK is not initialized. Ensure that [OH_Hid_Init()](#oh_hid_init) has been called to complete initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK service fails. Possible cause: an internal service error. Check the current operation and device status.<br>         [HID_DDK_MEMORY_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The memory data copy fails.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: abnormal device status, data transfer errors, etc. Check the device status and parameters.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode): This operation is not supported. |

### OH_Hid_GetRawUniqueId()

```c
int32_t OH_Hid_GetRawUniqueId(Hid_DeviceHandle *dev, uint8_t *data, uint32_t bufSize)
```

**Description**

Obtains the original unique identifier of a device.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be used before being opened and obtained through [OH_Hid_Open()](#oh_hid_open). |
| uint8_t *data | Buffer for storing the read data.|
| uint32_t bufSize | Size of the buffer for storing read data, which is greater than 0 and the maximum does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros), otherwise it cannot pass the parameter verification. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. **dev** is null.<br>             2. **data** is null. 3. The value of **bufSize** is **0**. 4. The value of **bufSize** exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros).<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The DDK is not initialized. Ensure that [OH_Hid_Init()](#oh_hid_init) has been called to complete initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: internal service error. Check the current operation and device status.<br>         [HID_DDK_MEMORY_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The memory data copy fails.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: abnormal device status, data transfer error, and so on. Check the device status and parameters.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode): This operation is not supported. |

### OH_Hid_SendReport()

```c
int32_t OH_Hid_SendReport(Hid_DeviceHandle *dev, Hid_ReportType reportType, const uint8_t *data, uint32_t length)
```

**Description**

Sends an HID report of a specified type to a device.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description                                                                                               |
| -- |---------------------------------------------------------------------------------------------------|
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle. It must be opened and obtained through [OH_Hid_Open()](#oh_hid_open) before use. |
| [Hid_ReportType](capi-hid-ddk-types-h.md#hid_reporttype) reportType | Report type, which can be an input report, output report, or feature report. |
| const uint8_t *data | Data to be sent.                                                                                          |
| uint32_t length | Byte length of the data to send. It must be greater than 0 and the maximum does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros); otherwise, parameter verification fails. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode) Operation successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode) Permission verification failed. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode) Parameter verification failed. Possible causes: 1. dev is a null pointer;<br>             2. data is a null pointer; 3. length is 0; 4. length exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros).<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode) The DDK is not initialized. Ensure that [OH_Hid_Init()](#oh_hid_init) has been called to complete initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode) Failed to communicate with the DDK service. Possible causes: internal service error. Check the current operation and device status.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode) I/O operation failed. Possible causes: abnormal device status, data transfer error, etc. Check the device status and parameters.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode) This operation is not supported. |

### OH_Hid_GetReport()

```c
int32_t OH_Hid_GetReport(Hid_DeviceHandle *dev, Hid_ReportType reportType, uint8_t *data, uint32_t bufSize)
```

**Description**

Obtains an HID report of a specified type from the device.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be used before being opened and obtained through [OH_Hid_Open()](#oh_hid_open). |
| [Hid_ReportType](capi-hid-ddk-types-h.md#hid_reporttype) reportType | Report type.|
| uint8_t *data | Buffer for storing the read data.|
| uint32_t bufSize | Size of the buffer for storing read data, which is greater than 0 and the maximum does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros), otherwise it cannot pass the parameter verification. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter verification fails. Possible causes: 1. **dev** is null.<br>             2. **data** is null. 3. The value of **bufSize** is **0**. 4. The value of **bufSize** exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros).<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The DDK is not initialized. Ensure that [OH_Hid_Init()](#oh_hid_init) has been called to complete initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: an internal service error. Check the current operation and device status.<br>         [HID_DDK_MEMORY_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The memory data copy fails.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: abnormal device status, data transfer errors, etc. Check the device status and parameters.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode): This operation is not supported. |

### OH_Hid_GetReportDescriptor()

```c
int32_t OH_Hid_GetReportDescriptor(Hid_DeviceHandle *dev, uint8_t *buf, uint32_t bufSize, uint32_t *bytesRead)
```

**Description**

Obtains the report descriptor of the HID device.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be used before being opened and obtained through [OH_Hid_Open()](#oh_hid_open). |
| uint8_t *buf | Buffer for storing descriptors.|
| uint32_t bufSize | Size of the buffer in bytes, which is greater than 0 and the maximum does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros), otherwise it fails the parameter verification. |
| uint32_t *bytesRead | Number of bytes to read.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that the application has declared the ohos.permission.ACCESS_DDK_HID permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter verification fails. Possible causes: 1. dev is null.<br>             2. buf is null. 3. The value of bufSize is 0. 4. The value of bufSize exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros).<br>             5. bytesRead is null.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The DDK is not initialized. Ensure that [OH_Hid_Init()](#oh_hid_init) has been called to complete initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK service fails. Possible causes: internal service error. Check the current operation and device status.<br>         [HID_DDK_MEMORY_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The memory data copy fails.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: abnormal device status, data transfer error, and so on. Check the device status and parameters.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode): This operation is not supported. |

