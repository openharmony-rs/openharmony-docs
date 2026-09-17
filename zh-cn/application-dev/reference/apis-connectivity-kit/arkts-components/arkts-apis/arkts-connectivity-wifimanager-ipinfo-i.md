# IpInfo

IPV4信息。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## gateway

```TypeScript
gateway: number
```

网关。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## ipAddress

```TypeScript
ipAddress: number
```

IP地址。（ipAddress值为number类型，需要转换为IP常用格式，具体请参考[IP格式转换](https://developer.huawei.com/consumer/cn/doc/harmonyos-faqs/faqs-connectivity-4)）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## leaseDuration

```TypeScript
leaseDuration: number
```

IP地址租用时长，单位：秒。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## netmask

```TypeScript
netmask: number
```

掩码。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## primaryDns

```TypeScript
primaryDns: number
```

主DNS服务器IP地址。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## secondDns

```TypeScript
secondDns: number
```

备DNS服务器IP地址。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## serverIp

```TypeScript
serverIp: number
```

DHCP服务端IP地址。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA
