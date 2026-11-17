# discoverServices

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## discoverServices

```TypeScript
function discoverServices(): void
```

Starts P2P service discovery. The pending requests' TLV queries are used, falling back to all service types if the pending list is empty. Use [addDnsSdServiceRequest](arkts-connectivity-wifimanager-adddnssdservicerequest-f.md) or [addUpnpServiceRequest](arkts-connectivity-wifimanager-addupnpservicerequest-f.md) to add a service request before starting discovery.

**Since:** 26.1.0

**Required permissions:** ohos.permission.GET_WIFI_PEERS_MAC

**Model restriction:** This API can be used only in the stage model.

<!--Device-wifiManager-function discoverServices(): void--><!--Device-wifiManager-function discoverServices(): void-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p-module-error) | Wi-Fi STA disabled. |
