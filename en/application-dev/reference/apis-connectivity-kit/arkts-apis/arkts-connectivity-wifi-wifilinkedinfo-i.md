# WifiLinkedInfo

```TypeScript
interface WifiLinkedInfo
```

Provides information about a Wi-Fi connection.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [WifiLinkedInfo](arkts-connectivity-wifimanager-wifilinkedinfo-i.md)

<!--Device-wifi-interface WifiLinkedInfo--><!--Device-wifi-interface WifiLinkedInfo-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## band

```TypeScript
band: number
```

Frequency band of the Wi-Fi access point. The value **1** indicates 2.4 GHz, and the value **2** indicates 5 GHz.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [band](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#band)

<!--Device-WifiLinkedInfo-band: number--><!--Device-WifiLinkedInfo-band: number-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## bssid

```TypeScript
bssid: string
```

BSSID of the hotspot, for example, **00:11:22:33:44:55**.

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [bssid](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#bssid)

<!--Device-WifiLinkedInfo-bssid: string--><!--Device-WifiLinkedInfo-bssid: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## connState

```TypeScript
connState: ConnState
```

Wi-Fi connection status.

**Type:** [ConnState](arkts-connectivity-wifi-connstate-e.md)

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [connState](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#connstate)

<!--Device-WifiLinkedInfo-connState: ConnState--><!--Device-WifiLinkedInfo-connState: ConnState-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## frequency

```TypeScript
frequency: number
```

Frequency of the Wi-Fi access point, in MHz.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [frequency](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#frequency)

<!--Device-WifiLinkedInfo-frequency: number--><!--Device-WifiLinkedInfo-frequency: number-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## ipAddress

```TypeScript
ipAddress: number
```

IP address of the Wi-Fi connection.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [ipAddress](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#ipaddress)

<!--Device-WifiLinkedInfo-ipAddress: number--><!--Device-WifiLinkedInfo-ipAddress: number-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## isHidden

```TypeScript
isHidden: boolean
```

Whether the Wi-Fi access point is a hidden network. The value **true** indicates that the Wi-Fi access point is a hidden network; the value **false** indicates the opposite.

**Type:** boolean

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [isHidden](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#ishidden)

<!--Device-WifiLinkedInfo-isHidden: boolean--><!--Device-WifiLinkedInfo-isHidden: boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## isRestricted

```TypeScript
isRestricted: boolean
```

Whether to restrict data volume at the Wi-Fi access point. The value **true** means to restrict data volume at the Wi-Fi access point, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [isRestricted](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#isrestricted)

<!--Device-WifiLinkedInfo-isRestricted: boolean--><!--Device-WifiLinkedInfo-isRestricted: boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## linkSpeed

```TypeScript
linkSpeed: number
```

Speed of the Wi-Fi access point, in Mbit/s.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [linkSpeed](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#linkspeed)

<!--Device-WifiLinkedInfo-linkSpeed: number--><!--Device-WifiLinkedInfo-linkSpeed: number-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## macAddress

```TypeScript
macAddress: string
```

MAC address of the device.

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [macAddress](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#macaddress)

<!--Device-WifiLinkedInfo-macAddress: string--><!--Device-WifiLinkedInfo-macAddress: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## rssi

```TypeScript
rssi: number
```

RSSI of the hotspot, in dBm.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [rssi](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#rssi)

<!--Device-WifiLinkedInfo-rssi: number--><!--Device-WifiLinkedInfo-rssi: number-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

Service set identifier (SSID) of the hotspot, in UTF-8 format. The maximum length is 32 bytes.

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [ssid](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#ssid)

<!--Device-WifiLinkedInfo-ssid: string--><!--Device-WifiLinkedInfo-ssid: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA
