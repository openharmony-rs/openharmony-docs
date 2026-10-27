# scsi_peripheral_types.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

## Overview

Provides the enum variables, structures, and macros used in the SCSI Peripheral DDK APIs.

**File to include**: &lt;scsi_peripheral/scsi_peripheral_types.h&gt;

**Library**: libscsi.z.so

**System capability**: SystemCapability.Driver.SCSI.Extension

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

## Summary

### Structs

| Name                                                                                  | typedef Keyword| Description|
|--------------------------------------------------------------------------------------| -- | -- |
| [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md) | ScsiPeripheral_DeviceMemMap | Represents the device memory mapping created by calling [OH_ScsiPeripheral_CreateDeviceMemMap](capi-scsi-peripheral-api-h.md#oh_scsiperipheral_createdevicememmap). The buffer that uses the device memory mapping can provide better performance.|
| [ScsiPeripheral_IORequest](capi-scsiperipheralddk-scsiperipheral-iorequest.md)       | ScsiPeripheral_IORequest | Defines the read/write operation request. This struct defines the request parameters required for the SCSI peripheral to perform read/write operations, including the start address of the logical block, transfer length, and control information.|
| [ScsiPeripheral_Request](capi-scsiperipheralddk-scsiperipheral-request.md)           | ScsiPeripheral_Request | Defines the SCSI request parameters. It is used to construct the request parameters for interacting with SCSI devices, including the CDB, data buffer, and timeout interval.|
| [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md)         | ScsiPeripheral_Response | Defines the SCSI response parameters, including the status, error diagnosis data, and transfer result. It is used to receive the response data from the SCSI device and determine whether the command is successful.|
| [ScsiPeripheral_TestUnitReadyRequest](capi-scsiperipheralddk-scsiperipheral-testunitreadyrequest.md) | ScsiPeripheral_TestUnitReadyRequest | Defines the SCSI command (**TEST UNIT READY**) request struct, which is usually used to check whether the logical unit is ready. A logical unit is an I/O operation entity that can be independently addressed in a SCSI device.|
| [ScsiPeripheral_InquiryRequest](capi-scsiperipheralddk-scsiperipheral-inquiryrequest.md)            | ScsiPeripheral_InquiryRequest | Defines the SCSI command (**INQUIRY**) request struct, which is usually used to query basic device information.|
| [ScsiPeripheral_InquiryInfo](capi-scsiperipheralddk-scsiperipheral-inquiryinfo.md)                  | ScsiPeripheral_InquiryInfo | Defines the SCSI **INQUIRY** data, which is used to store the query result of the **INQUIRY** command of SCSI peripherals.|
| [ScsiPeripheral_ReadCapacityRequest](capi-scsiperipheralddk-scsiperipheral-readcapacityrequest.md)  | ScsiPeripheral_ReadCapacityRequest | Defines the SCSI command (**READ CAPACITY**) request struct, which is used to send a command for reading the storage capacity. It helps obtain the logical block size and total number of blocks of a device.|
| [ScsiPeripheral_CapacityInfo](capi-scsiperipheralddk-scsiperipheral-capacityinfo.md)                | ScsiPeripheral_CapacityInfo | Defines the SCSI **READ CAPACITY** struct. It is used to obtain the storage capacity of a device during SCSI driver development. It supports operations such as partition management, available space check, and store resource allocation.|
| [ScsiPeripheral_RequestSenseRequest](capi-scsiperipheralddk-scsiperipheral-requestsenserequest.md)  | ScsiPeripheral_RequestSenseRequest | Defines the SCSI **REQUEST SENSE** request struct. This command is usually used to obtain device error information.|
| [ScsiPeripheral_BasicSenseInfo](capi-scsiperipheralddk-scsiperipheral-basicsenseinfo.md)            | ScsiPeripheral_BasicSenseInfo | Defines the basic information struct of SCSI sense data, which is used to encapsulate the sense data returned after a SCSI command is executed. This struct contains the response code, status flag, and various information fields, which are used by the driver to obtain and analyze the error status and command execution result of the SCSI device.|
| [ScsiPeripheral_VerifyRequest](capi-scsiperipheralddk-scsiperipheral-verifyrequest.md)              | ScsiPeripheral_VerifyRequest | Defines the SCSI command (**VERIFY**) request struct, which is usually used to verify the data integrity of logical blocks.|
| [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md)                            | ScsiPeripheral_Device | Defines the opaque SCSI device struct, which is used to represent the device handle that interacts with SCSI peripherals.|

### Macros

| Name| Description|
| -- | -- |
| SCSIPERIPHERAL_MIN_DESCRIPTOR_FORMAT_SENSE 8 | Defines the minimum length of the sense data in the descriptor format. **Since**: 18|
| SCSIPERIPHERAL_MIN_FIXED_FORMAT_SENSE 18 | Defines the minimum length of the sense data in the fixed format. **Since**: 18|
| SCSIPERIPHERAL_MAX_CMD_DESC_BLOCK_LEN 16 | Defines the maximum length of a CDB. **Since**: 18|
| SCSIPERIPHERAL_MAX_SENSE_DATA_LEN 252 | Defines the maximum length of the sense data. **Since**: 18|
| SCSIPERIPHERAL_VENDOR_ID_LEN 8 | Defines the length of a vendor ID. **Since**: 18|
| SCSIPERIPHERAL_PRODUCT_ID_LEN 16 | Defines the length of a product ID. **Since**: 18|
| SCSIPERIPHERAL_PRODUCT_REV_LEN 4 | Defines the length of a product revision version. **Since**: 18|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ScsiPeripheral_DdkErrCode](#scsiperipheral_ddkerrcode) | ScsiPeripheral_DdkErrCode | Enumerates the SCSI Peripheral DDK error codes.|
| [ScsiPeripheral_Status](#scsiperipheral_status) | ScsiPeripheral_Status | Enumerates the SCSI status codes used for the response.|

## Enum Description

### ScsiPeripheral_DdkErrCode

```c
enum ScsiPeripheral_DdkErrCode
```

**Description**

Enumerates the SCSI Peripheral DDK error codes.

**Since**: 18

| Enum| Description|
| -- | -- |
| SCSIPERIPHERAL_DDK_NO_PERM = 201 | Permission denied. Ensure that you have correctly declared the required permissions.|
| SCSIPERIPHERAL_DDK_INVALID_PARAMETER = 401 | Invalid parameter. Check whether the parameters meet the requirements.|
| SCSIPERIPHERAL_DDK_SUCCESS = 31700000 | Operation success.|
| SCSIPERIPHERAL_DDK_MEMORY_ERROR = 31700001 | Memory-related errors, such as insufficient memory, memory data replication failure, or memory request failure. Check the memory status and related parameters.|
| SCSIPERIPHERAL_DDK_INVALID_OPERATION = 31700002 | Invalid operation. Check whether the operation logic is correct.|
| SCSIPERIPHERAL_DDK_IO_ERROR = 31700003 | Device input/output operation failed. Check the transfer parameters and device specifications.|
| SCSIPERIPHERAL_DDK_TIMEOUT = 31700004 | Transfer timeout. Check the timeout parameters and device status.|
| SCSIPERIPHERAL_DDK_INIT_ERROR = 31700005 | DDK initialization error, or DDK uninitialized. Initialize the DDK service first.|
| SCSIPERIPHERAL_DDK_SERVICE_ERROR = 31700006 | Communication with the SCSI Peripheral DDK failed. Check whether the DDK service is running properly.|
| SCSIPERIPHERAL_DDK_DEVICE_NOT_FOUND = 31700007 | Device not found. Ensure that the input device information is correct.|

### ScsiPeripheral_Status

```c
enum ScsiPeripheral_Status
```

**Description**

Enumerates the SCSI status codes used for the response.

**Since**: 18

| Enum| Description|
| -- | -- |
| SCSIPERIPHERAL_STATUS_GOOD = 0x00 | Normal state.|
| SCSIPERIPHERAL_STATUS_CHECK_CONDITION_NEEDED = 0x02 | Status check required.|
| SCSIPERIPHERAL_STATUS_CONDITION_MET = 0x04 | Conditions met.|
| SCSIPERIPHERAL_STATUS_BUSY = 0x08 | Occupying.|
| SCSIPERIPHERAL_STATUS_RESERVATION_CONFLICT = 0x18 | Resource reservation conflict.|
| SCSIPERIPHERAL_STATUS_TASK_SET_FULL = 0x28 | Task set already full.|
| SCSIPERIPHERAL_STATUS_ACA_ACTIVE = 0x30 | ACA activity status.|
| SCSIPERIPHERAL_STATUS_TASK_ABORTED = 0x40 | Task aborted.|
