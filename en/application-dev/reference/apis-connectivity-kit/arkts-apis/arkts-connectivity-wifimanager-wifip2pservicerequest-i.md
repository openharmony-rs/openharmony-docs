# WifiP2pServiceRequest

```TypeScript
interface WifiP2pServiceRequest
```

Represents the P2P service discovery request (TLV query).

**Since:** 26.0.1

<!--Device-wifiManager-interface WifiP2pServiceRequest--><!--Device-wifiManager-interface WifiP2pServiceRequest-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## protocolType

```TypeScript
protocolType: P2pServiceProtocolType
```

Service protocol type.

**Type:** [P2pServiceProtocolType](arkts-connectivity-wifimanager-p2pserviceprotocoltype-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-WifiP2pServiceRequest-protocolType: P2pServiceProtocolType--><!--Device-WifiP2pServiceRequest-protocolType: P2pServiceProtocolType-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## query

```TypeScript
query: Uint8Array
```

Query bytes. The maximum length is 256.

**Type:** Uint8Array

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-WifiP2pServiceRequest-query: Uint8Array--><!--Device-WifiP2pServiceRequest-query: Uint8Array-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P
