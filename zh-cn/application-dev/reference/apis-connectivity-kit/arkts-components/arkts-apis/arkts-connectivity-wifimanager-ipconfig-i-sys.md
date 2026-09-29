# IpConfig（系统接口）

```TypeScript
interface IpConfig
```

IP配置信息。

**起始版本：** 9

<!--Device-wifiManager-interface IpConfig--><!--Device-wifiManager-interface IpConfig-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## dnsServers

```TypeScript
dnsServers: number[]
```

DNS服务器。

**类型：** number[]

**起始版本：** 9

<!--Device-IpConfig-dnsServers: int[]--><!--Device-IpConfig-dnsServers: int[]-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## domains

```TypeScript
domains: Array<string>
```

域信息。

**类型：** Array&lt;string&gt;

**起始版本：** 9

<!--Device-IpConfig-domains: Array<string>--><!--Device-IpConfig-domains: Array<string>-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## gateway

```TypeScript
gateway: number
```

网关。

**类型：** number

**起始版本：** 9

<!--Device-IpConfig-gateway: int--><!--Device-IpConfig-gateway: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## ipAddress

```TypeScript
ipAddress: number
```

IP地址。

**类型：** number

**起始版本：** 9

<!--Device-IpConfig-ipAddress: int--><!--Device-IpConfig-ipAddress: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## prefixLength

```TypeScript
prefixLength: number
```

掩码。

**类型：** number

**起始版本：** 9

<!--Device-IpConfig-prefixLength: int--><!--Device-IpConfig-prefixLength: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。
