# WifiDeviceConfig

```TypeScript
interface WifiDeviceConfig
```

Represents the Wi-Fi configuration information.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i.md)

<!--Device-wifi-interface WifiDeviceConfig--><!--Device-wifi-interface WifiDeviceConfig-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## bssid

```TypeScript
bssid: string
```

BSSID of the hotspot, for example, **00:11:22:33:44:55**.

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [bssid](arkts-connectivity-wifimanager-wifideviceconfig-i.md#bssid)

<!--Device-WifiDeviceConfig-bssid: string--><!--Device-WifiDeviceConfig-bssid: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## isHiddenSsid

```TypeScript
isHiddenSsid: boolean
```

Whether the network is hidden. The value **true** indicates that the network is hidden, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [isHiddenSsid](arkts-connectivity-wifimanager-wifideviceconfig-i.md#ishiddenssid)

<!--Device-WifiDeviceConfig-isHiddenSsid: boolean--><!--Device-WifiDeviceConfig-isHiddenSsid: boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## preSharedKey

```TypeScript
preSharedKey: string
```

PSK of the hotspot. The maximum length is 64 bytes.

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [preSharedKey](arkts-connectivity-wifimanager-wifideviceconfig-i.md#presharedkey)

<!--Device-WifiDeviceConfig-preSharedKey: string--><!--Device-WifiDeviceConfig-preSharedKey: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## securityType

```TypeScript
securityType: WifiSecurityType
```

Security type.

**Type:** [WifiSecurityType](arkts-connectivity-wifi-wifisecuritytype-e.md)

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [securityType](arkts-connectivity-wifimanager-wifideviceconfig-i.md#securitytype)

<!--Device-WifiDeviceConfig-securityType: WifiSecurityType--><!--Device-WifiDeviceConfig-securityType: WifiSecurityType-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

Service set identifier (SSID) of the hotspot, in UTF-8 format. The maximum length is 32 bytes.

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [ssid](arkts-connectivity-wifimanager-wifideviceconfig-i.md#ssid)

<!--Device-WifiDeviceConfig-ssid: string--><!--Device-WifiDeviceConfig-ssid: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA
