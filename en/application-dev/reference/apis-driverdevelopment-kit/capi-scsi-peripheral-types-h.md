# scsi_peripheral_types.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=bf2c7dec6618c889ba9f8aba11f191335ed707dc translatedAt=2026-11-10T01:09:29.496Z pushedAt=2026-11-10T01:42:40.580Z nl=1 -->

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
| [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md) | ScsiPeripheral_DeviceMemMap | Represents the device memory mapping created by calling [OH_ScsiPeripheral_CreateDeviceMemMap](capi-scsi-peripheral-api-h.md#oh_scsiperipheral_createdevicememmap). The buffer that uses the device memory mapping can provide better performance. |
| [ScsiPeripheral_IORequest](capi-scsiperipheralddk-scsiperipheral-iorequest.md)       | ScsiPeripheral_IORequest | Request parameters for read/write operations. This struct defines the request parameters required for read/write operations on a SCSI peripheral, including the logical block start address, transfer length, and control information. |
| [ScsiPeripheral_Request](capi-scsiperipheralddk-scsiperipheral-request.md)           | ScsiPeripheral_Request | Defines the SCSI request parameters. It is used to construct the request parameters for interacting with SCSI devices, including the CDB, data buffer, and timeout interval. |
| [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md)         | ScsiPeripheral_Response | Defines the SCSI response parameter struct, which contains the status, error diagnostic data, and transfer result, and is used to receive SCSI device response data and determine whether a command succeeds. |
| [ScsiPeripheral_TestUnitReadyRequest](capi-scsiperipheralddk-scsiperipheral-testunitreadyrequest.md) | ScsiPeripheral_TestUnitReadyRequest | Request struct for the SCSI command (TEST UNIT READY), which is typically used to check whether a logical unit is ready (a logical unit is an independently addressable I/O operation entity in a SCSI device). |
| [ScsiPeripheral_InquiryRequest](capi-scsiperipheralddk-scsiperipheral-inquiryrequest.md)            | ScsiPeripheral_InquiryRequest | Request structure for the SCSI INQUIRY command, typically used to query basic device information. |
| [ScsiPeripheral_InquiryInfo](capi-scsiperipheralddk-scsiperipheral-inquiryinfo.md)                  | ScsiPeripheral_InquiryInfo | SCSI INQUIRY data, used to store the query result of the INQUIRY command of a SCSI peripheral. |
| [ScsiPeripheral_ReadCapacityRequest](capi-scsiperipheralddk-scsiperipheral-readcapacityrequest.md)  | ScsiPeripheral_ReadCapacityRequest | Defines the request struct for the SCSI READ CAPACITY command, which is used to send a command for reading the storage capacity and helps obtain the logical block size and total number of blocks of the device. |
| [ScsiPeripheral_CapacityInfo](capi-scsiperipheralddk-scsiperipheral-capacityinfo.md)                | ScsiPeripheral_CapacityInfo | SCSI READ CAPACITY structure. Used to obtain the storage capacity information of a device when developing a SCSI device driver, and supports operations such as partition management, available space check, and storage resource allocation. |
| [ScsiPeripheral_RequestSenseRequest](capi-scsiperipheralddk-scsiperipheral-requestsenserequest.md)  | ScsiPeripheral_RequestSenseRequest | Request structure of the SCSI command (REQUEST SENSE), which is typically used to obtain device error information. |
| [ScsiPeripheral_BasicSenseInfo](capi-scsiperipheralddk-scsiperipheral-basicsenseinfo.md)            | ScsiPeripheral_BasicSenseInfo | Basic information structure of SCSI Sense Data, used to encapsulate the sense activation returned after a SCSI command is executed. This structure contains the response code, status flags, and various information fields, and is used by the driver to obtain and analyze the error status and command execution result of a SCSI device. |
| [ScsiPeripheral_VerifyRequest](capi-scsiperipheralddk-scsiperipheral-verifyrequest.md)              | ScsiPeripheral_VerifyRequest | Request struct for the SCSI VERIFY command, which is typically used to verify the data integrity of logical blocks. |
| [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md)                            | ScsiPeripheral_Device | Opaque SCSI device structure, used to represent the device handle for interacting with a SCSI peripheral. |

### Macros

| Name | Description |
| -- | -- |
| SCSIPERIPHERAL_MIN_DESCRIPTOR_FORMAT_SENSE 8 | Minimum length of descriptor format sense data. **Since:** 18|
| SCSIPERIPHERAL_MIN_FIXED_FORMAT_SENSE 18 | Minimum length of fixed format sense data. **Since:** 18|
| SCSIPERIPHERAL_MAX_CMD_DESC_BLOCK_LEN 16 | Maximum length of the command descriptor block. **Since:** 18|
| SCSIPERIPHERAL_MAX_SENSE_DATA_LEN 252 | Maximum length of sense data. **Since:** 18|
| SCSIPERIPHERAL_VENDOR_ID_LEN 8 | Length of the vendor identifier. **Since:** 18|
| SCSIPERIPHERAL_PRODUCT_ID_LEN 16 | Length of the product identifier. **Since:** 18|
| SCSIPERIPHERAL_PRODUCT_REV_LEN 4 | Length of the product revision number. **Since:** 18|

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
| SCSIPERIPHERAL_DDK_NO_PERM = 201 | No permission. Ensure that the application has declared the required permissions. |
| SCSIPERIPHERAL_DDK_INVALID_PARAMETER = 401 | Invalid parameter. Check whether the parameters meet the requirements. |
| SCSIPERIPHERAL_DDK_SUCCESS = 31700000 | Operation success.|
| SCSIPERIPHERAL_DDK_MEMORY_ERROR = 31700001 | Memory-related error, for example, insufficient memory, memory data copy failure, or memory allocation failure. Check the memory status and related parameters. |
| SCSIPERIPHERAL_DDK_INVALID_OPERATION = 31700002 | Invalid operation. Check whether the operation logic is correct. |
| SCSIPERIPHERAL_DDK_IO_ERROR = 31700003 | Device I/O operation failed. Check the transfer parameters and device specifications. |
| SCSIPERIPHERAL_DDK_TIMEOUT = 31700004 | Transmission timeout. Check the timeout parameters and device status. |
| SCSIPERIPHERAL_DDK_INIT_ERROR = 31700005 | DDK initialization error, or the DDK is not initialized. Initialize the DDK service first. |
| SCSIPERIPHERAL_DDK_SERVICE_ERROR = 31700006 | Communication with the SCSI Peripheral DDK service failed. Check whether the DDK service is running properly. |
| SCSIPERIPHERAL_DDK_DEVICE_NOT_FOUND = 31700007 | Device not found. Ensure that the device information passed in is correct. |

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
| SCSIPERIPHERAL_STATUS_TASK_ABORTED = 0x40 | Task aborted. |


