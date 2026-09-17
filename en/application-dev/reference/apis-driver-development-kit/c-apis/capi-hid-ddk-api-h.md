# hid_ddk_api.h

## Overview

Declares the HID DDK functions for accessing an input device from the host.

**Library**: libhid.z.so

**System capability**: SystemCapability.Driver.HID.Extension File to include: <hid/hid_ddk_api.h>

**Since**: 11

**Related module**: [HidDdk](capi-hidddk.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_Hid_CreateDevice(Hid_Device *hidDevice, Hid_EventProperties *hidEventProperties)](#oh_hid_createdevice) | Creates a device. |
| [int32_t OH_Hid_EmitEvent(int32_t deviceId, const Hid_EmitItem items[], uint16_t length)](#oh_hid_emitevent) | Sends an event list to a device. |
| [int32_t OH_Hid_DestroyDevice(int32_t deviceId)](#oh_hid_destroydevice) | Destroys a device. |
| [int32_t OH_Hid_Init(void)](#oh_hid_init) | Initializes an HID DDK. |
| [int32_t OH_Hid_Release(void)](#oh_hid_release) | Releases an HID DDK. |
| [int32_t OH_Hid_Open(uint64_t deviceId, uint8_t interfaceIndex, Hid_DeviceHandle **dev)](#oh_hid_open) | Opens the device specified by **deviceId** and **interfaceIndex**. |
| [int32_t OH_Hid_Close(Hid_DeviceHandle **dev)](#oh_hid_close) | Closes an HID device. |
| [int32_t OH_Hid_Write(Hid_DeviceHandle *dev, uint8_t *data, uint32_t length, uint32_t *bytesWritten)](#oh_hid_write) | Writes a report to an HID device. |
| [int32_t OH_Hid_ReadTimeout(Hid_DeviceHandle *dev, uint8_t *data, uint32_t bufSize, int timeout, uint32_t *bytesRead)](#oh_hid_readtimeout) | Reads a report from the HID device within the specified timeout interval. |
| [int32_t OH_Hid_Read(Hid_DeviceHandle *dev, uint8_t *data, uint32_t bufSize, uint32_t *bytesRead)](#oh_hid_read) | Reads a report from the HID device. The blocking mode (that is, blocking remains active until data can be read) is used by default. You can call [OH_Hid_SetNonBlocking](capi-hid-ddk-api-h.md#oh_hid_setnonblocking) to change the mode. |
| [int32_t OH_Hid_SetNonBlocking(Hid_DeviceHandle *dev, int nonBlock)](#oh_hid_setnonblocking) | Sets the device read mode to non-blocking mode. |
| [int32_t OH_Hid_GetRawInfo(Hid_DeviceHandle *dev, Hid_RawDevInfo *rawDevInfo)](#oh_hid_getrawinfo) | Obtains the original device information. |
| [int32_t OH_Hid_GetRawName(Hid_DeviceHandle *dev, char *data, uint32_t bufSize)](#oh_hid_getrawname) | Obtains the original device name. |
| [int32_t OH_Hid_GetPhysicalAddress(Hid_DeviceHandle *dev, char *data, uint32_t bufSize)](#oh_hid_getphysicaladdress) | Obtains the physical address of the HID device. |
| [int32_t OH_Hid_GetRawUniqueId(Hid_DeviceHandle *dev, uint8_t *data, uint32_t bufSize)](#oh_hid_getrawuniqueid) | Obtains the original unique identifier of a device. |
| [int32_t OH_Hid_SendReport(Hid_DeviceHandle *dev, Hid_ReportType reportType, const uint8_t *data, uint32_t length)](#oh_hid_sendreport) | Sends a report to the HID device. |
| [int32_t OH_Hid_GetReport(Hid_DeviceHandle *dev, Hid_ReportType reportType, uint8_t *data, uint32_t bufSize)](#oh_hid_getreport) | Obtains a report from the HID device. |
| [int32_t OH_Hid_GetReportDescriptor(Hid_DeviceHandle *dev, uint8_t *buf, uint32_t bufSize, uint32_t *bytesRead)](#oh_hid_getreportdescriptor) | Obtains the report descriptor of the HID device. |

## Function description

### OH_Hid_CreateDevice()

```c
int32_t OH_Hid_CreateDevice(Hid_Device *hidDevice, Hid_EventProperties *hidEventProperties)
```

**Description**

Creates a device.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Hid_Device *hidDevice | Pointer to the basic information about the device to create, including the device name, vendor ID, and product ID. |
| Hid_EventProperties *hidEventProperties | Pointer to the event properties related to the device to create, including the event type, key event properties, absolute coordinate event properties, and relative coordinate event properties. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | deviceID (a non-negative number) if the API call is successful.      {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INVALID_OPERATION}: The hid_ddk service connection fails.<br>    {@link HID_DDK_INVALID_PARAMETER}: The parameter check fails. Possible causes: 1. The input hidDevice is a<br>    null pointer.<br>    2. The input hidEventProperties is a null pointer. 3. The length of properties exceeds 7 characters.<br>    4. The length of hidEventTypes exceeds 5 characters.<br>    5. The length of hidKeys exceeds 100 characters. 6. The length of hidAbs exceeds 26 characters. 7. The<br>    length of hidRelBits exceeds 13 characters. 8. The length of hidMiscellaneous exceeds 6 characters.<br>    {@link HID_DDK_FAILURE}: The number of devices reaches the maximum value 200. |

### OH_Hid_EmitEvent()

```c
int32_t OH_Hid_EmitEvent(int32_t deviceId, const Hid_EmitItem items[], uint16_t length)
```

**Description**

Sends an event list to a device.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t deviceId | Device ID. |
| const Hid_EmitItem items[] | List of the events to send. The event information includes the event type (**Hid_EventType**), code (**Hid_SynEvent**, **Hid_KeyCode**, **Hid_AbsAxes**, **Hid_RelAxes**, or **Hid_MscEvent**), and value (depending on the actual device input). |
| uint16_t length | Length of the event list (number of events to be sent at a time). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link HID_DDK_SUCCESS}: The API call is successful.<br>    {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INVALID_OPERATION}: The hid_ddk service connection fails or the caller is not the device creator.<br>    {@link HID_DDK_INVALID_PARAMETER}: The parameter check fails. Possible causes: 1. The device ID is less than 0.<br>    2. The length of the input parameter length exceeds 7 characters. 3. The input parameter items is a null<br>    pointer.<br>    {@link HID_DDK_NULL_PTR}: The input device is a null pointer. |

### OH_Hid_DestroyDevice()

```c
int32_t OH_Hid_DestroyDevice(int32_t deviceId)
```

**Description**

Destroys a device.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t deviceId | Device ID. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link HID_DDK_SUCCESS}: The API call is successful.<br>    {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INVALID_OPERATION}: The hid_ddk service connection fails or the caller is not the device creator.<br>    {@link HID_DDK_NULL_PTR}: The corresponding device does not exist. |

### OH_Hid_Init()

```c
int32_t OH_Hid_Init(void)
```

**Description**

Initializes an HID DDK.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link HID_DDK_SUCCESS}: The operation is successful.<br>    {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INIT_ERROR}: The DDK initialization fails.<br>    {@link HID_DDK_SERVICE_ERROR}: Communication with the DDK server fails. |

### OH_Hid_Release()

```c
int32_t OH_Hid_Release(void)
```

**Description**

Releases an HID DDK.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link HID_DDK_SUCCESS}: The operation is successful.<br>    {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link HID_DDK_SERVICE_ERROR}: Communication with the DDK server fails. |

### OH_Hid_Open()

```c
int32_t OH_Hid_Open(uint64_t deviceId, uint8_t interfaceIndex, Hid_DeviceHandle **dev)
```

**Description**

Opens the device specified by **deviceId** and **interfaceIndex**.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t deviceId | Device ID. |
| uint8_t interfaceIndex | Interface index for the API of the HID device. |
| Hid_DeviceHandle **dev | Device operation handle. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link HID_DDK_SUCCESS}: The operation is successful.<br>    {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link HID_DDK_SERVICE_ERROR}: Communication with the DDK server fails.<br>    {@link HID_DDK_MEMORY_ERROR}: Memory allocation for the device fails.<br>    {@link HID_DDK_IO_ERROR}: The I/O operation fails.<br>    {@link HID_DDK_INVALID_PARAMETER}: The dev parameter or dev is null.<br>    {@link HID_DDK_DEVICE_NOT_FOUND}: No device is found based on deviceId and interfaceIndex. |

### OH_Hid_Close()

```c
int32_t OH_Hid_Close(Hid_DeviceHandle **dev)
```

**Description**

Closes an HID device.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| Hid_DeviceHandle **dev | Device operation handle. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link HID_DDK_SUCCESS}: The operation is successful.<br>    {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link HID_DDK_SERVICE_ERROR}: Communication with the DDK server fails.<br>    {@link HID_DDK_IO_ERROR}: The I/O operation fails.<br>    {@link HID_DDK_INVALID_PARAMETER}: The dev parameter or dev is null. |

### OH_Hid_Write()

```c
int32_t OH_Hid_Write(Hid_DeviceHandle *dev, uint8_t *data, uint32_t length, uint32_t *bytesWritten)
```

**Description**

Writes a report to an HID device.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| Hid_DeviceHandle *dev | Device operation handle. |
| uint8_t *data | Data to be written. |
| uint32_t length | Length of the data to be written. The maximum value is {@link HID_MAX_REPORT_BUFFER_SIZE}. Otherwise, the parameter verification fails. |
| uint32_t *bytesWritten | Number of written bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link HID_DDK_SUCCESS}: The operation is successful.<br>    {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INVALID_PARAMETER}: The parameter check fails. Possible causes: 1. dev is null.<br>    2. data is null. 3. The value of length is 0; 4. The value of length<br>    exceeds {@link HID_MAX_REPORT_BUFFER_SIZE}. 5. bytesWritten is null.<br>    {@link HID_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link HID_DDK_SERVICE_ERROR}: Communication with the DDK server fails.<br>    {@link HID_DDK_IO_ERROR}: The I/O operation fails. |

### OH_Hid_ReadTimeout()

```c
int32_t OH_Hid_ReadTimeout(Hid_DeviceHandle *dev, uint8_t *data, uint32_t bufSize, int timeout, uint32_t *bytesRead)
```

**Description**

Reads a report from the HID device within the specified timeout interval.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| Hid_DeviceHandle *dev | Device operation handle. |
| uint8_t *data | Buffer for storing the read data. |
| uint32_t bufSize | Size of the buffer for storing the read data. The maximum size is {@link HID_MAX_REPORT_BUFFER_SIZE}. Otherwise, the parameter verification fails. |
| int timeout | Timeout interval, in ms. The value **-1** indicates block waiting. |
| uint32_t *bytesRead | Number of bytes to read. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link HID_DDK_SUCCESS}: The operation is successful.<br>    {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INVALID_PARAMETER}: The parameter check fails. Possible causes: 1. dev is null.<br>    2. data is null. 3. The value of bufSize is 0. 4. The value of bufSize<br>    exceeds {@link HID_MAX_REPORT_BUFFER_SIZE}. 5. bytesRead is null.<br>    {@link HID_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link HID_DDK_SERVICE_ERROR}: Communication with the DDK server fails.<br>    {@link HID_DDK_MEMORY_ERROR}: The memory data copy fails.<br>    {@link HID_DDK_IO_ERROR}: The I/O operation fails.<br>    {@link HID_DDK_TIMEOUT}: The read operation times out. |

### OH_Hid_Read()

```c
int32_t OH_Hid_Read(Hid_DeviceHandle *dev, uint8_t *data, uint32_t bufSize, uint32_t *bytesRead)
```

**Description**

Reads a report from the HID device. The blocking mode (that is, blocking remains active until data can be read) is used by default. You can call [OH_Hid_SetNonBlocking](capi-hid-ddk-api-h.md#oh_hid_setnonblocking) to change the mode.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| Hid_DeviceHandle *dev | Device operation handle. |
| uint8_t *data | Buffer for storing the read data. |
| uint32_t bufSize | Size of the buffer for storing the read data. The maximum size is {@link HID_MAX_REPORT_BUFFER_SIZE}. Otherwise, the parameter verification fails. |
| uint32_t *bytesRead | Number of bytes to read. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link HID_DDK_SUCCESS}: The operation is successful.<br>    {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INVALID_PARAMETER}: The parameter check fails. Possible causes: 1. dev is null.<br>    2. data is null. 3. The value of bufSize is 0. 4. The value of bufSize<br>    exceeds {@link HID_MAX_REPORT_BUFFER_SIZE}. 5. bytesRead is null.<br>    {@link HID_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link HID_DDK_SERVICE_ERROR}: Communication with the DDK server fails.<br>    {@link HID_DDK_MEMORY_ERROR}: The memory data copy fails.<br>    {@link HID_DDK_IO_ERROR}: The I/O operation fails.<br>    {@link HID_DDK_TIMEOUT}: The read operation times out. |

### OH_Hid_SetNonBlocking()

```c
int32_t OH_Hid_SetNonBlocking(Hid_DeviceHandle *dev, int nonBlock)
```

**Description**

Sets the device read mode to non-blocking mode.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| Hid_DeviceHandle *dev | Device operation handle. |
| int nonBlock | Whether to enable the non-blocking mode for reading data. - **1**: The non-blocking mode is enabled. When [OH_Hid_Read](capi-hid-ddk-api-h.md#oh_hid_read) is called, if the device has readable data, {@link HID_DDK_SUCCESS} is returned; if the<br>    device has no readable data, {@link HID_DDK_TIMEOUT} is returned. - **0**: The non-blocking mode is disabled. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link HID_DDK_SUCCESS}: The operation is successful.<br>    {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link HID_DDK_INVALID_PARAMETER}: The parameter check fails. Possible causes: 1. dev is null.<br>    2. The value of nonBlock is not 1 or 0.<br>    {@link HID_DDK_SERVICE_ERROR}: Communication with the DDK server fails. |

### OH_Hid_GetRawInfo()

```c
int32_t OH_Hid_GetRawInfo(Hid_DeviceHandle *dev, Hid_RawDevInfo *rawDevInfo)
```

**Description**

Obtains the original device information.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| Hid_DeviceHandle *dev | Device operation handle. |
| Hid_RawDevInfo *rawDevInfo | Original device information, including the vendor ID, product ID, and bus type. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link HID_DDK_SUCCESS}: The operation is successful.<br>    {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INVALID_PARAMETER}: The parameter check fails. Possible causes: 1. dev is null.<br>    2. rawDevInfo is null.<br>    {@link HID_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link HID_DDK_SERVICE_ERROR}: Communication with the DDK server fails.<br>    {@link HID_DDK_IO_ERROR}: The I/O operation fails.<br>    {@link HID_DDK_INVALID_OPERATION}: This operation is not supported. |

### OH_Hid_GetRawName()

```c
int32_t OH_Hid_GetRawName(Hid_DeviceHandle *dev, char *data, uint32_t bufSize)
```

**Description**

Obtains the original device name.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| Hid_DeviceHandle *dev | Device operation handle. |
| char *data | Buffer for storing the read data. |
| uint32_t bufSize | Size of the buffer for storing the read data. The maximum size is {@link HID_MAX_REPORT_BUFFER_SIZE}. Otherwise, the parameter verification fails. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link HID_DDK_SUCCESS}: The operation is successful.<br>    {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INVALID_PARAMETER}: The parameter check fails. Possible causes: 1. dev is null.<br>    2. data is null. 3. The value of bufSize is 0.<br>    4. The value of bufSize exceeds {@link HID_MAX_REPORT_BUFFER_SIZE}.<br>    {@link HID_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link HID_DDK_SERVICE_ERROR}: Communication with the DDK server fails.<br>    {@link HID_DDK_MEMORY_ERROR}: The memory data copy fails.<br>    {@link HID_DDK_IO_ERROR}: The I/O operation fails.<br>    {@link HID_DDK_INVALID_OPERATION}: This operation is not supported. |

### OH_Hid_GetPhysicalAddress()

```c
int32_t OH_Hid_GetPhysicalAddress(Hid_DeviceHandle *dev, char *data, uint32_t bufSize)
```

**Description**

Obtains the physical address of the HID device.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| Hid_DeviceHandle *dev | Device operation handle. |
| char *data | Buffer for storing the read data. |
| uint32_t bufSize | Size of the buffer for storing the read data. The maximum size is {@link HID_MAX_REPORT_BUFFER_SIZE}. Otherwise, the parameter verification fails. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link HID_DDK_SUCCESS}: The operation is successful.<br>    {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INVALID_PARAMETER}: The parameter check fails. Possible causes: 1. dev is null.<br>    2. data is null. 3. The value of bufSize is 0.<br>    4. The value of bufSize exceeds {@link HID_MAX_REPORT_BUFFER_SIZE}.<br>    {@link HID_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link HID_DDK_SERVICE_ERROR}: Communication with the DDK server fails.<br>    {@link HID_DDK_MEMORY_ERROR}: The memory data copy fails.<br>    {@link HID_DDK_IO_ERROR}: The I/O operation fails.<br>    {@link HID_DDK_INVALID_OPERATION}: This operation is not supported. |

### OH_Hid_GetRawUniqueId()

```c
int32_t OH_Hid_GetRawUniqueId(Hid_DeviceHandle *dev, uint8_t *data, uint32_t bufSize)
```

**Description**

Obtains the original unique identifier of a device.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| Hid_DeviceHandle *dev | Device operation handle. |
| uint8_t *data | Buffer for storing the read data. |
| uint32_t bufSize | Size of the buffer for storing the read data. The maximum size is {@link HID_MAX_REPORT_BUFFER_SIZE}. Otherwise, the parameter verification fails. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link HID_DDK_SUCCESS}: The operation is successful.<br>    {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INVALID_PARAMETER}: The parameter check fails. Possible causes: 1. dev is null.<br>    2. data is null. 3. The value of bufSize is 0.<br>    4. The value of bufSize exceeds {@link HID_MAX_REPORT_BUFFER_SIZE}.<br>    {@link HID_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link HID_DDK_SERVICE_ERROR}: Communication with the DDK server fails.<br>    {@link HID_DDK_MEMORY_ERROR}: The memory data copy fails.<br>    {@link HID_DDK_IO_ERROR}: The I/O operation fails.<br>    {@link HID_DDK_INVALID_OPERATION}: This operation is not supported. |

### OH_Hid_SendReport()

```c
int32_t OH_Hid_SendReport(Hid_DeviceHandle *dev, Hid_ReportType reportType, const uint8_t *data, uint32_t length)
```

**Description**

Sends a report to the HID device.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| Hid_DeviceHandle *dev | Device operation handle. |
| Hid_ReportType reportType | Report type. |
| const uint8_t *data | Data to be sent. |
| uint32_t length | Length of the data to be sent, in bytes. The maximum value is {@link HID_MAX_REPORT_BUFFER_SIZE}. Otherwise, the parameter verification fails. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link HID_DDK_SUCCESS}: The operation is successful.<br>    {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INVALID_PARAMETER}: The parameter check fails. Possible causes: 1. dev is null.<br>    2. data is null. 3. The value of length is 0;<br>    4. The value of length exceeds {@link HID_MAX_REPORT_BUFFER_SIZE}.<br>    {@link HID_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link HID_DDK_SERVICE_ERROR}: Communication with the DDK server fails.<br>    {@link HID_DDK_IO_ERROR}: The I/O operation fails.<br>    {@link HID_DDK_INVALID_OPERATION}: This operation is not supported. |

### OH_Hid_GetReport()

```c
int32_t OH_Hid_GetReport(Hid_DeviceHandle *dev, Hid_ReportType reportType, uint8_t *data, uint32_t bufSize)
```

**Description**

Obtains a report from the HID device.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| Hid_DeviceHandle *dev | Device operation handle. |
| Hid_ReportType reportType | Report type. |
| uint8_t *data | Buffer for storing the read data. |
| uint32_t bufSize | Size of the buffer for storing the read data. The maximum size is {@link HID_MAX_REPORT_BUFFER_SIZE}. Otherwise, the parameter verification fails. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link HID_DDK_SUCCESS}: The operation is successful.<br>    {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INVALID_PARAMETER}: The parameter check fails. Possible causes: 1. dev is null.<br>    2. data is null. 3. The value of bufSize is 0.<br>    4. The value of bufSize exceeds {@link HID_MAX_REPORT_BUFFER_SIZE}.<br>    {@link HID_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link HID_DDK_SERVICE_ERROR}: Communication with the DDK server fails.<br>    {@link HID_DDK_MEMORY_ERROR}: The memory data copy fails.<br>    {@link HID_DDK_IO_ERROR}: The I/O operation fails.<br>    {@link HID_DDK_INVALID_OPERATION}: This operation is not supported. |

### OH_Hid_GetReportDescriptor()

```c
int32_t OH_Hid_GetReportDescriptor(Hid_DeviceHandle *dev, uint8_t *buf, uint32_t bufSize, uint32_t *bytesRead)
```

**Description**

Obtains the report descriptor of the HID device.

**Required permission**: ohos.permission.ACCESS_DDK_HID

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| Hid_DeviceHandle *dev | Device operation handle. |
| uint8_t *buf | Buffer for storing descriptors. |
| uint32_t bufSize | Size of the buffer, in bytes. The maximum value is {@link HID_MAX_REPORT_BUFFER_SIZE}. Otherwise, the parameter verification fails. |
| uint32_t *bytesRead | Number of bytes to read. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link HID_DDK_SUCCESS}: The operation is successful.<br>    {@link HID_DDK_NO_PERM}: The permission verification fails.<br>    {@link HID_DDK_INVALID_PARAMETER}: The parameter check fails. Possible causes: 1. dev is null.<br>    2. buf is null. 3. The value of bufSize is 0. 4. The value of bufSize<br>    exceeds {@link HID_MAX_REPORT_BUFFER_SIZE}. 5. bytesRead is null.<br>    {@link HID_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link HID_DDK_SERVICE_ERROR}: Communication with the DDK server fails.<br>    {@link HID_DDK_MEMORY_ERROR}: The memory data copy fails.<br>    {@link HID_DDK_IO_ERROR}: The I/O operation fails.<br>    {@link HID_DDK_INVALID_OPERATION}: This operation is not supported. |


