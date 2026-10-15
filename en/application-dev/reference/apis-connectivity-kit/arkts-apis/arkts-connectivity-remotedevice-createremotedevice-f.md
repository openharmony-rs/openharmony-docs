# createRemoteDevice

## Modules to Import

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## createRemoteDevice

```TypeScript
function createRemoteDevice(address: string): RemoteDevice
```

Creates a **RemoteDevice** instance. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-remoteDevice-function createRemoteDevice(address: string): RemoteDevice--><!--Device-remoteDevice-function createRemoteDevice(address: string): RemoteDevice-End-->

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
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes:         1. The hardware does not support the capability;         2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [36100041](../errorcode-nearlink-service.md#36100041-invalid-url) | Invalid address. |
