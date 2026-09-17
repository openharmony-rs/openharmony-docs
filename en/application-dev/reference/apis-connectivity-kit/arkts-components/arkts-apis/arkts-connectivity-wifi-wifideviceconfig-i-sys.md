# WifiDeviceConfig

Wi-Fi device configuration information.

@interface WifiDeviceConfig

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i.md)

**System capability:** SystemCapability.Communication.WiFi.STA

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## creatorUid

```TypeScript
creatorUid: number
```

The UID of the Wi-Fi configuration creator

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [creatorUid](arkts-connectivity-wifimanager-wifideviceconfig-i-sys.md#creatoruid)

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## disableReason

```TypeScript
disableReason: number
```

Disable reason

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [disableReason](arkts-connectivity-wifimanager-wifideviceconfig-i-sys.md#disablereason)

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## ipType

```TypeScript
ipType: IpType
```

IP Type

**Type:** [IpType](arkts-connectivity-wifi-iptype-e-sys.md)

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [ipType](arkts-connectivity-wifimanager-wifideviceconfig-i-sys.md#iptype)

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## netId

```TypeScript
netId: number
```

Allocated networkId

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [netId](arkts-connectivity-wifimanager-wifideviceconfig-i-sys.md#netid)

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## randomMacAddr

```TypeScript
randomMacAddr: string
```

Random mac address, the length is 6

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [randomMacAddr](arkts-connectivity-wifimanager-wifideviceconfig-i-sys.md#randommacaddr)

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## randomMacType

```TypeScript
randomMacType: number
```

Random mac type

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [randomMacType](arkts-connectivity-wifimanager-wifideviceconfig-i-sys.md#randommactype)

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## staticIp

```TypeScript
staticIp: IpConfig
```

IP config of static

**Type:** [IpConfig](arkts-connectivity-wifi-ipconfig-i-sys.md)

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [staticIp](arkts-connectivity-wifimanager-wifideviceconfig-i-sys.md#staticip)

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.
