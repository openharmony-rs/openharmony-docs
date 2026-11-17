# offP2pServiceDiscovery

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## offP2pServiceDiscovery

```TypeScript
function offP2pServiceDiscovery(callback?: Callback<P2pServiceDiscoveryInfo>): void
```

Unsubscribes from generic service response events.

**Since:** 26.1.0

**Required permissions:** ohos.permission.GET_WIFI_INFO

**Model restriction:** This API can be used only in the stage model.

<!--Device-wifiManager-function offP2pServiceDiscovery(callback?: Callback<P2pServiceDiscoveryInfo>): void--><!--Device-wifiManager-function offP2pServiceDiscovery(callback?: Callback<P2pServiceDiscoveryInfo>): void-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[P2pServiceDiscoveryInfo](arkts-connectivity-wifimanager-p2pservicediscoveryinfo-t.md)&gt; | No | Callback to unregister. If not specified, all callbacks for this event type are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | Operation failed. |
