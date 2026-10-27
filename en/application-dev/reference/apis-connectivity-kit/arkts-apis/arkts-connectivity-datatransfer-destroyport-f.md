# destroyPort

## Modules to Import

```TypeScript
import { dataTransfer } from '@kit.ConnectivityKit';
```

## destroyPort

```TypeScript
function destroyPort(uuid: string): void
```

Destroys the port channel. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-dataTransfer-function destroyPort(uuid: string): void--><!--Device-dataTransfer-function destroyPort(uuid: string): void-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**See also:** [createPort](arkts-connectivity-datatransfer-createport-f.md#createport-1) Registers a port channel.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uuid | string | Yes | NearLink service UUID, which is a string of 36 characters. The value consists of 32 hexadecimal digits and four hyphens (-), for example, **FFFFFFFF-1234-5678-ABCD-000000001234**, which indicates a 128-bit ID. The value cannot be set to a standard NearLink UUID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes:         1. The hardware does not support the capability;         2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100022](../errorcode-nearlink-service.md#36100022-port-not-registered) | The UUID is not registered. |
| [36100043](../errorcode-nearlink-service.md#36100043-invalid-uuid) | Invalid UUID. |
| [36100044](../errorcode-nearlink-service.md#36100044-standard-nearlink-service-uuid-not-allowed) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
