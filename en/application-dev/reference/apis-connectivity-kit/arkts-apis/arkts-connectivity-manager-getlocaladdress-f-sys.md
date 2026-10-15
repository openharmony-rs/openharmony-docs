# getLocalAddress (System API)

## Modules to Import

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## getLocalAddress

```TypeScript
function getLocalAddress(): string
```

Queries the MAC address of the local device. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK and ohos.permission.GET_NEARLINK_LOCAL_MAC

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-manager-function getLocalAddress(): string--><!--Device-manager-function getLocalAddress(): string-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| string | Local MAC address, for example, **'11:22:33:AA:BB:FF'**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes:         1. The hardware does not support the capability;         2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
