# P2pUpnpInfo

```TypeScript
interface P2pUpnpInfo
```

Represents the UPnP service response information received from a peer device.

**Since:** 26.1.0

<!--Device-wifiManager-interface P2pUpnpInfo--><!--Device-wifiManager-interface P2pUpnpInfo-End-->

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

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-P2pUpnpInfo-device: WifiP2pDevice--><!--Device-P2pUpnpInfo-device: WifiP2pDevice-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## uniqueServiceNames

```TypeScript
uniqueServiceNames: Array<string>
```

List of unique service names discovered. The maximum size of a single data record is 1024 bytes, and the data volume is related to the number of services on the target device.

**Type:** Array&lt;string&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-P2pUpnpInfo-uniqueServiceNames: Array<string>--><!--Device-P2pUpnpInfo-uniqueServiceNames: Array<string>-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P
