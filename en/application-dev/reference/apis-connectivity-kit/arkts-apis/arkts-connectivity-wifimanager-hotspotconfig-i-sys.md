# HotspotConfig (System API)

```TypeScript
interface HotspotConfig
```

Represents the hotspot configuration.

**Since:** 9

<!--Device-wifiManager-interface HotspotConfig--><!--Device-wifiManager-interface HotspotConfig-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## band

```TypeScript
band: number
```

Hotspot band. The value **1** stands for 2.4 GHz, the value **2** for 5 GHz, and the value **3** for dual bands.

**Type:** number

**Since:** 9

<!--Device-HotspotConfig-band: int--><!--Device-HotspotConfig-band: int-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## channel

```TypeScript
channel?: number
```

Hotspot channel (channels 1 to 14 for 2.4 GHz, and channels 7 to 196 for 5 GHz)

**Type:** number

**Since:** 10

<!--Device-HotspotConfig-channel?: int--><!--Device-HotspotConfig-channel?: int-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## ipAddress

```TypeScript
ipAddress?: string
```

DHCP server IP address

**Type:** string

**Since:** 10

<!--Device-HotspotConfig-ipAddress?: string--><!--Device-HotspotConfig-ipAddress?: string-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## maxConn

```TypeScript
maxConn: number
```

Maximum number of connections allowed.

**Type:** number

**Since:** 9

<!--Device-HotspotConfig-maxConn: int--><!--Device-HotspotConfig-maxConn: int-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## preSharedKey

```TypeScript
preSharedKey: string
```

PSK of the hotspot.

**Type:** string

**Since:** 9

<!--Device-HotspotConfig-preSharedKey: string--><!--Device-HotspotConfig-preSharedKey: string-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## securityType

```TypeScript
securityType: WifiSecurityType
```

Security type.

**Type:** [WifiSecurityType](arkts-connectivity-wifimanager-wifisecuritytype-e.md)

**Since:** 9

<!--Device-HotspotConfig-securityType: WifiSecurityType--><!--Device-HotspotConfig-securityType: WifiSecurityType-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## ssid

```TypeScript
ssid: string
```

SSID of the hotspot, in UTF-8 format.

**Type:** string

**Since:** 9

<!--Device-HotspotConfig-ssid: string--><!--Device-HotspotConfig-ssid: string-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.
