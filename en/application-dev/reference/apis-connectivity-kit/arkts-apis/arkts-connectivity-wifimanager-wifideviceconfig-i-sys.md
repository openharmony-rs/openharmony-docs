# WifiDeviceConfig

Wi-Fi device configuration information. @typedef WifiDeviceConfig

**Since:** 12

**System capability:** SystemCapability.Communication.WiFi.STA

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## configStatus

```TypeScript
configStatus?: number
```

Device config status: 0 - enabled, 1 - disabled, 2 - permanent disabled, 3 - unknown.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## creatorUid

```TypeScript
creatorUid?: number
```

The UID of the Wi-Fi configuration creator.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## disableReason

```TypeScript
disableReason?: number
```

Disable reason

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## family

```TypeScript
family?: number
```

Static IP family: 0 - IPv4, 1 - Ipv6.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## ipType

```TypeScript
ipType?: IpType
```

IP Type

**Type:** [IpType](arkts-connectivity-wifimanager-iptype-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## isAutoConnectAllowed

```TypeScript
isAutoConnectAllowed?: boolean
```

Allow auto connect config: false - not, true - yes.

**Type:** boolean

**Since:** 17

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## isSecureWifi

```TypeScript
isSecureWifi?: boolean
```

Secure wifi detect config: false - not, true - yes.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## netId

```TypeScript
netId?: number
```

Allocated networkId

**Type:** number

**Since:** 22

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## proxyConfig

```TypeScript
proxyConfig?: WifiProxyConfig
```

Proxy config.

**Type:** [WifiProxyConfig](arkts-connectivity-wifimanager-wifiproxyconfig-i-sys.md)

**Since:** 10

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## randomMacAddr

```TypeScript
randomMacAddr?: string
```

Random mac address, the length is 6.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## randomMacType

```TypeScript
randomMacType?: number
```

Random mac type

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## staticIp

```TypeScript
staticIp?: IpConfig
```

IP config of static

**Type:** [IpConfig](arkts-connectivity-wifimanager-ipconfig-i-sys.md)

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## staticIpv6

```TypeScript
staticIpv6?: Ipv6Config
```

IPv6 config of static

**Type:** [Ipv6Config](arkts-connectivity-wifimanager-ipv6config-i-sys.md)

**Since:** 20

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.
