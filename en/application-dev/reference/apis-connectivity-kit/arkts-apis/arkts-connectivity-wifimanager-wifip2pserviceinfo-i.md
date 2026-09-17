# WifiP2pServiceInfo

Represents the P2P service information.

**Since:** 26.1.0

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

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.WiFi.P2P

## queryList

```TypeScript
queryList: Array<string>
```

Query string list consumed by wpa_supplicant. The maximum size of a single data record is 1024.

**Type:** Array&lt;string&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.WiFi.P2P

## serviceName

```TypeScript
serviceName: string
```

Service name. Refer to the [addDnsSdLocalP2pService](arkts-connectivity-wifimanager-adddnssdlocalp2pservice-f.md) or [addUpnpLocalP2pService](arkts-connectivity-wifimanager-addupnplocalp2pservice-f.md) functions.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.WiFi.P2P
