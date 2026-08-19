# IpConfig（系统接口）

WLAN IP配置信息。

**起始版本：** 23

<!--Device-wifiManager-interface IpConfig--><!--Device-wifiManager-interface IpConfig-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## dnsServers

```TypeScript
dnsServers: int[]
```

DNS服务器。

**类型：** int[]

**起始版本：** 23

<!--Device-IpConfig-dnsServers: int[]--><!--Device-IpConfig-dnsServers: int[]-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## domains

```TypeScript
domains: Array<string>
```

域名。

**类型：** Array&lt;string&gt;

**起始版本：** 23

<!--Device-IpConfig-domains: Array<string>--><!--Device-IpConfig-domains: Array<string>-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## gateway

```TypeScript
gateway: int
```

网关。

**类型：** int

**起始版本：** 23

<!--Device-IpConfig-gateway: int--><!--Device-IpConfig-gateway: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## ipAddress

```TypeScript
ipAddress: int
```

IP地址。

**类型：** int

**起始版本：** 23

<!--Device-IpConfig-ipAddress: int--><!--Device-IpConfig-ipAddress: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## prefixLength

```TypeScript
prefixLength: int
```

前缀长度。

**类型：** int

**起始版本：** 23

<!--Device-IpConfig-prefixLength: int--><!--Device-IpConfig-prefixLength: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

