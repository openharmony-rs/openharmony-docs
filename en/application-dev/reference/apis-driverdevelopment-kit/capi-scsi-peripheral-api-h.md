# scsi_peripheral_api.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=b5aa01b6af5d19922ff7e85249d00c2a9af91e2a translatedAt=2026-11-10T01:11:21.495Z pushedAt=2026-11-10T01:42:29.615Z nl=1 -->

## Overview

Declares the SCSI Peripheral DDK APIs for accessing SCSI devices from the host side. This module is based on the SCSI protocol standard and provides SCSI device access capabilities through DDK driver services.

**File to include**: <scsi_peripheral/scsi_peripheral_api.h>

**Library**: libscsi.z.so

**System capability**: SystemCapability.Driver.SCSI.Extension

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [int32_t OH_ScsiPeripheral_Init(void)](#oh_scsiperipheral_init) | Initializes the SCSI Peripheral DDK. This method must be called before any other SCSI Peripheral DDK method. After use, OH_ScsiPeripheral_Release must be called to release resources; otherwise, a resource leak will occur. |
| [int32_t OH_ScsiPeripheral_Release(void)](#oh_scsiperipheral_release) | Releases the SCSI Peripheral DDK. You must first initialize it through OH_ScsiPeripheral_Init, and release it after the SCSI Peripheral DDK methods are no longer used, to avoid a resource leak. |
| [int32_t OH_ScsiPeripheral_Open(uint64_t deviceId, uint8_t interfaceIndex, ScsiPeripheral_Device **dev)](#oh_scsiperipheral_open) | Opens the SCSI device specified by deviceId and interfaceIndex. The deviceId can be obtained by shifting the bus number of the USB device left by 32 bits and then performing a bitwise OR operation with its device address. interfaceIndex is the index of the USB interface to be opened. After the device is used, OH_ScsiPeripheral_Close must be called to close the device and release resources; otherwise, a resource leak will occur. |
| [int32_t OH_ScsiPeripheral_Close(ScsiPeripheral_Device **dev)](#oh_scsiperipheral_close) | Closes the SCSI device, releases the device handle resource, and invalidates it. This method is used in pair with OH_ScsiPeripheral_Open. After the device is used, this method must be called to close the device and release resources; otherwise, a resource leak will occur. |
| [int32_t OH_ScsiPeripheral_TestUnitReady(ScsiPeripheral_Device *dev, ScsiPeripheral_TestUnitReadyRequest *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_testunitready) | Checks whether the logical unit is ready (a logical unit is an independently addressable I/O operation entity in a SCSI device). |
| [int32_t OH_ScsiPeripheral_Inquiry(ScsiPeripheral_Device *dev, ScsiPeripheral_InquiryRequest *request, ScsiPeripheral_InquiryInfo *inquiryInfo, ScsiPeripheral_Response *response)](#oh_scsiperipheral_inquiry) | Queries the basic information of the SCSI device. |
| [int32_t OH_ScsiPeripheral_ReadCapacity10(ScsiPeripheral_Device *dev, ScsiPeripheral_ReadCapacityRequest *request, ScsiPeripheral_CapacityInfo *capacityInfo, ScsiPeripheral_Response *response)](#oh_scsiperipheral_readcapacity10) | Obtains the capacity information of the SCSI device. |
| [int32_t OH_ScsiPeripheral_RequestSense(ScsiPeripheral_Device *dev, ScsiPeripheral_RequestSenseRequest *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_requestsense) | Obtains the sense data (information returned by the SCSI device to the host, used to report the device status, error information, and diagnostic information). |
| [int32_t OH_ScsiPeripheral_Read10(ScsiPeripheral_Device *dev, ScsiPeripheral_IORequest *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_read10) | Reads data from the specified logical block. |
| [int32_t OH_ScsiPeripheral_Write10(ScsiPeripheral_Device *dev, ScsiPeripheral_IORequest *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_write10) | Writes data to the specified logical block of the device. |
| [int32_t OH_ScsiPeripheral_Verify10(ScsiPeripheral_Device *dev, ScsiPeripheral_VerifyRequest *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_verify10) | Verifies the specified logical block. |
| [int32_t OH_ScsiPeripheral_SendRequestByCdb(ScsiPeripheral_Device *dev, ScsiPeripheral_Request *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_sendrequestbycdb) | Sends a SCSI command in the form of a CDB (Command Descriptor Block). |
| [int32_t OH_ScsiPeripheral_CreateDeviceMemMap(ScsiPeripheral_Device *dev, size_t size, ScsiPeripheral_DeviceMemMap **devMmap)](#oh_scsiperipheral_createdevicememmap) | Creates a buffer. After the buffer is used, call [OH_ScsiPeripheral_DestroyDeviceMemMap()](#oh_scsiperipheral_destroydevicememmap) to destroy the buffer; otherwise, a resource leak will occur. |
| [int32_t OH_ScsiPeripheral_DestroyDeviceMemMap(ScsiPeripheral_DeviceMemMap *devMmap)](#oh_scsiperipheral_destroydevicememmap) | Destroys a buffer. To prevent resource leakage, destroy a buffer in time after use.|
| [int32_t OH_ScsiPeripheral_ParseBasicSenseInfo(uint8_t *senseData, uint8_t senseDataLen, ScsiPeripheral_BasicSenseInfo *senseInfo)](#oh_scsiperipheral_parsebasicsenseinfo) | Parses the basic sense data, including the Information, Command specific information, and Sense key specific fields. |

## Function Description

### OH_ScsiPeripheral_Init()

```c
int32_t OH_ScsiPeripheral_Init(void)
```

**Description**

Initializes the SCSI Peripheral DDK. This method must be called before any other SCSI Peripheral DDK method. After use, OH_ScsiPeripheral_Release must be called to release resources; otherwise, a resource leak will occur.

**Required permissions**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) The interface is called successfully.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Permission verification failed. Ensure that the application has obtained the ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Failed to initialize the DDK.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Failed to communicate with the DDK service. Check whether the DDK service is initialized and running normally. |

### OH_ScsiPeripheral_Release()

```c
int32_t OH_ScsiPeripheral_Release(void)
```

**Description**

Releases the SCSI Peripheral DDK. You must first initialize it through OH_ScsiPeripheral_Init, and release it after the SCSI Peripheral DDK methods are no longer used, to avoid a resource leak.

**Required permissions**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_SUCCESS if the interface is called successfully.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_NO_PERM if permission verification fails. Ensure that the application has obtained the ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_INIT_ERROR if the DDK is uninitialized or DDK initialization fails.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_SERVICE_ERROR if communication with the DDK service fails. Check whether the DDK service is initialized and running normally. |

### OH_ScsiPeripheral_Open()

```c
int32_t OH_ScsiPeripheral_Open(uint64_t deviceId, uint8_t interfaceIndex, ScsiPeripheral_Device **dev)
```

**Description**

Opens the SCSI device specified by deviceId and interfaceIndex. The deviceId can be obtained by shifting the bus number of the USB device left by 32 bits and then performing a bitwise OR operation with its device address. interfaceIndex is the index of the USB interface to be opened. After the device is used, OH_ScsiPeripheral_Close must be called to close the device and release resources; otherwise, a resource leak will occur.

**Required permissions**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18


**Parameters**

| Name                            | Description|
|---------------------------------| -- |
| uint64_t deviceId               | Device ID, which represents the device to operate. It can be obtained by calling [OH_Usb_GetDevices](capi-usb-ddk-api-h.md#oh_usb_getdevices). |
| uint8_t interfaceIndex          |  Interface index, which is the index of the USB interface corresponding to the SCSI device to open. |
| [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md) **dev | Device handle. For details, see [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) The interface is called successfully.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Permission verification failed. Ensure that the application has obtained the ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) The DDK is not initialized. Call OH_ScsiPeripheral_Init to initialize it first.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) dev is null or *dev is null. Check whether the pointer parameter is correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Failed to communicate with the DDK service. Check whether the DDK service is initialized and running normally.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Memory operation failed. Check the memory status and whether an out-of-bounds operation exists.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) An I/O error occurred in the DDK. Check whether the device status is normal and the parameters are correct.<br>         [SCSIPERIPHERAL_DDK_DEVICE_NOT_FOUND](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) The device cannot be found by deviceId and interfaceIndex.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) The operation is not supported. Check the device specification and status.|

### OH_ScsiPeripheral_Close()

```c
int32_t OH_ScsiPeripheral_Close(ScsiPeripheral_Device **dev)
```

**Description**

Closes the SCSI device, releases the device handle resource, and invalidates it. This method is used in pair with OH_ScsiPeripheral_Open. After the device is used, this method must be called to close the device and release resources; otherwise, a resource leak will occur.

**Required permissions**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md) **dev | Device handle. For details, see [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) The interface is called successfully.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Permission verification failed. Ensure that the application has obtained the ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) The DDK is not initialized. Call OH_ScsiPeripheral_Init to initialize it first.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) dev is null or *dev is null. Check whether the pointer parameter is correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Failed to communicate with the DDK service. Check whether the DDK service is initialized and running properly.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) An I/O error occurred in the DDK. Check whether the device status is normal and the parameters are correct. |

### OH_ScsiPeripheral_TestUnitReady()

```c
int32_t OH_ScsiPeripheral_TestUnitReady(ScsiPeripheral_Device *dev, ScsiPeripheral_TestUnitReadyRequest *request, ScsiPeripheral_Response *response)
```

**Description**

Checks whether the logical unit is ready (a logical unit is an independently addressable I/O operation entity in a SCSI device).

**Required permissions**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18


**Parameters**

| Name                                                                                        | Description                                                                                                                    |
|---------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md) *dev                                                                  | Device handle. For details, see [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md).                                                                               |
| [ScsiPeripheral_TestUnitReadyRequest](capi-scsiperipheralddk-scsiperipheral-testunitreadyrequest.md) *request | Request of the **test unit ready** command. For details, see [ScsiPeripheral_TestUnitReadyRequest](capi-scsiperipheralddk-scsiperipheral-testunitreadyrequest.md).|
| [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md) *response      | Response returned by the **test unit ready** command. For details, see [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md).      |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_SUCCESS if the interface is called successfully.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_NO_PERM if permission verification fails. Ensure the application has been correctly granted the ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_INIT_ERROR if the DDK is uninitialized. Call OH_ScsiPeripheral_Init first to initialize it.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_INVALID_PARAMETER if dev is null, request is null, or response is null. Check whether the pointer parameters are correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_SERVICE_ERROR if service communication with the DDK fails. Check whether the DDK service has been initialized and runs normally.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_MEMORY_ERROR if a memory operation fails. Check the memory status and whether there is an out-of-bounds operation.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_IO_ERROR if an I/O error occurs in the DDK. Check whether the device status is normal and whether the parameters are correct.<br>         [SCSIPERIPHERAL_DDK_TIMEOUT](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_TIMEOUT if a transmission timeout occurs. Check the device status, or appropriately increase the timeout duration.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_INVALID_OPERATION if the operation is not supported. Check the device specifications and status. |

### OH_ScsiPeripheral_Inquiry()

```c
int32_t OH_ScsiPeripheral_Inquiry(ScsiPeripheral_Device *dev, ScsiPeripheral_InquiryRequest *request, ScsiPeripheral_InquiryInfo *inquiryInfo, ScsiPeripheral_Response *response)
```

**Description**

Queries basic information about the SCSI device.

**Required permissions**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18


**Parameters**

| Name                                                                                   | Description                                                                                                  |
|----------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md) *dev                                                             | Device handle. For details, see [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md).                                                             |
| [ScsiPeripheral_InquiryRequest](capi-scsiperipheralddk-scsiperipheral-inquiryrequest.md) *request        | Request of the **inquiry** command. For details, see [ScsiPeripheral_InquiryRequest](capi-scsiperipheralddk-scsiperipheral-inquiryrequest.md).          |
| [ScsiPeripheral_InquiryInfo](capi-scsiperipheralddk-scsiperipheral-inquiryinfo.md) *inquiryInfo          | Query result returned by the **inquiry** command. For details, see [ScsiPeripheral_InquiryInfo](capi-scsiperipheralddk-scsiperipheral-inquiryinfo.md).              |
| [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md) *response | Raw response returned by the inquiry command. For details, see [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_SUCCESS if the interface is called successfully.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_NO_PERM if permission verification fails. Ensure that the application has obtained the ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_INIT_ERROR if the DDK is uninitialized. Call OH_ScsiPeripheral_Init to initialize it first.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_INVALID_PARAMETER if dev, request, inquiryInfo, inquiryInfo->data, or response is null. Check whether the pointer parameters are correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_SERVICE_ERROR if communication with the DDK service fails. Check whether the DDK service is initialized and running normally.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_MEMORY_ERROR if a memory operation fails. Check the memory status and whether any out-of-bounds operation exists.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_IO_ERROR if an I/O error occurs in the DDK. Check whether the device status is normal and whether the parameters are correct.<br>         [SCSIPERIPHERAL_DDK_TIMEOUT](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_TIMEOUT if a transmission timeout occurs. Check the device status or increase the timeout duration appropriately.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_INVALID_OPERATION if the operation is not supported. Check the device specification and status. |

### OH_ScsiPeripheral_ReadCapacity10()

```c
int32_t OH_ScsiPeripheral_ReadCapacity10(ScsiPeripheral_Device *dev, ScsiPeripheral_ReadCapacityRequest *request, ScsiPeripheral_CapacityInfo *capacityInfo, ScsiPeripheral_Response *response)
```

**Description**

Obtains the capacity information about the SCSI device.

**Required permissions**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18


**Parameters**

| Name                                                                                      | Description                                                                                                        |
|-------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md) *dev                                                                | Device handle. For details, see [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md).                                                                   |
| [ScsiPeripheral_ReadCapacityRequest](capi-scsiperipheralddk-scsiperipheral-readcapacityrequest.md) *request | Request of the **read capacity** command. For details, see [ScsiPeripheral_ReadCapacityRequest](capi-scsiperipheralddk-scsiperipheral-readcapacityrequest.md).|
| [ScsiPeripheral_CapacityInfo](capi-scsiperipheralddk-scsiperipheral-capacityinfo.md) *capacityInfo          | Capacity information returned by the **read capacity** command. For details, see [ScsiPeripheral_CapacityInfo](capi-scsiperipheralddk-scsiperipheral-capacityinfo.md).            |
| [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md) *response    | Original response returned by the **read capacity** command. For details, see [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) The interface is called successfully.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Permission verification failed. Ensure that the application has obtained the ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) The DDK is uninitialized. Call OH_ScsiPeripheral_Init to initialize it first.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) dev, request, capacityInfo, or response is null. Check whether the pointer parameters are correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Failed to communicate with the DDK service. Check whether the DDK service is initialized and running normally.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Memory operation failed. Check the memory status and whether any out-of-bounds operation exists.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) An I/O error occurred in the DDK. Check whether the device status is normal and whether the parameters are correct.<br>         [SCSIPERIPHERAL_DDK_TIMEOUT](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Transmission timeout. Check the device status or increase the timeout duration appropriately.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) The operation is not supported. Check the device specification and status. |

### OH_ScsiPeripheral_RequestSense()

```c
int32_t OH_ScsiPeripheral_RequestSense(ScsiPeripheral_Device *dev, ScsiPeripheral_RequestSenseRequest *request, ScsiPeripheral_Response *response)
```

**Description**

Obtains the sense data (information returned by the SCSI device to the host, used to report the device status, error information, and diagnostic information).

**Required permissions**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18


**Parameters**

| Name                                                                                      | Description                                                                                                        |
|-------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md) *dev                                                                | Device handle. For details, see [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md).                                                                   |
| [ScsiPeripheral_RequestSenseRequest](capi-scsiperipheralddk-scsiperipheral-requestsenserequest.md) *request | Request of the **Request Sense** command. For details, see [ScsiPeripheral_RequestSenseRequest](capi-scsiperipheralddk-scsiperipheral-requestsenserequest.md).|
| [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md) *response    | Response returned by the **Request Sense** command. For details, see [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md).  |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns this code if the interface is called successfully.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns this code if permission verification fails. Ensure that the application has obtained the ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns this code if the DDK is uninitialized. Call OH_ScsiPeripheral_Init to initialize it first.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns this code if dev, request, or response is null. Check whether the pointer parameters are correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns this code if communication with the DDK service fails. Check whether the DDK service is initialized and in normal operation.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns this code if a memory operation fails. Check the memory status and whether an out-of-bounds operation exists.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns this code if an I/O error occurs in the DDK. Check whether the device status is normal and whether the parameters are correct.<br>         [SCSIPERIPHERAL_DDK_TIMEOUT](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns this code if a transmission timeout occurs. Check the device status or increase the timeout duration appropriately.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns this code if the operation is not supported. Check the device specification and status. |

### OH_ScsiPeripheral_Read10()

```c
int32_t OH_ScsiPeripheral_Read10(ScsiPeripheral_Device *dev, ScsiPeripheral_IORequest *request, ScsiPeripheral_Response *response)
```

**Description**

Reads data from the specified logical block(s).

**Required permissions**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18


**Parameters**

| Name                                                                                    | Description                                                                                             |
|-----------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md) *dev                                                              | Device handle. For details, see [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md).                                                        |
| [ScsiPeripheral_IORequest](capi-scsiperipheralddk-scsiperipheral-iorequest.md) *request | Request of the **read** command. For details, see [ScsiPeripheral_IORequest](capi-scsiperipheralddk-scsiperipheral-iorequest.md).|
| [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md) *response  | Response returned by the **read** command. For details, see [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_SUCCESS if the interface is called successfully.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_NO_PERM if permission verification fails. Ensure the application has been correctly granted the ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_INIT_ERROR if the DDK is uninitialized. Call OH_ScsiPeripheral_Init first to initialize it.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_INVALID_PARAMETER if dev is null, request is null, or request->data or response is null. Check whether the pointer parameter is correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_SERVICE_ERROR if service communication with the DDK fails. Check whether the DDK service has been initialized and runs normally.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_MEMORY_ERROR if a memory operation fails. Check the memory status and whether there is an out-of-bounds operation.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_IO_ERROR if an I/O error occurs in the DDK. Check whether the device status is normal and whether the parameter is correct.<br>         [SCSIPERIPHERAL_DDK_TIMEOUT](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_TIMEOUT if a transmission timeout occurs. Check the device status or appropriately increase the timeout duration.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_INVALID_OPERATION if the operation is not supported. Check the device specifications and status. |

### OH_ScsiPeripheral_Write10()

```c
int32_t OH_ScsiPeripheral_Write10(ScsiPeripheral_Device *dev, ScsiPeripheral_IORequest *request, ScsiPeripheral_Response *response)
```

**Description**

Writes data to the specified logical block(s) of a device.

**Required permissions**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18


**Parameters**

| Name                                                                                    | Description                                                                                              |
|-----------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md) *dev                                                              | Device handle. For details, see [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md).                                                         |
| [ScsiPeripheral_IORequest](capi-scsiperipheralddk-scsiperipheral-iorequest.md) *request | Request of the **write** command. For details, see [ScsiPeripheral_IORequest](capi-scsiperipheralddk-scsiperipheral-iorequest.md).|
| [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md) *response  | Response returned by the **write** command. For details, see [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_SUCCESS if the interface is called successfully.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_NO_PERM if permission verification fails. Ensure the application has been correctly granted the ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_INIT_ERROR if the DDK is uninitialized. Call OH_ScsiPeripheral_Init first to initialize it.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_INVALID_PARAMETER if dev is null, request is null, request->data is null, or response is null. Check whether the pointer parameters are correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_SERVICE_ERROR if communication with the DDK service fails. Check whether the DDK service has been initialized and runs normally.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_MEMORY_ERROR if a memory operation fails. Check the memory status and whether there is an out-of-bounds operation.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_IO_ERROR if an I/O error occurs in the DDK. Check whether the device status is normal and whether the parameters are correct.<br>         [SCSIPERIPHERAL_DDK_TIMEOUT](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_TIMEOUT if a transmission timeout occurs. Check the device status or appropriately increase the timeout duration.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Returns SCSIPERIPHERAL_DDK_INVALID_OPERATION if the operation is not supported. Check the device specifications and status. |

### OH_ScsiPeripheral_Verify10()

```c
int32_t OH_ScsiPeripheral_Verify10(ScsiPeripheral_Device *dev, ScsiPeripheral_VerifyRequest *request, ScsiPeripheral_Response *response)
```

**Description**

Verifies the specified logical block(s).

**Required permissions**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18


**Parameters**

| Name                                                                                   | Description                                                                                               |
|----------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md) *dev                                                             | Device handle. For details, see [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md).                                                          |
| [ScsiPeripheral_VerifyRequest](capi-scsiperipheralddk-scsiperipheral-verifyrequest.md) *request          | Request of the **verify** command. For details, see [ScsiPeripheral_VerifyRequest](capi-scsiperipheralddk-scsiperipheral-verifyrequest.md).          |
| [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md) *response | Response returned by the **verify** command. For details, see [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) The interface is called successfully.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Permission verification failed. Ensure the application has been correctly granted the ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) The DDK is uninitialized. Call OH_ScsiPeripheral_Init first to initialize it.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) dev is null, request is null, or response is null. Check whether the pointer parameters are correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Failed to communicate with the DDK service. Check whether the DDK service is initialized and runs normally.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Memory operation failed. Check the memory status and whether there is an out-of-bounds operation.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) An I/O error occurred in the DDK. Check whether the device status is normal and whether the parameters are correct.<br>         [SCSIPERIPHERAL_DDK_TIMEOUT](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Transmission timeout. Check the device status or appropriately increase the timeout duration.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) The DDK does not support this operation. Check the device specifications and status. |

### OH_ScsiPeripheral_SendRequestByCdb()

```c
int32_t OH_ScsiPeripheral_SendRequestByCdb(ScsiPeripheral_Device *dev, ScsiPeripheral_Request *request, ScsiPeripheral_Response *response)
```

**Description**

Sends a SCSI command in the form of a CDB (Command Descriptor Block).

**Required permissions**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18


**Parameters**

| Name                                                                                   | Description                                                                                  |
|----------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md) *dev                                                             | Device handle. For details, see [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md).                                             |
| [ScsiPeripheral_Request](capi-scsiperipheralddk-scsiperipheral-request.md) *request    | Pointer to the CDB request. For details, see [ScsiPeripheral_Request](capi-scsiperipheralddk-scsiperipheral-request.md). When calling this API, ensure that the data field is not empty and the cdbLength field is not 0.   |
| [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md) *response | Pointer to the CDB response. For details, see [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md). |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) The interface is called successfully.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Permission verification failed. Ensure that the application has obtained the ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) The DDK is uninitialized. Call OH_ScsiPeripheral_Init to initialize it first.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) dev is null, request is null, request->data is<br>         null, request->cdbLength is 0, or response is null. Check whether the pointer parameters are correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Failed to communicate with the DDK service. Check whether the DDK service is initialized and running normally.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Memory operation failed. Check the memory status and whether there is an out-of-bounds operation.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) An I/O error occurred in the DDK. Check whether the device status is normal and whether the parameters are correct.<br>         [SCSIPERIPHERAL_DDK_TIMEOUT](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) Transmission timeout. Check the device status or increase the timeout duration appropriately.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) The operation is not supported. Check the device specification and status. |

### OH_ScsiPeripheral_CreateDeviceMemMap()

```c
int32_t OH_ScsiPeripheral_CreateDeviceMemMap(ScsiPeripheral_Device *dev, size_t size, ScsiPeripheral_DeviceMemMap **devMmap)
```

**Description**

Creates a buffer. After the buffer is used, call [OH_ScsiPeripheral_DestroyDeviceMemMap()](#oh_scsiperipheral_destroydevicememmap) to destroy the buffer; otherwise, a resource leak will occur.

**Since**: 18


**Parameters**

| Parameter | Description |
|------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md) *dev  | Device handle. For details, see [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md).   |
| size_t size | Size of the buffer, in bytes.|
| [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md) **devMmap | The created buffer is returned to the caller through this parameter. For details, see [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md). |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) The interface is called successfully.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) dev is null, devMmap is null, or *devMmap is null. Check whether the pointer parameters are correct.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) A memory operation fails. Check the memory status and whether an out-of-bounds operation exists. |

### OH_ScsiPeripheral_DestroyDeviceMemMap()

```c
int32_t OH_ScsiPeripheral_DestroyDeviceMemMap(ScsiPeripheral_DeviceMemMap *devMmap)
```

**Description**

Destroys a buffer. To prevent resource leakage, destroy a buffer in time after use.

**Since**: 18


**Parameters**

| Name                                                                                          | Description                                                                                                                                                                               |
|-----------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md) *devMmap | Pointer to the buffer to be destroyed, which is created by [OH_ScsiPeripheral_CreateDeviceMemMap()](#oh_scsiperipheral_createdevicememmap). |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) if the interface is called successfully.<br>         Returns [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) if devMmap is null. Check whether the pointer parameter is correct.<br>         Returns [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) if a memory operation fails. Check the memory status and whether an out-of-bounds operation exists. |

### OH_ScsiPeripheral_ParseBasicSenseInfo()

```c
int32_t OH_ScsiPeripheral_ParseBasicSenseInfo(uint8_t *senseData, uint8_t senseDataLen, ScsiPeripheral_BasicSenseInfo *senseInfo)
```

**Description**

Parses the basic sense data, including the Information, Command specific information, and Sense key specific fields.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| uint8_t *senseData | Pointer to the Sense Data to be parsed. |
| uint8_t senseDataLen | Length of the Sense Data, that is, the length of the data pointed to by the senseData parameter, in bytes. |
| [ScsiPeripheral_BasicSenseInfo](capi-scsiperipheralddk-scsiperipheral-basicsenseinfo.md) *senseInfo | Basic sense data after parsing. For details, see [ScsiPeripheral_BasicSenseInfo](capi-scsiperipheralddk-scsiperipheral-basicsenseinfo.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) if the interface is called successfully.<br>         Returns [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode) if the senseData format is neither descriptor nor fixed format, or senseDataLen is less than<br>         [SCSIPERIPHERAL_MIN_DESCRIPTOR_FORMAT_SENSE](capi-scsi-peripheral-types-h.md#macros) or senseDataLen is less than [SCSIPERIPHERAL_MIN_FIXED_FORMAT_SENSE](capi-scsi-peripheral-types-h.md#macros). |


