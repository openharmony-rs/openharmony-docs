# createCdsmClient

## Modules to Import

```TypeScript
import { cdsm } from '@kit.ConnectivityKit';
```

## createCdsmClient

```TypeScript
function createCdsmClient(address: string): CdsmClient
```

Creates a CDSM client instance.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| address | string | Yes | Address of a member device in the paired and connected coordinated devices set. The address format is **11:22:33:AA:BB:FF**. The address must contain six segments, each segment is a string of two hexadecimal characters, and the segments are separated by colons (:). |

**Return value:**

| Type | Description |
| --- | --- |
| [CdsmClient](arkts-connectivity-cdsm-cdsmclient-i.md) | **CdsmClient** instance used to query and subscribe to the CDSM information of a remote device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because the chip does not support it. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100041](../errorcode-nearlink-service.md#36100041-invalid-url) | Invalid address. |
| [36100050](../errorcode-nearlink-service.md#36100050-coordinated-device-set-management-not-supported) | Coordinated Devices Set Management not supported. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
