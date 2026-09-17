# scsi_peripheral_api.h

## Overview

Declares the SCSI Peripheral DDK APIs used by the host to access the SCSI device.

**Library**: libscsi.z.so

**System capability**: SystemCapability.Driver.SCSI.Extension

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_ScsiPeripheral_Init(void)](#oh_scsiperipheral_init) | Initializes the SCSI Peripheral DDK. |
| [int32_t OH_ScsiPeripheral_Release(void)](#oh_scsiperipheral_release) | Releases the SCSI Peripheral DDK. |
| [int32_t OH_ScsiPeripheral_Open(uint64_t deviceId, uint8_t interfaceIndex, ScsiPeripheral_Device **dev)](#oh_scsiperipheral_open) | Opens the SCSI device specified by **deviceId** and **interfaceIndex**. The **deviceId** can be obtained by shifting the bus number of the USB device left by 32 bits and then performing a bitwise OR operation with the device address. **interfaceIndex** refers to the index of the USB interface to be opened. |
| [int32_t OH_ScsiPeripheral_Close(ScsiPeripheral_Device **dev)](#oh_scsiperipheral_close) | Closes the SCSI device. |
| [int32_t OH_ScsiPeripheral_TestUnitReady(ScsiPeripheral_Device *dev, ScsiPeripheral_TestUnitReadyRequest *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_testunitready) | Checks whether the logical unit is ready. |
| [int32_t OH_ScsiPeripheral_Inquiry(ScsiPeripheral_Device *dev, ScsiPeripheral_InquiryRequest *request, ScsiPeripheral_InquiryInfo *inquiryInfo, ScsiPeripheral_Response *response)](#oh_scsiperipheral_inquiry) | Queries basic information about the SCSI device. |
| [int32_t OH_ScsiPeripheral_ReadCapacity10(ScsiPeripheral_Device *dev, ScsiPeripheral_ReadCapacityRequest *request, ScsiPeripheral_CapacityInfo *capacityInfo, ScsiPeripheral_Response *response)](#oh_scsiperipheral_readcapacity10) | Obtains the capacity information about the SCSI device. |
| [int32_t OH_ScsiPeripheral_RequestSense(ScsiPeripheral_Device *dev, ScsiPeripheral_RequestSenseRequest *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_requestsense) | Obtains sense data, that is, information returned by the SCSI device to the host to report the device status, error information, and diagnosis information. |
| [int32_t OH_ScsiPeripheral_Read10(ScsiPeripheral_Device *dev, ScsiPeripheral_IORequest *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_read10) | Reads data from the specified logical block(s). |
| [int32_t OH_ScsiPeripheral_Write10(ScsiPeripheral_Device *dev, ScsiPeripheral_IORequest *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_write10) | Writes data to the specified logical block(s) of a device. |
| [int32_t OH_ScsiPeripheral_Verify10(ScsiPeripheral_Device *dev, ScsiPeripheral_VerifyRequest *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_verify10) | Verifies the specified logical block(s). |
| [int32_t OH_ScsiPeripheral_SendRequestByCdb(ScsiPeripheral_Device *dev, ScsiPeripheral_Request *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_sendrequestbycdb) | Sends SCSI commands in CDB mode. |
| [int32_t OH_ScsiPeripheral_CreateDeviceMemMap(ScsiPeripheral_Device *dev, size_t size, ScsiPeripheral_DeviceMemMap **devMmap)](#oh_scsiperipheral_createdevicememmap) | Creates a buffer. To avoid resource leakage, use [OH_ScsiPeripheral_DestroyDeviceMemMap](capi-scsi-peripheral-api-h.md#oh_scsiperipheral_destroydevicememmap) to destroy a buffer after use. |
| [int32_t OH_ScsiPeripheral_DestroyDeviceMemMap(ScsiPeripheral_DeviceMemMap *devMmap)](#oh_scsiperipheral_destroydevicememmap) | Destroys a buffer. To prevent resource leakage, destroy a buffer in time after use. |
| [int32_t OH_ScsiPeripheral_ParseBasicSenseInfo(uint8_t *senseData, uint8_t senseDataLen, ScsiPeripheral_BasicSenseInfo *senseInfo)](#oh_scsiperipheral_parsebasicsenseinfo) | Parses basic sense data, including the **Information**, **Command specific information**, and **Sense key specific** fields. |

## Function description

### OH_ScsiPeripheral_Init()

```c
int32_t OH_ScsiPeripheral_Init(void)
```

**Description**

Initializes the SCSI Peripheral DDK.

**Required permission**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link SCSIPERIPHERAL_DDK_SUCCESS}: The API call is successful.<br>    {@link SCSIPERIPHERAL_DDK_NO_PERM}: The permission verification fails.<br>    {@link SCSIPERIPHERAL_DDK_INIT_ERROR}: The DDK initialization fails.<br>    {@link SCSIPERIPHERAL_DDK_SERVICE_ERROR}: The communication with the DDK service fails. |

### OH_ScsiPeripheral_Release()

```c
int32_t OH_ScsiPeripheral_Release(void)
```

**Description**

Releases the SCSI Peripheral DDK.

**Required permission**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link SCSIPERIPHERAL_DDK_SUCCESS}: The API call is successful.<br>    {@link SCSIPERIPHERAL_DDK_NO_PERM}: The permission verification fails.<br>    {@link SCSIPERIPHERAL_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link SCSIPERIPHERAL_DDK_SERVICE_ERROR}: The communication with the DDK service fails. |

### OH_ScsiPeripheral_Open()

```c
int32_t OH_ScsiPeripheral_Open(uint64_t deviceId, uint8_t interfaceIndex, ScsiPeripheral_Device **dev)
```

**Description**

Opens the SCSI device specified by **deviceId** and **interfaceIndex**. The **deviceId** can be obtained by shifting the bus number of the USB device left by 32 bits and then performing a bitwise OR operation with the device address. **interfaceIndex** refers to the index of the USB interface to be opened.

**Required permission**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t deviceId | Device ID. |
| uint8_t interfaceIndex | Interface index for the API of the SCSI device. |
| ScsiPeripheral_Device **dev | Device handle. For details, see {@link ScsiPeripheral_Device}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link SCSIPERIPHERAL_DDK_SUCCESS}: The API call is successful.<br>    {@link SCSIPERIPHERAL_DDK_NO_PERM}: The permission verification fails.<br>    {@link SCSIPERIPHERAL_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_PARAMETER}: The input dev or dev is null.<br>    {@link SCSIPERIPHERAL_DDK_SERVICE_ERROR}: The communication with the DDK service fails.<br>    {@link SCSIPERIPHERAL_DDK_MEMORY_ERROR}: The memory operation fails.<br>    {@link SCSIPERIPHERAL_DDK_IO_ERROR}: An I/O error occurs.<br>    {@link SCSIPERIPHERAL_DDK_DEVICE_NOT_FOUND}: No device is found based on the specified deviceId and<br>    interfaceIndex.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_OPERATION}: The operation is not supported. |

### OH_ScsiPeripheral_Close()

```c
int32_t OH_ScsiPeripheral_Close(ScsiPeripheral_Device **dev)
```

**Description**

Closes the SCSI device.

**Required permission**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ScsiPeripheral_Device **dev | Device handle. For details, see {@link ScsiPeripheral_Device}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link SCSIPERIPHERAL_DDK_SUCCESS}: The API call is successful.<br>    {@link SCSIPERIPHERAL_DDK_NO_PERM}: The permission verification fails.<br>    {@link SCSIPERIPHERAL_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_PARAMETER}: The input dev or dev is null.<br>    {@link SCSIPERIPHERAL_DDK_SERVICE_ERROR}: The communication with the DDK service fails.<br>    {@link SCSIPERIPHERAL_DDK_IO_ERROR}: An I/O error occurs. |

### OH_ScsiPeripheral_TestUnitReady()

```c
int32_t OH_ScsiPeripheral_TestUnitReady(ScsiPeripheral_Device *dev, ScsiPeripheral_TestUnitReadyRequest *request, ScsiPeripheral_Response *response)
```

**Description**

Checks whether the logical unit is ready.

**Required permission**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ScsiPeripheral_Device *dev | Device handle. For details, see {@link ScsiPeripheral_Device}. |
| ScsiPeripheral_TestUnitReadyRequest *request | Request of the **test unit ready** command. For details, see {@link ScsiPeripheral_TestUnitReadyRequest}. |
| ScsiPeripheral_Response *response | Response returned by the **test unit ready** command. For details, see {@link ScsiPeripheral_Response}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link SCSIPERIPHERAL_DDK_SUCCESS}: The API call is successful.<br>    {@link SCSIPERIPHERAL_DDK_NO_PERM}: The permission verification fails.<br>    {@link SCSIPERIPHERAL_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_PARAMETER}: The input dev, request, or response is null.<br>    {@link SCSIPERIPHERAL_DDK_SERVICE_ERROR}: The communication with the DDK service fails.<br>    {@link SCSIPERIPHERAL_DDK_MEMORY_ERROR}: The memory operation fails.<br>    {@link SCSIPERIPHERAL_DDK_IO_ERROR}: An I/O error occurs.<br>    {@link SCSIPERIPHERAL_DDK_TIMEOUT}: The transmission times out.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_OPERATION}: The operation is not supported. |

### OH_ScsiPeripheral_Inquiry()

```c
int32_t OH_ScsiPeripheral_Inquiry(ScsiPeripheral_Device *dev, ScsiPeripheral_InquiryRequest *request, ScsiPeripheral_InquiryInfo *inquiryInfo, ScsiPeripheral_Response *response)
```

**Description**

Queries basic information about the SCSI device.

**Required permission**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ScsiPeripheral_Device *dev | Device handle. For details, see {@link ScsiPeripheral_Device}. |
| ScsiPeripheral_InquiryRequest *request | Request of the **inquiry** command. For details, see {@link ScsiPeripheral_InquiryRequest}. |
| ScsiPeripheral_InquiryInfo *inquiryInfo | Query result returned by the **inquiry** command. For details, see {@link ScsiPeripheral_InquiryInfo}. |
| ScsiPeripheral_Response *response | Raw response returned by the inquiry command. For details, see {@link ScsiPeripheral_Response}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link SCSIPERIPHERAL_DDK_SUCCESS}: The API call is successful.<br>    {@link SCSIPERIPHERAL_DDK_NO_PERM}: The permission verification fails.<br>    {@link SCSIPERIPHERAL_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_PARAMETER}: The input dev, request, inquiryInfo,<br>    inquiryInfo->data, or response is null.<br>    {@link SCSIPERIPHERAL_DDK_SERVICE_ERROR}: The communication with the DDK service fails.<br>    {@link SCSIPERIPHERAL_DDK_MEMORY_ERROR}: The memory operation fails.<br>    {@link SCSIPERIPHERAL_DDK_IO_ERROR}: An I/O error occurs.<br>    {@link SCSIPERIPHERAL_DDK_TIMEOUT}: The transmission times out.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_OPERATION}: The operation is not supported. |

### OH_ScsiPeripheral_ReadCapacity10()

```c
int32_t OH_ScsiPeripheral_ReadCapacity10(ScsiPeripheral_Device *dev, ScsiPeripheral_ReadCapacityRequest *request, ScsiPeripheral_CapacityInfo *capacityInfo, ScsiPeripheral_Response *response)
```

**Description**

Obtains the capacity information about the SCSI device.

**Required permission**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ScsiPeripheral_Device *dev | Device handle. For details, see {@link ScsiPeripheral_Device}. |
| ScsiPeripheral_ReadCapacityRequest *request | Request of the **read capacity** command. For details, see {@link ScsiPeripheral_ReadCapacityRequest}. |
| ScsiPeripheral_CapacityInfo *capacityInfo | Capacity information returned by the **read capacity** command. For details, see {@link ScsiPeripheral_CapacityInfo}. |
| ScsiPeripheral_Response *response | Original response returned by the **read capacity** command. For details, see {@link ScsiPeripheral_Response}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link SCSIPERIPHERAL_DDK_SUCCESS}: The API call is successful.<br>    {@link SCSIPERIPHERAL_DDK_NO_PERM}: The permission verification fails.<br>    {@link SCSIPERIPHERAL_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_PARAMETER}: The input dev, request, capacityInfo, or response<br>    is null.<br>    {@link SCSIPERIPHERAL_DDK_SERVICE_ERROR}: The communication with the DDK service fails.<br>    {@link SCSIPERIPHERAL_DDK_MEMORY_ERROR}: The memory operation fails.<br>    {@link SCSIPERIPHERAL_DDK_IO_ERROR}: An I/O error occurs.<br>    {@link SCSIPERIPHERAL_DDK_TIMEOUT}: The transmission times out.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_OPERATION}: The operation is not supported. |

### OH_ScsiPeripheral_RequestSense()

```c
int32_t OH_ScsiPeripheral_RequestSense(ScsiPeripheral_Device *dev, ScsiPeripheral_RequestSenseRequest *request, ScsiPeripheral_Response *response)
```

**Description**

Obtains sense data, that is, information returned by the SCSI device to the host to report the device status, error information, and diagnosis information.

**Required permission**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ScsiPeripheral_Device *dev | Device handle. For details, see {@link ScsiPeripheral_Device}. |
| ScsiPeripheral_RequestSenseRequest *request | Request of the **Request Sense** command. For details, see {@link ScsiPeripheral_RequestSenseRequest}. |
| ScsiPeripheral_Response *response | Response returned by the **Request Sense** command. For details, see {@link ScsiPeripheral_Response}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link SCSIPERIPHERAL_DDK_SUCCESS}: The API call is successful.<br>    {@link SCSIPERIPHERAL_DDK_NO_PERM}: The permission verification fails.<br>    {@link SCSIPERIPHERAL_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_PARAMETER}: The input dev, request, or response is null.<br>    {@link SCSIPERIPHERAL_DDK_SERVICE_ERROR}: The communication with the DDK service fails.<br>    {@link SCSIPERIPHERAL_DDK_MEMORY_ERROR}: The memory operation fails.<br>    {@link SCSIPERIPHERAL_DDK_IO_ERROR}: An I/O error occurs.<br>    {@link SCSIPERIPHERAL_DDK_TIMEOUT}: The transmission times out.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_OPERATION}: The operation is not supported. |

### OH_ScsiPeripheral_Read10()

```c
int32_t OH_ScsiPeripheral_Read10(ScsiPeripheral_Device *dev, ScsiPeripheral_IORequest *request, ScsiPeripheral_Response *response)
```

**Description**

Reads data from the specified logical block(s).

**Required permission**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ScsiPeripheral_Device *dev | Device handle. For details, see {@link ScsiPeripheral_Device}. |
| ScsiPeripheral_IORequest *request | Request of the **read** command. For details, see {@link ScsiPeripheral_IORequest}. |
| ScsiPeripheral_Response *response | Response returned by the **read** command. For details, see {@link ScsiPeripheral_Response}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link SCSIPERIPHERAL_DDK_SUCCESS}: The API call is successful.<br>    {@link SCSIPERIPHERAL_DDK_NO_PERM}: The permission verification fails.<br>    {@link SCSIPERIPHERAL_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_PARAMETER}: The input dev, request, request->data, or response<br>    is null.<br>    {@link SCSIPERIPHERAL_DDK_SERVICE_ERROR}: The communication with the DDK service fails.<br>    {@link SCSIPERIPHERAL_DDK_MEMORY_ERROR}: The memory operation fails.<br>    {@link SCSIPERIPHERAL_DDK_IO_ERROR}: An I/O error occurs.<br>    {@link SCSIPERIPHERAL_DDK_TIMEOUT}: The transmission times out.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_OPERATION}: The operation is not supported. |

### OH_ScsiPeripheral_Write10()

```c
int32_t OH_ScsiPeripheral_Write10(ScsiPeripheral_Device *dev, ScsiPeripheral_IORequest *request, ScsiPeripheral_Response *response)
```

**Description**

Writes data to the specified logical block(s) of a device.

**Required permission**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ScsiPeripheral_Device *dev | Device handle. For details, see {@link ScsiPeripheral_Device}. |
| ScsiPeripheral_IORequest *request | Request of the **write** command. For details, see {@link ScsiPeripheral_IORequest}. |
| ScsiPeripheral_Response *response | Response returned by the **write** command. For details, see {@link ScsiPeripheral_Response}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link SCSIPERIPHERAL_DDK_SUCCESS}: The API call is successful.<br>    {@link SCSIPERIPHERAL_DDK_NO_PERM}: The permission verification fails.<br>    {@link SCSIPERIPHERAL_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_PARAMETER}: The input dev, request, request->data, or response<br>    is null.<br>    {@link SCSIPERIPHERAL_DDK_SERVICE_ERROR}: The communication with the DDK service fails.<br>    {@link SCSIPERIPHERAL_DDK_MEMORY_ERROR}: The memory operation fails.<br>    {@link SCSIPERIPHERAL_DDK_IO_ERROR}: An I/O error occurs.<br>    {@link SCSIPERIPHERAL_DDK_TIMEOUT}: The transmission times out.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_OPERATION}: The operation is not supported. |

### OH_ScsiPeripheral_Verify10()

```c
int32_t OH_ScsiPeripheral_Verify10(ScsiPeripheral_Device *dev, ScsiPeripheral_VerifyRequest *request, ScsiPeripheral_Response *response)
```

**Description**

Verifies the specified logical block(s).

**Required permission**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ScsiPeripheral_Device *dev | Device handle. For details, see {@link ScsiPeripheral_Device}. |
| ScsiPeripheral_VerifyRequest *request | Request of the **verify** command. For details, see {@link ScsiPeripheral_VerifyRequest}. |
| ScsiPeripheral_Response *response | Response returned by the **verify** command. For details, see {@link ScsiPeripheral_Response}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link SCSIPERIPHERAL_DDK_SUCCESS}: The API call is successful.<br>    {@link SCSIPERIPHERAL_DDK_NO_PERM}: The permission verification fails.<br>    {@link SCSIPERIPHERAL_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_PARAMETER}: The input dev, request, or response is null.<br>    {@link SCSIPERIPHERAL_DDK_SERVICE_ERROR}: The communication with the DDK service fails.<br>    {@link SCSIPERIPHERAL_DDK_MEMORY_ERROR}: The memory operation fails.<br>    {@link SCSIPERIPHERAL_DDK_IO_ERROR}: An I/O error occurs.<br>    {@link SCSIPERIPHERAL_DDK_TIMEOUT}: The transmission times out.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_OPERATION}: The operation is not supported. |

### OH_ScsiPeripheral_SendRequestByCdb()

```c
int32_t OH_ScsiPeripheral_SendRequestByCdb(ScsiPeripheral_Device *dev, ScsiPeripheral_Request *request, ScsiPeripheral_Response *response)
```

**Description**

Sends SCSI commands in CDB mode.

**Required permission**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ScsiPeripheral_Device *dev | Device handle. For details, see {@link ScsiPeripheral_Device}. |
| ScsiPeripheral_Request *request | Request. For details, see {@link ScsiPeripheral_Request}. |
| ScsiPeripheral_Response *response | Response. For details, see {@link ScsiPeripheral_Response}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link SCSIPERIPHERAL_DDK_SUCCESS}: The API call is successful.<br>    {@link SCSIPERIPHERAL_DDK_NO_PERM}: The permission verification fails.<br>    {@link SCSIPERIPHERAL_DDK_INIT_ERROR}: The DDK is not initialized.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_PARAMETER}: The input dev, request, request->data, or response<br>    is null, or request->cdbLength is 0.<br>    {@link SCSIPERIPHERAL_DDK_SERVICE_ERROR}: The communication with the DDK service fails.<br>    {@link SCSIPERIPHERAL_DDK_MEMORY_ERROR}: The memory operation fails.<br>    {@link SCSIPERIPHERAL_DDK_IO_ERROR}: An I/O error occurs.<br>    {@link SCSIPERIPHERAL_DDK_TIMEOUT}: The transmission times out.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_OPERATION}: The operation is not supported. |

### OH_ScsiPeripheral_CreateDeviceMemMap()

```c
int32_t OH_ScsiPeripheral_CreateDeviceMemMap(ScsiPeripheral_Device *dev, size_t size, ScsiPeripheral_DeviceMemMap **devMmap)
```

**Description**

Creates a buffer. To avoid resource leakage, use [OH_ScsiPeripheral_DestroyDeviceMemMap](capi-scsi-peripheral-api-h.md#oh_scsiperipheral_destroydevicememmap) to destroy a buffer after use.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ScsiPeripheral_Device *dev | Device handle. For details, see {@link ScsiPeripheral_Device}. |
| size_t size | Buffer size. |
| ScsiPeripheral_DeviceMemMap **devMmap | Device memory mapping used to return the created buffer to the caller. For details, see {@link ScsiPeripheral_DeviceMemMap}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link SCSIPERIPHERAL_DDK_SUCCESS}: The API call is successful.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_PARAMETER}: The input dev, devMmap, or devMmap is null.<br>    {@link SCSIPERIPHERAL_DDK_MEMORY_ERROR}: The memory operation fails. |

### OH_ScsiPeripheral_DestroyDeviceMemMap()

```c
int32_t OH_ScsiPeripheral_DestroyDeviceMemMap(ScsiPeripheral_DeviceMemMap *devMmap)
```

**Description**

Destroys a buffer. To prevent resource leakage, destroy a buffer in time after use.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ScsiPeripheral_DeviceMemMap *devMmap | Buffer to be destroyed, which is created by calling [OH_ScsiPeripheral_CreateDeviceMemMap](capi-scsi-peripheral-api-h.md#oh_scsiperipheral_createdevicememmap). For details, see {@link ScsiPeripheral_DeviceMemMap}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link SCSIPERIPHERAL_DDK_SUCCESS}: The API call is successful.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_PARAMETER}: The input devMmap is null.<br>    {@link SCSIPERIPHERAL_DDK_MEMORY_ERROR}: The memory operation fails. |

### OH_ScsiPeripheral_ParseBasicSenseInfo()

```c
int32_t OH_ScsiPeripheral_ParseBasicSenseInfo(uint8_t *senseData, uint8_t senseDataLen, ScsiPeripheral_BasicSenseInfo *senseInfo)
```

**Description**

Parses basic sense data, including the **Information**, **Command specific information**, and **Sense key specific** fields.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint8_t *senseData | Sense data to be parsed. |
| uint8_t senseDataLen | Length of sense data. |
| ScsiPeripheral_BasicSenseInfo *senseInfo | Basic sense data after parsing. For details, see {@link ScsiPeripheral_BasicSenseInfo}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link SCSIPERIPHERAL_DDK_SUCCESS}: The API call is successful.<br>    {@link SCSIPERIPHERAL_DDK_INVALID_PARAMETER}: The input senseData is not a descriptor or is not of the fixed<br>    format, or senseDataLen is smaller than {@link SCSIPERIPHERAL_MIN_DESCRIPTOR_FORMAT_SENSE}<br>    or {@link SCSIPERIPHERAL_MIN_FIXED_FORMAT_SENSE}. |


