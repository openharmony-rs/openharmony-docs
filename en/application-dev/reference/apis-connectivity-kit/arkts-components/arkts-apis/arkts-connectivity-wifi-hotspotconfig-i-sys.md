# HotspotConfig (System API)

```TypeScript
interface HotspotConfig
```

Wi-Fi hotspot configuration information.

@interface HotspotConfig

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [HotspotConfig](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md)

<!--Device-wifi-interface HotspotConfig--><!--Device-wifi-interface HotspotConfig-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## band

```TypeScript
band: number
```

The frequency band of the Wi-Fi hotspot

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [band](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md#band)

<!--Device-HotspotConfig-band: number--><!--Device-HotspotConfig-band: number-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## maxConn

```TypeScript
maxConn: number
```

The maximum number of connections allowed by the Wi-Fi hotspot

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [maxConn](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md#maxconn)

<!--Device-HotspotConfig-maxConn: number--><!--Device-HotspotConfig-maxConn: number-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## preSharedKey

```TypeScript
preSharedKey: string
```

The password of the Wi-Fi hotspot

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [preSharedKey](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md#presharedkey)

<!--Device-HotspotConfig-preSharedKey: string--><!--Device-HotspotConfig-preSharedKey: string-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## securityType

```TypeScript
securityType: WifiSecurityType
```

The encryption mode of the Wi-Fi hotspot

**Type:** [WifiSecurityType](arkts-connectivity-wifi-wifisecuritytype-e.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [securityType](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md#securitytype)

<!--Device-HotspotConfig-securityType: WifiSecurityType--><!--Device-HotspotConfig-securityType: WifiSecurityType-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

## ssid

```TypeScript
ssid: string
```

The SSID of the Wi-Fi hotspot

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [ssid](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md#ssid)

<!--Device-HotspotConfig-ssid: string--><!--Device-HotspotConfig-ssid: string-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.
