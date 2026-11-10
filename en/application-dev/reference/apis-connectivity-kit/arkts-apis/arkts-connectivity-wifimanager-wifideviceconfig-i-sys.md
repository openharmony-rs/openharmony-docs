# WifiDeviceConfig (System API)

```TypeScript
interface WifiDeviceConfig
```

Represents the Wi-Fi configuration information.

**Since:** 9

<!--Device-wifiManager-interface WifiDeviceConfig--><!--Device-wifiManager-interface WifiDeviceConfig-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## configStatus

```TypeScript
configStatus?: number
```

Status indicating whether the current network can be selected.

**1**: network selection allowed

**2**: network selection forbidden

**3**: network selection permanently forbidden

4: unknown

**Type:** number

**Since:** 12

<!--Device-WifiDeviceConfig-configStatus?: int--><!--Device-WifiDeviceConfig-configStatus?: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## creatorUid

```TypeScript
creatorUid?: number
```

ID of the creator.

**Type:** number

**Since:** 9

<!--Device-WifiDeviceConfig-creatorUid?: int--><!--Device-WifiDeviceConfig-creatorUid?: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## disableReason

```TypeScript
disableReason?: number
```

Reason for disabling Wi-Fi.

**-1**: unknown reason

**0**: not disabled

**1**: association refused

**2**: authentication failed

**3**: DHCP failure

**4**: no Internet connection

**5**: no authentication credentials

**6**: no Internet connection permanently

**7**: disabled by Wi-Fi manager

**8**: disabled due to incorrect password

**9**: authentication without subscription

**10**: private EAP authentication error

**11**: network not found

**12**: consecutive failures

**13**: disabled by the system

**14**: EAP-AKA authentication failed

**15**: association removed

**16**: maximum number of forbidden network selections

**Type:** number

**Since:** 9

<!--Device-WifiDeviceConfig-disableReason?: int--><!--Device-WifiDeviceConfig-disableReason?: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## family

```TypeScript
family?: number
```

Static IP family: 0 - IPv4, 1 - Ipv6.

**Type:** number

**Since:** 20

<!--Device-WifiDeviceConfig-family?: int--><!--Device-WifiDeviceConfig-family?: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## ipType

```TypeScript
ipType?: IpType
```

IP address type.

**Type:** [IpType](arkts-connectivity-wifimanager-iptype-e-sys.md)

**Since:** 9

<!--Device-WifiDeviceConfig-ipType?: IpType--><!--Device-WifiDeviceConfig-ipType?: IpType-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## isAutoConnectAllowed

```TypeScript
isAutoConnectAllowed?: boolean
```

Whether automatic connection is allowed. The value **true** indicates that automatic connection is allowed, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 17

<!--Device-WifiDeviceConfig-isAutoConnectAllowed?: boolean--><!--Device-WifiDeviceConfig-isAutoConnectAllowed?: boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## isSecureWifi

```TypeScript
isSecureWifi?: boolean
```

Whether the Wi-Fi connection is secure. The value **true** indicates that the Wi-Fi connection is secure, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 20

<!--Device-WifiDeviceConfig-isSecureWifi?: boolean--><!--Device-WifiDeviceConfig-isSecureWifi?: boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## proxyConfig

```TypeScript
proxyConfig?: WifiProxyConfig
```

Proxy configuration.

**Type:** [WifiProxyConfig](arkts-connectivity-wifimanager-wifiproxyconfig-i-sys.md)

**Since:** 10

<!--Device-WifiDeviceConfig-proxyConfig?: WifiProxyConfig--><!--Device-WifiDeviceConfig-proxyConfig?: WifiProxyConfig-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## randomMacAddr

```TypeScript
randomMacAddr?: string
```

MAC address.

**Type:** string

**Since:** 9

<!--Device-WifiDeviceConfig-randomMacAddr?: string--><!--Device-WifiDeviceConfig-randomMacAddr?: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## randomMacType

```TypeScript
randomMacType?: number
```

MAC address type.

The value **0** indicates a random MAC address, and the value **1** indicates a device MAC address.

**Type:** number

**Since:** 9

<!--Device-WifiDeviceConfig-randomMacType?: int--><!--Device-WifiDeviceConfig-randomMacType?: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## staticIp

```TypeScript
staticIp?: IpConfig
```

Static IP address information.

**Type:** [IpConfig](arkts-connectivity-wifimanager-ipconfig-i-sys.md)

**Since:** 9

<!--Device-WifiDeviceConfig-staticIp?: IpConfig--><!--Device-WifiDeviceConfig-staticIp?: IpConfig-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## staticIpv6

```TypeScript
staticIpv6?: Ipv6Config
```

IPv6 config of static

**Type:** [Ipv6Config](arkts-connectivity-wifimanager-ipv6config-i-sys.md)

**Since:** 20

<!--Device-WifiDeviceConfig-staticIpv6?: Ipv6Config--><!--Device-WifiDeviceConfig-staticIpv6?: Ipv6Config-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.
