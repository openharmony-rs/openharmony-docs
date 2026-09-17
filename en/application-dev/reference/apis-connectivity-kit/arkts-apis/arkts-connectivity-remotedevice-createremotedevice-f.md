# createRemoteDevice

## Modules to Import

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## createRemoteDevice

```TypeScript
function createRemoteDevice(address: string): RemoteDevice
```

Creates a **RemoteDevice** instance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| address | string | Yes | Address of a remote device. The address format is **11:22:33:AA:BB:FF**. |

**Return value:**

| Type | Description |
| --- | --- |
| [RemoteDevice](arkts-connectivity-remotedevice-remotedevice-i.md) | **RemoteDevice** instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because the chip does not support it. |
| [36100041](../errorcode-nearlink-service.md#36100041-invalid-url) | Invalid address. |
