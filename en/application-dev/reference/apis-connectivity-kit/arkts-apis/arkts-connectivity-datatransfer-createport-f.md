# createPort

## Modules to Import

```TypeScript
import { dataTransfer } from '@kit.ConnectivityKit';
```

## createPort

```TypeScript
function createPort(uuid: string): void
```

Registers a port channel. A port channel can be used to connect to a remote device only after being registered. If the port channel is no longer needed after use, call [dataTransfer.destroyPort](arkts-connectivity-datatransfer-destroyport-f.md) to destroy it. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-dataTransfer-function createPort(uuid: string): void--><!--Device-dataTransfer-function createPort(uuid: string): void-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

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
| [36100020](../errorcode-nearlink-service.md#36100020-duplicate-port-registration) | The UUID is already registered. |
| [36100021](../errorcode-nearlink-service.md#36100021-number-of-registered-ports-exceeds-the-upper-limit) | Port exceeds the upper limit. |
| [36100043](../errorcode-nearlink-service.md#36100043-invalid-uuid) | Invalid UUID. |
| [36100044](../errorcode-nearlink-service.md#36100044-standard-nearlink-service-uuid-not-allowed) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
