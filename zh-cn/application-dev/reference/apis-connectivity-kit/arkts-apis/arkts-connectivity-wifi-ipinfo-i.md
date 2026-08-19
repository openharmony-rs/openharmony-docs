# IpInfo

WLAN IP信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [IpInfo](arkts-connectivity-wifimanager-ipinfo-i.md)

<!--Device-wifi-interface IpInfo--><!--Device-wifi-interface IpInfo-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## gateway

```TypeScript
gateway: number
```

WLAN连接的网关

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [gateway](arkts-connectivity-wifimanager-ipinfo-i.md#gateway)

<!--Device-IpInfo-gateway: number--><!--Device-IpInfo-gateway: number-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

## ipAddress

```TypeScript
ipAddress: number
```

WLAN连接的IP地址

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ipAddress](arkts-connectivity-wifimanager-ipinfo-i.md#ipaddress)

<!--Device-IpInfo-ipAddress: number--><!--Device-IpInfo-ipAddress: number-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

## leaseDuration

```TypeScript
leaseDuration: number
```

WLAN连接的IP地址租约时长

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [leaseDuration](arkts-connectivity-wifimanager-ipinfo-i.md#leaseduration)

<!--Device-IpInfo-leaseDuration: number--><!--Device-IpInfo-leaseDuration: number-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

## netmask

```TypeScript
netmask: number
```

WLAN连接的网络掩码

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [netmask](arkts-connectivity-wifimanager-ipinfo-i.md#netmask)

<!--Device-IpInfo-netmask: number--><!--Device-IpInfo-netmask: number-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

## primaryDns

```TypeScript
primaryDns: number
```

WLAN连接的主DNS服务器IP地址

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [primaryDns](arkts-connectivity-wifimanager-ipinfo-i.md#primarydns)

<!--Device-IpInfo-primaryDns: number--><!--Device-IpInfo-primaryDns: number-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

## secondDns

```TypeScript
secondDns: number
```

WLAN连接的辅助DNS服务器IP地址

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [secondDns](arkts-connectivity-wifimanager-ipinfo-i.md#seconddns)

<!--Device-IpInfo-secondDns: number--><!--Device-IpInfo-secondDns: number-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

## serverIp

```TypeScript
serverIp: number
```

WLAN连接的DHCP服务器IP地址

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [serverIp](arkts-connectivity-wifimanager-ipinfo-i.md#serverip)

<!--Device-IpInfo-serverIp: number--><!--Device-IpInfo-serverIp: number-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

