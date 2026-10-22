# connect

## Modules to Import

```TypeScript
import { dataTransfer } from '@kit.ConnectivityKit';
```

## connect

```TypeScript
function connect(params: ConnectionParams): Promise<void>
```

Connects to a remote device. This API uses a promise to return the result. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-dataTransfer-function connect(params: ConnectionParams): Promise<void>--><!--Device-dataTransfer-function connect(params: ConnectionParams): Promise<void>-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**See also:** [disconnect](arkts-connectivity-datatransfer-disconnect-f.md#disconnect-1) Disconnects from the remote device.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [ConnectionParams](arkts-connectivity-datatransfer-connectionparams-i.md) | Yes | Connection parameters of the port. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes:         1. The hardware does not support the capability;         2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100041](../errorcode-nearlink-service.md#36100041-invalid-url) | Invalid address. |
| [36100043](../errorcode-nearlink-service.md#36100043-invalid-uuid) | Invalid UUID. |
| [36100044](../errorcode-nearlink-service.md#36100044-standard-nearlink-service-uuid-not-allowed) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
