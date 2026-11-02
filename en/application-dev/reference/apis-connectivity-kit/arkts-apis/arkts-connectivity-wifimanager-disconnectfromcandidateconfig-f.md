# disconnectFromCandidateConfig

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## disconnectFromCandidateConfig

```TypeScript
function disconnectFromCandidateConfig(networkId: number, blockDuration: number): void
```

Disconnects a candidate network identified by networkId for a period of time. The disconnected candidate network will not be re-associated during the block duration. You can only disconnect candidate networks that were added by the caller.

**Since:** 26.1.0

**Required permissions:** ohos.permission.SET_WIFI_INFO

**Model restriction:** This API can be used only in the stage model.

<!--Device-wifiManager-function disconnectFromCandidateConfig(networkId: int, blockDuration: int): void--><!--Device-wifiManager-function disconnectFromCandidateConfig(networkId: int, blockDuration: int): void-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| networkId | number | Yes | Identifies the candidate network to be disconnected. |
| blockDuration | number | Yes | Duration for which the network is blocked from re-associated, in seconds. If the value is -1, the candidate network is permanently blocked from re-associated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta-internal-error) | Operation failed, possibly causes: <br>The network identified by networkId does not exist. <br>The candidate network was not added by the caller. <br>The caller is not running in the foreground. |
| [2501001](../errorcode-wifi.md#2501001-sta-disabled) | Wi-Fi STA disabled. |
