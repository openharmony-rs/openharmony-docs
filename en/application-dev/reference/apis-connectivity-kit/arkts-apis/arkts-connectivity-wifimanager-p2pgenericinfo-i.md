# P2pGenericInfo

```TypeScript
interface P2pGenericInfo
```

Represents the generic service response information received from a peer device.

**Since:** 26.0.1

<!--Device-wifiManager-interface P2pGenericInfo--><!--Device-wifiManager-interface P2pGenericInfo-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## device

```TypeScript
device: WifiP2pDevice
```

The peer device that responded with the service.

**Type:** [WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-P2pGenericInfo-device: WifiP2pDevice--><!--Device-P2pGenericInfo-device: WifiP2pDevice-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## protocolType

```TypeScript
protocolType: P2pServiceProtocolType
```

Service protocol type of the response.

**Type:** [P2pServiceProtocolType](arkts-connectivity-wifimanager-p2pserviceprotocoltype-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-P2pGenericInfo-protocolType: P2pServiceProtocolType--><!--Device-P2pGenericInfo-protocolType: P2pServiceProtocolType-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## responseData

```TypeScript
responseData: Uint8Array
```

Raw response data from the peer device. The maximum length is 1024.

**Type:** Uint8Array

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-P2pGenericInfo-responseData: Uint8Array--><!--Device-P2pGenericInfo-responseData: Uint8Array-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P
