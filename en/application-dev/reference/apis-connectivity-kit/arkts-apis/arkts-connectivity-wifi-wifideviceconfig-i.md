# WifiDeviceConfig

```TypeScript
interface WifiDeviceConfig
```

Wi-Fi device configuration information.

@interface WifiDeviceConfig

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

Wi-Fi bssid(MAC): the length is 6

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

Hide SSID or not, false(default): not hide

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

Wi-Fi key: maximum length is 64

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

Security type: reference definition of WifiSecurityType

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

Wi-Fi SSID: the maximum length is 32

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [ssid](arkts-connectivity-wifimanager-wifideviceconfig-i.md#ssid)

<!--Device-WifiDeviceConfig-ssid: string--><!--Device-WifiDeviceConfig-ssid: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA
