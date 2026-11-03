# scsi_peripheral_api.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

## Overview

Declares the SCSI Peripheral DDK APIs used by the host to access the SCSI device. This module provides the SCSI device access capability through the DDK driver service based on the SCSI protocol.

**File to include**: <scsi_peripheral/scsi_peripheral_api.h>

**Library**: libscsi.z.so

**System capability**: SystemCapability.Driver.SCSI.Extension

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [int32_t OH_ScsiPeripheral_Init(void)](#oh_scsiperipheral_init) | Initializes the SCSI Peripheral DDK. This method must be called before all other SCSI Peripheral DDK methods. After using the method, you must call **OH_ScsiPeripheral_Release** to release resources. Otherwise, resource leaks may occur.|
| [int32_t OH_ScsiPeripheral_Release(void)](#oh_scsiperipheral_release) | Releases the SCSI Peripheral DDK. You must call **OH_ScsiPeripheral_Init** to initialize the SCSI Peripheral DDK and call this method to release resources when it is no longer used to avoid resource leaks.|
| [int32_t OH_ScsiPeripheral_Open(uint64_t deviceId, uint8_t interfaceIndex, ScsiPeripheral_Device **dev)](#oh_scsiperipheral_open) | Opens the SCSI device specified by **deviceId** and **interfaceIndex**. The **deviceId** can be obtained by shifting the bus number of the USB device left by 32 bits and then performing a bitwise OR operation with the device address. **interfaceIndex** refers to the index of the USB interface to be opened. After using the device, you must call **OH_ScsiPeripheral_Close** to close the device and release resources. Otherwise, resource leaks may occur.|
| [int32_t OH_ScsiPeripheral_Close(ScsiPeripheral_Device **dev)](#oh_scsiperipheral_close) | Closes the SCSI device, releases the device handle resources, and invalidates the handle. This API is used together with **OH_ScsiPeripheral_Open**. After using the device, you must call this API to close the device and release resources. Otherwise, resource leaks may occur.|
| [int32_t OH_ScsiPeripheral_TestUnitReady(ScsiPeripheral_Device *dev, ScsiPeripheral_TestUnitReadyRequest *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_testunitready) | Checks whether the logical unit is ready. A logical unit is an I/O operation entity that can be independently addressed in a SCSI device.|
| [int32_t OH_ScsiPeripheral_Inquiry(ScsiPeripheral_Device *dev, ScsiPeripheral_InquiryRequest *request, ScsiPeripheral_InquiryInfo *inquiryInfo, ScsiPeripheral_Response *response)](#oh_scsiperipheral_inquiry) | Queries basic information about the SCSI device.|
| [int32_t OH_ScsiPeripheral_ReadCapacity10(ScsiPeripheral_Device *dev, ScsiPeripheral_ReadCapacityRequest *request, ScsiPeripheral_CapacityInfo *capacityInfo, ScsiPeripheral_Response *response)](#oh_scsiperipheral_readcapacity10) | Obtains the capacity information about the SCSI device.|
| [int32_t OH_ScsiPeripheral_RequestSense(ScsiPeripheral_Device *dev, ScsiPeripheral_RequestSenseRequest *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_requestsense) | Obtains sense data, that is, information returned by the SCSI device to the host, which is used to report the device status, error information, and diagnosis information.|
| [int32_t OH_ScsiPeripheral_Read10(ScsiPeripheral_Device *dev, ScsiPeripheral_IORequest *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_read10) | Reads data from the specified logical block(s).|
| [int32_t OH_ScsiPeripheral_Write10(ScsiPeripheral_Device *dev, ScsiPeripheral_IORequest *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_write10) | Writes data to the specified logical block(s) of a device.|
| [int32_t OH_ScsiPeripheral_Verify10(ScsiPeripheral_Device *dev, ScsiPeripheral_VerifyRequest *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_verify10) | Verifies the specified logical block(s).|
| [int32_t OH_ScsiPeripheral_SendRequestByCdb(ScsiPeripheral_Device *dev, ScsiPeripheral_Request *request, ScsiPeripheral_Response *response)](#oh_scsiperipheral_sendrequestbycdb) | Sends SCSI commands in CDB mode.|
| [int32_t OH_ScsiPeripheral_CreateDeviceMemMap(ScsiPeripheral_Device *dev, size_t size, ScsiPeripheral_DeviceMemMap **devMmap)](#oh_scsiperipheral_createdevicememmap) | Creates a buffer. To avoid memory leakage, use [OH_ScsiPeripheral_DestroyDeviceMemMap](#oh_scsiperipheral_destroydevicememmap) to destroy a buffer after use.|
| [int32_t OH_ScsiPeripheral_DestroyDeviceMemMap(ScsiPeripheral_DeviceMemMap *devMmap)](#oh_scsiperipheral_destroydevicememmap) | Destroys a buffer. To prevent resource leakage, destroy a buffer in time after use.|
| [int32_t OH_ScsiPeripheral_ParseBasicSenseInfo(uint8_t *senseData, uint8_t senseDataLen, ScsiPeripheral_BasicSenseInfo *senseInfo)](#oh_scsiperipheral_parsebasicsenseinfo) | Parses basic sense data, including the **Information**, **Command specific information**, and **Sense key specific** fields.|

## Function Description

### OH_ScsiPeripheral_Init()

```c
int32_t OH_ScsiPeripheral_Init(void)
```

**Description**

Initializes the SCSI Peripheral DDK. This method must be called before all other SCSI Peripheral DDK methods. After using the method, you must call **OH_ScsiPeripheral_Release** to release resources. Otherwise, resource leaks may occur.

**Required permissions**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The API call is successful.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The permission verification fails. Ensure that you have obtained the **ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL** permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The DDK initialization fails.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The communication with the DDK service fails. Check whether the DDK service is initialized and running properly.|

### OH_ScsiPeripheral_Release()

```c
int32_t OH_ScsiPeripheral_Release(void)
```

**Description**

Releases the SCSI Peripheral DDK. You must call **OH_ScsiPeripheral_Init** to initialize the SCSI Peripheral DDK and call this method to release resources when it is no longer used to avoid resource leaks.

**Required permissions**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The API call is successful.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The permission verification fails. Ensure that you have obtained the **ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL** permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The DDK is not initialized or the DDK initialization fails.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The communication with the DDK service fails. Check whether the DDK service is initialized and running properly.|

### OH_ScsiPeripheral_Open()

```c
int32_t OH_ScsiPeripheral_Open(uint64_t deviceId, uint8_t interfaceIndex, ScsiPeripheral_Device **dev)
```

**Description**

Opens the SCSI device specified by **deviceId** and **interfaceIndex**. The **deviceId** can be obtained by shifting the bus number of the USB device left by 32 bits and then performing a bitwise OR operation with the device address. **interfaceIndex** refers to the index of the USB interface to be opened. After using the device, you must call **OH_ScsiPeripheral_Close** to close the device and release resources. Otherwise, resource leaks may occur.

**Required permissions**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18


**Parameters**

| Name                            | Description|
|---------------------------------| -- |
| uint64_t deviceId               | ID of the device to be operated, which can be obtained by calling [OH_Usb_GetDevices](capi-usb-ddk-api-h.md#oh_usb_getdevices).|
| uint8_t interfaceIndex          |  Interface index, which is the index of the USB interface corresponding to the SCSI device to be opened.|
| [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md) **dev | Device handle. For details, see [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The API call is successful.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The permission verification fails. Ensure that you have obtained the **ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL** permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The DDK is not initialized. Call **OH_ScsiPeripheral_Init** to complete the initialization first.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The input **dev** or ***dev** is null. Check whether the pointer parameter is correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The communication with the DDK service fails. Check whether the DDK service is initialized and running properly.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The memory operation fails. Check the memory status and whether there are out-of-bounds operations.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): An I/O error occurs. Check whether the device status is normal and whether the parameters are correct.<br>         [SCSIPERIPHERAL_DDK_DEVICE_NOT_FOUND](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): No device is found based on the specified **deviceId** and **interfaceIndex**.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The operation is not supported. Check the device specifications and status.|

### OH_ScsiPeripheral_Close()

```c
int32_t OH_ScsiPeripheral_Close(ScsiPeripheral_Device **dev)
```

**Description**

Closes the SCSI device, releases the device handle resources, and invalidates the handle. This API is used together with **OH_ScsiPeripheral_Open**. After using the device, you must call this API to close the device and release resources. Otherwise, resource leaks may occur.

**Required permissions**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md) **dev | Device handle. For details, see [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The API call is successful.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The permission verification fails. Ensure that you have obtained the **ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL** permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The DDK is not initialized. Call **OH_ScsiPeripheral_Init** to complete the initialization first.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The input **dev** or ***dev** is null. Check whether the pointer parameter is correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The communication with the DDK service fails. Check whether the DDK service is initialized and running properly.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): An I/O error occurs. Check whether the device status is normal and whether the parameters are correct.|

### OH_ScsiPeripheral_TestUnitReady()

```c
int32_t OH_ScsiPeripheral_TestUnitReady(ScsiPeripheral_Device *dev, ScsiPeripheral_TestUnitReadyRequest *request, ScsiPeripheral_Response *response)
```

**Description**

Checks whether the logical unit is ready. A logical unit is an I/O operation entity that can be independently addressed in a SCSI device.

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
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The API call is successful.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The permission verification fails. Ensure that you have obtained the **ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL** permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The DDK is not initialized. Call **OH_ScsiPeripheral_Init** to complete the initialization first.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The input **dev**, **request**, or **response** is null. Check whether the pointer parameter is correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The communication with the DDK service fails. Check whether the DDK service is initialized and running properly.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The memory operation fails. Check the memory status and whether there are out-of-bounds operations.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): An I/O error occurs. Check whether the device status is normal and whether the parameters are correct.<br>         [SCSIPERIPHERAL_DDK_TIMEOUT](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The transmission times out. Check the device status or increase the timeout interval.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The operation is not supported. Check the device specifications and status.|

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
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The API call is successful.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The permission verification fails. Ensure that you have obtained the **ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL** permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The DDK is not initialized. Call **OH_ScsiPeripheral_Init** to complete the initialization first.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The input **dev**, **request**, **inquiryInfo**, **inquiryInfo->data**, or **response** is null. Check whether the pointer parameter is correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The communication with the DDK service fails. Check whether the DDK service is initialized and running properly.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The memory operation fails. Check the memory status and whether there are out-of-bounds operations.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): An I/O error occurs. Check whether the device status is normal and whether the parameters are correct.<br>         [SCSIPERIPHERAL_DDK_TIMEOUT](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The transmission times out. Check the device status or increase the timeout interval.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The operation is not supported. Check the device specifications and status.|

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
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The API call is successful.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The permission verification fails. Ensure that you have obtained the **ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL** permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The DDK is not initialized. Call **OH_ScsiPeripheral_Init** to complete the initialization first.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The input **dev**, **request**, **capacityInfo**, or **response** is null. Check whether the pointer parameter is correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The communication with the DDK service fails. Check whether the DDK service is initialized and running properly.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The memory operation fails. Check the memory status and whether there are out-of-bounds operations.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): An I/O error occurs. Check whether the device status is normal and whether the parameters are correct.<br>         [SCSIPERIPHERAL_DDK_TIMEOUT](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The transmission times out. Check the device status or increase the timeout interval.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The operation is not supported. Check the device specifications and status.|

### OH_ScsiPeripheral_RequestSense()

```c
int32_t OH_ScsiPeripheral_RequestSense(ScsiPeripheral_Device *dev, ScsiPeripheral_RequestSenseRequest *request, ScsiPeripheral_Response *response)
```

**Description**

Obtains sense data, that is, information returned by the SCSI device to the host, which is used to report the device status, error information, and diagnosis information.

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
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The API call is successful.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The permission verification fails. Ensure that you have obtained the **ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL** permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The DDK is not initialized. Call **OH_ScsiPeripheral_Init** to complete the initialization first.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The input **dev**, **request**, or **response** is null. Check whether the pointer parameter is correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The communication with the DDK service fails. Check whether the DDK service is initialized and running properly.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The memory operation fails. Check the memory status and whether there are out-of-bounds operations.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): An I/O error occurs. Check whether the device status is normal and whether the parameters are correct.<br>         [SCSIPERIPHERAL_DDK_TIMEOUT](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The transmission times out. Check the device status or increase the timeout interval.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The operation is not supported. Check the device specifications and status.|

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
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The API call is successful.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The permission verification fails. Ensure that you have obtained the **ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL** permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The DDK is not initialized. Call **OH_ScsiPeripheral_Init** to complete the initialization first.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The input **dev**, **request**, **request->data**, or **response** is null. Check whether the pointer parameter is correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The communication with the DDK service fails. Check whether the DDK service is initialized and running properly.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The memory operation fails. Check the memory status and whether there are out-of-bounds operations.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): An I/O error occurs. Check whether the device status is normal and whether the parameters are correct.<br>         [SCSIPERIPHERAL_DDK_TIMEOUT](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The transmission times out. Check the device status or increase the timeout interval.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The operation is not supported. Check the device specifications and status.|

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
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The API call is successful.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The permission verification fails. Ensure that you have obtained the **ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL** permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The DDK is not initialized. Call **OH_ScsiPeripheral_Init** to complete the initialization first.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The input **dev**, **request**, **request->data**, or **response** is null. Check whether the pointer parameter is correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The communication with the DDK service fails. Check whether the DDK service is initialized and running properly.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The memory operation fails. Check the memory status and whether there are out-of-bounds operations.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): An I/O error occurs. Check whether the device status is normal and whether the parameters are correct.<br>         [SCSIPERIPHERAL_DDK_TIMEOUT](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The transmission times out. Check the device status or increase the timeout interval.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The operation is not supported. Check the device specifications and status.|

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
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The API call is successful.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The permission verification fails. Ensure that you have obtained the **ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL** permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The DDK is not initialized. Call **OH_ScsiPeripheral_Init** to complete the initialization first.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The input **dev**, **request**, or **response** is null. Check whether the pointer parameter is correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The communication with the DDK service fails. Check whether the DDK service is initialized and running properly.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The memory operation fails. Check the memory status and whether there are out-of-bounds operations.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): An I/O error occurs. Check whether the device status is normal and whether the parameters are correct.<br>         [SCSIPERIPHERAL_DDK_TIMEOUT](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The transmission times out. Check the device status or increase the timeout interval.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The operation is not supported. Check the device specifications and status.|

### OH_ScsiPeripheral_SendRequestByCdb()

```c
int32_t OH_ScsiPeripheral_SendRequestByCdb(ScsiPeripheral_Device *dev, ScsiPeripheral_Request *request, ScsiPeripheral_Response *response)
```

**Description**

Sends SCSI commands in CDB mode.

**Required permissions**: ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

**Since**: 18


**Parameters**

| Name                                                                                   | Description                                                                                  |
|----------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md) *dev                                                             | Device handle. For details, see [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md).                                             |
| [ScsiPeripheral_Request](capi-scsiperipheralddk-scsiperipheral-request.md) *request    | CDB request. For details, see [ScsiPeripheral_Request](capi-scsiperipheralddk-scsiperipheral-request.md). Before calling this function, ensure that the **data** field is not empty and the **cdbLength** field is not 0.  |
| [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md) *response | CDB response. For details, see [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The API call is successful.<br>         [SCSIPERIPHERAL_DDK_NO_PERM](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The permission verification fails. Ensure that you have obtained the **ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL** permission.<br>         [SCSIPERIPHERAL_DDK_INIT_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The DDK is not initialized. Call **OH_ScsiPeripheral_Init** to complete the initialization first.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The input **dev**, **request**, **request->data**, or **response**<br>         is null, or **request->cdbLength** is 0. Check whether the pointer parameter is correct.<br>         [SCSIPERIPHERAL_DDK_SERVICE_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The communication with the DDK service fails. Check whether the DDK service is initialized and running properly.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The memory operation fails. Check the memory status and whether there are out-of-bounds operations.<br>         [SCSIPERIPHERAL_DDK_IO_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): An I/O error occurs. Check whether the device status is normal and whether the parameters are correct.<br>         [SCSIPERIPHERAL_DDK_TIMEOUT](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The transmission times out. Check the device status or increase the timeout interval.<br>         [SCSIPERIPHERAL_DDK_INVALID_OPERATION](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The operation is not supported. Check the device specifications and status.|

### OH_ScsiPeripheral_CreateDeviceMemMap()

```c
int32_t OH_ScsiPeripheral_CreateDeviceMemMap(ScsiPeripheral_Device *dev, size_t size, ScsiPeripheral_DeviceMemMap **devMmap)
```

**Description**

Creates a buffer. To avoid memory leakage, use [OH_ScsiPeripheral_DestroyDeviceMemMap](#oh_scsiperipheral_destroydevicememmap) to destroy a buffer after use.

**Since**: 18


**Parameters**

| Name| Description|
|------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md) *dev  | Device handle. For details, see [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md).  |
| size_t size | Buffer size, in bytes.|
| [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md) **devMmap | Device memory mapping used to return the created buffer to the caller. For details, see [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The API call is successful.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The input **dev**, **devMmap**, or ***devMmap** is null. Check whether the pointer parameter is correct.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The memory operation fails. Check the memory status and whether there are out-of-bounds operations.|

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
| [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md) *devMmap | Pointer to the buffer to be destroyed. The buffer is created by calling [OH_ScsiPeripheral_CreateDeviceMemMap](#oh_scsiperipheral_createdevicememmap).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The API call is successful.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The input **devMmap** is null. Check whether the pointer parameter is correct.<br>         [SCSIPERIPHERAL_DDK_MEMORY_ERROR](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The memory operation fails. Check the memory status and whether there are out-of-bounds operations.|

### OH_ScsiPeripheral_ParseBasicSenseInfo()

```c
int32_t OH_ScsiPeripheral_ParseBasicSenseInfo(uint8_t *senseData, uint8_t senseDataLen, ScsiPeripheral_BasicSenseInfo *senseInfo)
```

**Description**

Parses basic sense data, including the **Information**, **Command specific information**, and **Sense key specific** fields.

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| uint8_t *senseData | Sense data to be parsed.|
| uint8_t senseDataLen | Length of the sense data, that is, the length of the data to which the **senseData** parameter points. The unit is byte.|
| [ScsiPeripheral_BasicSenseInfo](capi-scsiperipheralddk-scsiperipheral-basicsenseinfo.md) *senseInfo | Basic sense data after parsing. For details, see [ScsiPeripheral_BasicSenseInfo](capi-scsiperipheralddk-scsiperipheral-basicsenseinfo.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [SCSIPERIPHERAL_DDK_SUCCESS](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The API call is successful.<br>         [SCSIPERIPHERAL_DDK_INVALID_PARAMETER](capi-scsi-peripheral-types-h.md#scsiperipheral_ddkerrcode): The input **senseData** is not a descriptor or is not of the fixed format, or **senseDataLen** is smaller than<br>         [SCSIPERIPHERAL_MIN_DESCRIPTOR_FORMAT_SENSE](capi-scsi-peripheral-types-h.md#macros) or **senseDataLen** is smaller than [SCSIPERIPHERAL_MIN_FIXED_FORMAT_SENSE](capi-scsi-peripheral-types-h.md#macros).|
