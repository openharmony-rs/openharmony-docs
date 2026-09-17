# createClient

## Modules to Import

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## createClient

```TypeScript
function createClient(address: string): Client
```

Creates an SSAP client instance.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| address | string | Yes | Address of the remote server device. The address format is **11:22:33:AA:BB:FF**. |

**Return value:**

| Type | Description |
| --- | --- |
| [Client](arkts-connectivity-ssap-client-i.md) | SSAP client instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because the chip does not support it. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100041](../errorcode-nearlink-service.md#36100041-invalid-url) | Invalid address. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
