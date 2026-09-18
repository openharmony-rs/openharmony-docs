# WifiLinkedInfo

Wi-Fi connection information. @typedef WifiLinkedInfo

**Since:** 12

**System capability:** SystemCapability.Communication.WiFi.STA

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## band

```TypeScript
band: number
```

The frequency band of a Wi-Fi access point.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

## bssid

```TypeScript
bssid: string
```

The BSSID of the Wi-Fi hotspot

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

## channelWidth

```TypeScript
channelWidth: WifiChannelWidth
```

Channel width of the connected hotspot.

**Type:** [WifiChannelWidth](arkts-connectivity-wifimanager-wifichannelwidth-e.md)

**Since:** 10

**System capability:** SystemCapability.Communication.WiFi.STA

## connState

```TypeScript
connState: ConnState
```

The state of this Wi-Fi connection.

**Type:** [ConnState](arkts-connectivity-wifimanager-connstate-e.md)

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

## frequency

```TypeScript
frequency: number
```

The frequency of a Wi-Fi access point.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

## ipAddress

```TypeScript
ipAddress: number
```

The IP address of this Wi-Fi connection.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

## isHidden

```TypeScript
isHidden: boolean
```

Whether the SSID of the access point (AP) of this Wi-Fi connection is hidden.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

## isHiLinkNetwork

```TypeScript
isHiLinkNetwork: boolean
```

Whether the Wi-Fi hotspot is HiLink network.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.Communication.WiFi.STA

## isRestricted

```TypeScript
isRestricted: boolean
```

Whether this Wi-Fi connection restricts the data volume.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

## linkSpeed

```TypeScript
linkSpeed: number
```

The speed of a Wi-Fi access point.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

## macAddress

```TypeScript
macAddress: string
```

The Wi-Fi MAC address of a device.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

## macType

```TypeScript
macType: number
```

Type of macAddress: 0 - real mac, 1 - random mac.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

## maxSupportedRxLinkSpeed

```TypeScript
maxSupportedRxLinkSpeed: number
```

Max rx speed of a Wi-Fi access point.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Communication.WiFi.STA

## maxSupportedTxLinkSpeed

```TypeScript
maxSupportedTxLinkSpeed: number
```

Max tx speed of a Wi-Fi access point.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Communication.WiFi.STA

## rssi

```TypeScript
rssi: number
```

The RSSI(dBm) of a Wi-Fi access point.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

## rxLinkSpeed

```TypeScript
rxLinkSpeed: number
```

The rx speed of a Wi-Fi access point.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

The SSID of the Wi-Fi hotspot

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

## supportedWifiCategory

```TypeScript
supportedWifiCategory: WifiCategory
```

Supported wifi category

**Type:** [WifiCategory](arkts-connectivity-wifimanager-wificategory-e.md)

**Since:** 12

**System capability:** SystemCapability.Communication.WiFi.STA

## wifiLinkType

```TypeScript
wifiLinkType?: WifiLinkType
```

Wi-Fi link type

**Type:** [WifiLinkType](arkts-connectivity-wifimanager-wifilinktype-e.md)

**Since:** 18

**System capability:** SystemCapability.Communication.WiFi.STA

## wifiStandard

```TypeScript
wifiStandard: WifiStandard
```

Wifi standard of current connection.

**Type:** [WifiStandard](arkts-connectivity-wifimanager-wifistandard-e.md)

**Since:** 10

**System capability:** SystemCapability.Communication.WiFi.STA
