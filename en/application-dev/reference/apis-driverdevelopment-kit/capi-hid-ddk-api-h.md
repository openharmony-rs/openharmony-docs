# hid_ddk_api.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

## Overview

Declares the HID DDK functions for accessing an input device from the host. DDK stands for Driver Development Kit. This module provides APIs for creating, opening, reading data from, and writing data to HID devices, as well as managing devices and injecting events. It supports two use modes. The first one is creating virtual HID devices and injecting events, which is suitable for simulating keyboard, mouse, and touchscreen inputs. The second one is accessing and communicating with real HID devices, which allows you to open, read, and write device reports and obtain device information. The second mode is applicable to scenarios where data interaction with HID devices is required.

**File to include**: <hid/hid_ddk_api.h>

**Library**: libhid.z.so

**System capability**: SystemCapability.Driver.HID.Extension

**Since**: 11

**Related module**: [HidDdk](capi-hidddk.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [int32_t OH_Hid_CreateDevice(Hid_Device *hidDevice, Hid_EventProperties *hidEventProperties)](#oh_hid_createdevice) | Creates a device. This function is applicable to scenarios where virtual HID input devices need to be simulated, such as simulating input devices like keyboards and mouse devices for automated testing. This function must be used in pairs with [OH_Hid_DestroyDevice](#oh_hid_destroydevice).|
| [int32_t OH_Hid_EmitEvent(int32_t deviceId, const Hid_EmitItem items[], uint16_t length)](#oh_hid_emitevent) | Sends an event list to a device. Events are injected into the system through the virtual device created by [OH_Hid_CreateDevice](#oh_hid_createdevice), and the system processes them as real input events. This function is applicable to scenarios where user input events are simulated, such as simulating key presses, mouse movements, and clicks for automated testing or remote control.|
| [int32_t OH_Hid_DestroyDevice(int32_t deviceId)](#oh_hid_destroydevice) | Destroys a device. This function must be used in pairs with [OH_Hid_CreateDevice](#oh_hid_createdevice). Only the device created by the current caller can be destroyed.|
| [int32_t OH_Hid_Init(void)](#oh_hid_init) | Initializes an HID DDK. This method must be called before all other HID DDK methods. When no HID DDK function is used, you must call [OH_Hid_Release](#oh_hid_release) to release resources.|
| [int32_t OH_Hid_Release(void)](#oh_hid_release) | Releases an HID DDK. This function must be used in pairs with [OH_Hid_Init](#oh_hid_init).|
| [int32_t OH_Hid_Open(uint64_t deviceId, uint8_t interfaceIndex, Hid_DeviceHandle **dev)](#oh_hid_open) | Opens the device specified by **deviceId** and **interfaceIndex**. After using the device, call [OH_Hid_Close](#oh_hid_close) to release the device resources.|
| [int32_t OH_Hid_Close(Hid_DeviceHandle **dev)](#oh_hid_close) | Closes a device. This function must be used in pairs with [OH_Hid_Open](#oh_hid_open). It can be used to release device resources when the communication with the HID device is no longer required.|
| [int32_t OH_Hid_Write(Hid_DeviceHandle *dev, uint8_t *data, uint32_t length, uint32_t *bytesWritten)](#oh_hid_write) | Writes an HID report to the device.|
| [int32_t OH_Hid_ReadTimeout(Hid_DeviceHandle *dev, uint8_t *data, uint32_t bufSize, int timeout, uint32_t *bytesRead)](#oh_hid_readtimeout) | Reads a report from the device within the specified timeout interval.|
| [int32_t OH_Hid_Read(Hid_DeviceHandle *dev, uint8_t *data, uint32_t bufSize, uint32_t *bytesRead)](#oh_hid_read) | Reads a report from the device. The blocking mode (that is, blocking remains active until data can be read) is used by default. You can call [OH_Hid_SetNonBlocking](capi-hid-ddk-api-h.md#oh_hid_setnonblocking) to change the mode.|
| [int32_t OH_Hid_SetNonBlocking(Hid_DeviceHandle *dev, int nonBlock)](#oh_hid_setnonblocking) | Sets the device read mode to non-blocking mode.|
| [int32_t OH_Hid_GetRawInfo(Hid_DeviceHandle *dev, Hid_RawDevInfo *rawDevInfo)](#oh_hid_getrawinfo) | Obtains the original device information.|
| [int32_t OH_Hid_GetRawName(Hid_DeviceHandle *dev, char *data, uint32_t bufSize)](#oh_hid_getrawname) | Obtains the original device name.|
| [int32_t OH_Hid_GetPhysicalAddress(Hid_DeviceHandle *dev, char *data, uint32_t bufSize)](#oh_hid_getphysicaladdress) | Obtains the physical address of a device.|
| [int32_t OH_Hid_GetRawUniqueId(Hid_DeviceHandle *dev, uint8_t *data, uint32_t bufSize)](#oh_hid_getrawuniqueid) | Obtains the original unique identifier of a device.|
| [int32_t OH_Hid_SendReport(Hid_DeviceHandle *dev, Hid_ReportType reportType, const uint8_t *data, uint32_t length)](#oh_hid_sendreport) | Sends an HID report of a specified type to the device.|
| [int32_t OH_Hid_GetReport(Hid_DeviceHandle *dev, Hid_ReportType reportType, uint8_t *data, uint32_t bufSize)](#oh_hid_getreport) | Obtains an HID report of a specified type from the device.|
| [int32_t OH_Hid_GetReportDescriptor(Hid_DeviceHandle *dev, uint8_t *buf, uint32_t bufSize, uint32_t *bytesRead)](#oh_hid_getreportdescriptor) | Obtains the report descriptor of the device.|

## Function Description

### OH_Hid_CreateDevice()

```c
int32_t OH_Hid_CreateDevice(Hid_Device *hidDevice, Hid_EventProperties *hidEventProperties)
```

**Description**

Creates a device. This function is applicable to scenarios where virtual HID input devices need to be simulated, such as simulating input devices like keyboards and mouse devices for automated testing. This function must be used in pairs with [OH_Hid_DestroyDevice](#oh_hid_destroydevice).

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
| int32_t | **deviceID**, indicating the ID of the device that is successfully created. The value must be a non-negative integer.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode): The HID DDK service connection fails. Possible cause: The DDK service is not initialized. Call **OH_Hid_Init** to complete the initialization.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. The input **hidDevice** is a null pointer.<br>         2. The input **hidEventProperties** is a null pointer. 3. The length of **properties** exceeds 7 characters. 4. The length of **hidEventTypes** exceeds 5 characters.<br>         5. The length of **hidKeys** exceeds 100 characters. 6. The length of **hidAbs** exceeds 26 characters. 7. The length of **hidRelBits** exceeds 13 characters.<br>         8. The length of **hidMiscellaneous** exceeds 6 characters.<br>         [HID_DDK_FAILURE](capi-hid-ddk-types-h.md#hid_ddkerrcode): The number of devices reaches the maximum value 200.|

### OH_Hid_EmitEvent()

```c
int32_t OH_Hid_EmitEvent(int32_t deviceId, const Hid_EmitItem items[], uint16_t length)
```

**Description**

Sends an event list to a device. Events are injected into the system through the virtual device created by [OH_Hid_CreateDevice](#oh_hid_createdevice), and the system processes them as real input events. This function is applicable to scenarios where user input events are simulated, such as simulating key presses, mouse movements, and clicks for automated testing or remote control.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| int32_t deviceId | Device ID, which must be the ID of the device created by the current caller using [OH_Hid_CreateDevice](#oh_hid_createdevice). The value must be a non-negative integer.|
| const [Hid_EmitItem](capi-hidddk-hid-emititem.md) items[] | List of the events to send. The event information includes the event type (**Hid_EventType**), code (**Hid_SynEvent**, **Hid_KeyCode**, **Hid_AbsAxes**, **Hid_RelAxes**, or **Hid_MscEvent**), and value (depending on the actual device input). The sent events will be injected into the specified device to simulate the corresponding input behavior on the device.|
| uint16_t length | Length of the event list (number of events to be sent at a time). The value range is [1, 7].|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The API call is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode): The HID DDK service connection fails or the caller is not the device creator. Ensure that **OH_Hid_Init** is called to complete the initialization and the caller is the device creator.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. The device ID is less than 0. 2. The length of the input parameter **length** exceeds 7 characters. 3. The input parameter **items** is a null pointer. Check the parameter validity.<br>         [HID_DDK_NULL_PTR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The corresponding device does not exist. Ensure that a valid device ID returned by **OH_Hid_CreateDevice** is used and the device is not destroyed.|

### OH_Hid_DestroyDevice()

```c
int32_t OH_Hid_DestroyDevice(int32_t deviceId)
```

**Description**

Destroys a device. This function can be used to release system resources when the virtual HID device is no longer required. This function must be used in pairs with [OH_Hid_CreateDevice](#oh_hid_createdevice). Only the device created by the current caller can be destroyed.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| int32_t deviceId | Device ID, which must be the ID of the device created by the current caller. The value must be a non-negative integer.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The API call is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode): The HID DDK service connection fails or the caller is not the device creator. Ensure that **OH_Hid_Init** is called to complete the initialization and the caller is the device creator.<br>         [HID_DDK_NULL_PTR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The device does not exist. Ensure that a valid device ID returned by **OH_Hid_CreateDevice** is used and the device is not destroyed.|

### OH_Hid_Init()

```c
int32_t OH_Hid_Init(void)
```

**Description**

Initializes an HID DDK. This method must be called before all other HID DDK methods. When no HID DDK function is used, you must call [OH_Hid_Release](#oh_hid_release) to release resources.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The DDK initialization fails.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: An internal service error occurs. Check the current operation and device status.|

### OH_Hid_Release()

```c
int32_t OH_Hid_Release(void)
```

**Description**

Releases an HID DDK. This function must be used in pairs with [OH_Hid_Init](#oh_hid_init).

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): DDK is not initialized. Ensure that you have called [OH_Hid_Init](#oh_hid_init) to complete the initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: An internal service error occurs. Check the current operation and device status.|

### OH_Hid_Open()

```c
int32_t OH_Hid_Open(uint64_t deviceId, uint8_t interfaceIndex, Hid_DeviceHandle **dev)
```

**Description**

Opens the device specified by **deviceId** and **interfaceIndex**. This function applies to scenarios where communication with a specific HID device is required. After using the device, call [OH_Hid_Close](#oh_hid_close) to release the device resources.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name                       | Description|
|----------------------------| -- |
| uint64_t deviceId          | ID of the device to be operated, which can be obtained by calling [OH_Usb_GetDevices](capi-usb-ddk-api-h.md#oh_usb_getdevices).|
| uint8_t interfaceIndex     | Interface index for the API of the HID device.|
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) **dev | Device operation handle. This is an output parameter. After the API is called successfully, a value is assigned to this parameter, indicating the opened HID device.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): DDK is not initialized. Ensure that you have called [OH_Hid_Init](#oh_hid_init) to complete the initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: An internal service error occurs. Check the current operation and device status.<br>         [HID_DDK_MEMORY_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Memory allocation for the device fails.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: The device status is abnormal or a data transmission error occurs. Check the device status and parameters.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The **dev** parameter or ***dev** is null.<br>         [HID_DDK_DEVICE_NOT_FOUND](capi-hid-ddk-types-h.md#hid_ddkerrcode): No device is found based on **deviceId** and **interfaceIndex**.|

### OH_Hid_Close()

```c
int32_t OH_Hid_Close(Hid_DeviceHandle **dev)
```

**Description**

Closes a device. This function must be used in pairs with [OH_Hid_Open](#oh_hid_open). It can be used to release device resources when the communication with the HID device is no longer required.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) **dev | Device operation handle, which must be opened and obtained by calling [OH_Hid_Open](#oh_hid_open). After the API is called successfully, the resources are released and the handle is set to null.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): DDK is not initialized. Ensure that you have called [OH_Hid_Init](#oh_hid_init) to complete the initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: An internal service error occurs. Check the current operation and device status.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: The device status is abnormal or a data transmission error occurs. Check the device status and parameters.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The **dev** parameter or ***dev** is null.|

### OH_Hid_Write()

```c
int32_t OH_Hid_Write(Hid_DeviceHandle *dev, uint8_t *data, uint32_t length, uint32_t *bytesWritten)
```

**Description**

Writes an HID report to the device.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be opened and obtained by calling [OH_Hid_Open](#oh_hid_open) before being used.|
| uint8_t *data | Data to be written.|
| uint32_t length | Length of the data to be written, in bytes. Ensure that the value is greater than 0 and does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros). Otherwise, the parameter verification fails.|
| uint32_t *bytesWritten | Number of written bytes.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. **dev** is null.<br>             2. **data** is null. 3. The value of **length** is **0**; 4. The value of **length** exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros).<br>             5. **bytesWritten** is null.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): DDK is not initialized. Ensure that you have called [OH_Hid_Init](#oh_hid_init) to complete the initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: An internal service error occurs. Check the current operation and device status.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: The device status is abnormal or a data transmission error occurs. Check the device status and parameters.|

### OH_Hid_ReadTimeout()

```c
int32_t OH_Hid_ReadTimeout(Hid_DeviceHandle *dev, uint8_t *data, uint32_t bufSize, int timeout, uint32_t *bytesRead)
```

**Description**

Reads a report from the device within the specified timeout interval.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be opened and obtained by calling [OH_Hid_Open](#oh_hid_open) before being used.|
| uint8_t *data | Buffer for storing the read data.|
| uint32_t bufSize | Size of the buffer for storing the read data. Ensure that the value is greater than 0 and does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros). Otherwise, the parameter verification fails.|
| int timeout | Timeout interval, in milliseconds. If the value is greater than 0, it indicates the number of milliseconds to wait before a timeout occurs. If the value is **0**, it indicates that the operation is performed immediately. If the value is **-1**, it indicates that the operation is blocked until the data is read and no timeout occurs.|
| uint32_t *bytesRead | Number of bytes to read.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. **dev** is null.<br>             2. **data** is null. 3. The value of **bufSize** is **0**. 4. The value of **bufSize** exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros).<br>             5. **bytesRead** is null.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): DDK is not initialized. Ensure that you have called [OH_Hid_Init](#oh_hid_init) to complete the initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: An internal service error occurs. Check the current operation and device status.<br>         [HID_DDK_MEMORY_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The memory data copy fails.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: The device status is abnormal or a data transmission error occurs. Check the device status and parameters.<br>         [HID_DDK_TIMEOUT](capi-hid-ddk-types-h.md#hid_ddkerrcode): The read operation times out.|

### OH_Hid_Read()

```c
int32_t OH_Hid_Read(Hid_DeviceHandle *dev, uint8_t *data, uint32_t bufSize, uint32_t *bytesRead)
```

**Description**

Reads a report from the device. The blocking mode (that is, blocking remains active until data can be read) is used by default. You can call [OH_Hid_SetNonBlocking](capi-hid-ddk-api-h.md#oh_hid_setnonblocking) to change the mode.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be opened and obtained by calling [OH_Hid_Open](#oh_hid_open) before being used.|
| uint8_t *data | Buffer for storing the read data.|
| uint32_t bufSize | Size of the buffer for storing the read data. Ensure that the value is greater than 0 and does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros). Otherwise, the parameter verification fails.|
| uint32_t *bytesRead | Number of bytes to read.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. **dev** is null.<br>             2. **data** is null. 3. The value of **bufSize** is **0**. 4. The value of **bufSize** exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros).<br>             5. **bytesRead** is null.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): DDK is not initialized. Ensure that you have called [OH_Hid_Init](#oh_hid_init) to complete the initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: An internal service error occurs. Check the current operation and device status.<br>         [HID_DDK_MEMORY_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The memory data copy fails.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: The device status is abnormal or a data transmission error occurs. Check the device status and parameters.<br>         [HID_DDK_TIMEOUT](capi-hid-ddk-types-h.md#hid_ddkerrcode): The read operation times out.|

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
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be opened and obtained by calling [OH_Hid_Open](#oh_hid_open) before being used.|
| int nonBlock | Whether to enable the non-blocking mode for reading data. **1**: The non-blocking mode is enabled. When [OH_Hid_Read](capi-hid-ddk-api-h.md#oh_hid_read) is called, if the device has readable data, [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode) is returned;<br>                 if the device has no readable data, [HID_DDK_TIMEOUT](capi-hid-ddk-types-h.md#hid_ddkerrcode) is returned. **0**: The non-blocking mode is disabled, and the blocking mode is enabled.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): DDK is not initialized. Ensure that you have called [OH_Hid_Init](#oh_hid_init) to complete the initialization.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. **dev** is null.<br>             2. The value of **nonBlock** is not **1** or **0**.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: An internal service error occurs. Check the current operation and device status.|

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
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be opened and obtained by calling [OH_Hid_Open](#oh_hid_open) before being used.|
| [Hid_RawDevInfo](capi-hidddk-hid-rawdevinfo.md) *rawDevInfo | Original device information, including the vendor ID, product ID, and bus type.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. **dev** is null.<br>             2. **rawDevInfo** is null.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): DDK is not initialized. Ensure that you have called [OH_Hid_Init](#oh_hid_init) to complete the initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: An internal service error occurs. Check the current operation and device status.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: The device status is abnormal or a data transmission error occurs. Check the device status and parameters.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode): This operation is not supported.|

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
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be opened and obtained by calling [OH_Hid_Open](#oh_hid_open) before being used.|
| char *data | Buffer for storing the read data.|
| uint32_t bufSize | Size of the buffer for storing the read data. Ensure that the value is greater than 0 and does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros). Otherwise, the parameter verification fails.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. **dev** is null.<br>             2. **data** is null. 3. The value of **bufSize** is **0**. 4. The value of **bufSize** exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros).<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): DDK is not initialized. Ensure that you have called [OH_Hid_Init](#oh_hid_init) to complete the initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: An internal service error occurs. Check the current operation and device status.<br>         [HID_DDK_MEMORY_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The memory data copy fails.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: The device status is abnormal or a data transmission error occurs. Check the device status and parameters.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode): This operation is not supported.|

### OH_Hid_GetPhysicalAddress()

```c
int32_t OH_Hid_GetPhysicalAddress(Hid_DeviceHandle *dev, char *data, uint32_t bufSize)
```

**Description**

Obtains the physical address of a device.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be opened and obtained by calling [OH_Hid_Open](#oh_hid_open) before being used.|
| char *data | Buffer for storing the read data.|
| uint32_t bufSize | Size of the buffer for storing the read data. Ensure that the value is greater than 0 and does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros). Otherwise, the parameter verification fails.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. **dev** is null.<br>             2. **data** is null. 3. The value of **bufSize** is **0**. 4. The value of **bufSize** exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros).<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): DDK is not initialized. Ensure that you have called [OH_Hid_Init](#oh_hid_init) to complete the initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: An internal service error occurs. Check the current operation and device status.<br>         [HID_DDK_MEMORY_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The memory data copy fails.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: The device status is abnormal or a data transmission error occurs. Check the device status and parameters.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode): This operation is not supported.|

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
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be opened and obtained by calling [OH_Hid_Open](#oh_hid_open) before being used.|
| uint8_t *data | Buffer for storing the read data.|
| uint32_t bufSize | Size of the buffer for storing the read data. Ensure that the value is greater than 0 and does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros). Otherwise, the parameter verification fails.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. **dev** is null.<br>             2. **data** is null. 3. The value of **bufSize** is **0**. 4. The value of **bufSize** exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros).<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): DDK is not initialized. Ensure that you have called [OH_Hid_Init](#oh_hid_init) to complete the initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: An internal service error occurs. Check the current operation and device status.<br>         [HID_DDK_MEMORY_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The memory data copy fails.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: The device status is abnormal or a data transmission error occurs. Check the device status and parameters.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode): This operation is not supported.|

### OH_Hid_SendReport()

```c
int32_t OH_Hid_SendReport(Hid_DeviceHandle *dev, Hid_ReportType reportType, const uint8_t *data, uint32_t length)
```

**Description**

Sends an HID report of a specified type to the device.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description|
| -- |---------------------------------------------------------------------------------------------------|
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be opened and obtained by calling [OH_Hid_Open](#oh_hid_open) before being used.|
| [Hid_ReportType](capi-hid-ddk-types-h.md#hid_reporttype) reportType | Report type, which can be an input report, output report, or feature report.|
| const uint8_t *data | Data to be sent.|
| uint32_t length | Length of the data to be sent, in bytes. Ensure that the value is greater than 0 and does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros). Otherwise, the parameter verification fails.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. **dev** is null.<br>             2. **data** is null. 3. The value of **length** is **0**; 4. The value of **length** exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros).<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): DDK is not initialized. Ensure that you have called [OH_Hid_Init](#oh_hid_init) to complete the initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: An internal service error occurs. Check the current operation and device status.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: The device status is abnormal or a data transmission error occurs. Check the device status and parameters.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode): This operation is not supported.|

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
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be opened and obtained by calling [OH_Hid_Open](#oh_hid_open) before being used.|
| [Hid_ReportType](capi-hid-ddk-types-h.md#hid_reporttype) reportType | Report type.|
| uint8_t *data | Buffer for storing the read data.|
| uint32_t bufSize | Size of the buffer for storing the read data. Ensure that the value is greater than 0 and does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros). Otherwise, the parameter verification fails.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. **dev** is null.<br>             2. **data** is null. 3. The value of **bufSize** is **0**. 4. The value of **bufSize** exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros).<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): DDK is not initialized. Ensure that you have called [OH_Hid_Init](#oh_hid_init) to complete the initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: An internal service error occurs. Check the current operation and device status.<br>         [HID_DDK_MEMORY_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The memory data copy fails.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: The device status is abnormal or a data transmission error occurs. Check the device status and parameters.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode): This operation is not supported.|

### OH_Hid_GetReportDescriptor()

```c
int32_t OH_Hid_GetReportDescriptor(Hid_DeviceHandle *dev, uint8_t *buf, uint32_t bufSize, uint32_t *bytesRead)
```

**Description**

Obtains the report descriptor of the device.

**Required permissions**: ohos.permission.ACCESS_DDK_HID

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md) *dev | Device operation handle, which must be opened and obtained by calling [OH_Hid_Open](#oh_hid_open) before being used.|
| uint8_t *buf | Buffer for storing descriptors.|
| uint32_t bufSize | Size of the buffer, in bytes. Ensure that the value is greater than 0 and does not exceed [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros). Otherwise, the parameter verification fails.|
| uint32_t *bytesRead | Number of bytes to read.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [HID_DDK_SUCCESS](capi-hid-ddk-types-h.md#hid_ddkerrcode): The operation is successful.<br>         [HID_DDK_NO_PERM](capi-hid-ddk-types-h.md#hid_ddkerrcode): The permission verification fails. Ensure that you have declared the **ohos.permission.ACCESS_DDK_HID** permission.<br>         [HID_DDK_INVALID_PARAMETER](capi-hid-ddk-types-h.md#hid_ddkerrcode): The parameter check fails. Possible causes: 1. **dev** is null.<br>             2. **buf** is null. 3. The value of **bufSize** is **0**. 4. The value of **bufSize** exceeds [HID_MAX_REPORT_BUFFER_SIZE](capi-hid-ddk-types-h.md#macros).<br>             5. **bytesRead** is null.<br>         [HID_DDK_INIT_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): DDK is not initialized. Ensure that you have called [OH_Hid_Init](#oh_hid_init) to complete the initialization.<br>         [HID_DDK_SERVICE_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): Communication with the DDK server fails. Possible cause: An internal service error occurs. Check the current operation and device status.<br>         [HID_DDK_MEMORY_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The memory data copy fails.<br>         [HID_DDK_IO_ERROR](capi-hid-ddk-types-h.md#hid_ddkerrcode): The I/O operation fails. Possible causes: The device status is abnormal or a data transmission error occurs. Check the device status and parameters.<br>         [HID_DDK_INVALID_OPERATION](capi-hid-ddk-types-h.md#hid_ddkerrcode): This operation is not supported.|
