# WifiScanInfo

Describes the scanned Wi-Fi information.

@interface WifiScanInfo

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [WifiScanInfo](arkts-connectivity-wifimanager-wifiscaninfo-i.md)

**System capability:** SystemCapability.Communication.WiFi.STA

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## band

```TypeScript
band: number
```

Frequency band, 1: 2.4G, 2: 5G

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [band](arkts-connectivity-wifimanager-wifiscaninfo-i.md#band)

**System capability:** SystemCapability.Communication.WiFi.STA

## bssid

```TypeScript
bssid: string
```

Wi-Fi bssid(MAC): the length is 6

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [bssid](arkts-connectivity-wifimanager-wifiscaninfo-i.md#bssid)

**System capability:** SystemCapability.Communication.WiFi.STA

## capabilities

```TypeScript
capabilities: string
```

Hotspot capability

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [capabilities](arkts-connectivity-wifimanager-wifiscaninfo-i.md#capabilities)

**System capability:** SystemCapability.Communication.WiFi.STA

## channelWidth

```TypeScript
channelWidth: number
```

Channel width

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [channelWidth](arkts-connectivity-wifimanager-wifiscaninfo-i.md#channelwidth)

**System capability:** SystemCapability.Communication.WiFi.STA

## frequency

```TypeScript
frequency: number
```

Frequency

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [frequency](arkts-connectivity-wifimanager-wifiscaninfo-i.md#frequency)

**System capability:** SystemCapability.Communication.WiFi.STA

## rssi

```TypeScript
rssi: number
```

Received signal strength indicator (RSSI)

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [rssi](arkts-connectivity-wifimanager-wifiscaninfo-i.md#rssi)

**System capability:** SystemCapability.Communication.WiFi.STA

## securityType

```TypeScript
securityType: WifiSecurityType
```

Security type: reference definition of WifiSecurityType

**Type:** [WifiSecurityType](arkts-connectivity-wifi-wifisecuritytype-e.md)

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [securityType](arkts-connectivity-wifimanager-wifiscaninfo-i.md#securitytype)

**System capability:** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

Wi-Fi SSID: the maximum length is 32

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [ssid](arkts-connectivity-wifimanager-wifiscaninfo-i.md#ssid)

**System capability:** SystemCapability.Communication.WiFi.STA

## timestamp

```TypeScript
timestamp: number
```

Time stamp

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [timestamp](arkts-connectivity-wifimanager-wifiscaninfo-i.md#timestamp)

**System capability:** SystemCapability.Communication.WiFi.STA
