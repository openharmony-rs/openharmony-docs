# connectDevice (System API)

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## connectDevice

```TypeScript
function connectDevice(addrInfo: AddressInfo, params: ConnectParam): Promise<AttachStateChangeInfo>
```

Connecting devices based on addresses

**Since:** 26.0.0

**Required permissions:** ohos.permission.CONNECT_MECHANIC_HARDWARE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| addrInfo | [AddressInfo](arkts-mechanic-mechanicmanager-addressinfo-i-sys.md) | Yes | Address information. |
| params | [ConnectParam](arkts-mechanic-mechanicmanager-connectparam-i-sys.md) | Yes | Connect Parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AttachStateChangeInfo](arkts-mechanic-mechanicmanager-attachstatechangeinfo-i.md)&gt; | Promise used to return the attach state change information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-system-error) | Service exception. |
