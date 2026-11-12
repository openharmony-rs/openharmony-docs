# InterceptedRecord（系统接口）

```TypeScript
interface InterceptedRecord
```

拦截记录信息结构。

**起始版本：** 14

<!--Device-netFirewall-interface InterceptedRecord--><!--Device-netFirewall-interface InterceptedRecord-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## appUid

```TypeScript
appUid?: number
```

应用程序或服务UID，默认值为0。

**类型：** number

**起始版本：** 14

<!--Device-InterceptedRecord-appUid?: int--><!--Device-InterceptedRecord-appUid?: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。

## domain

```TypeScript
domain?: string
```

域名。

**类型：** string

**起始版本：** 14

<!--Device-InterceptedRecord-domain?: string--><!--Device-InterceptedRecord-domain?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。

## localIp

```TypeScript
localIp?: string
```

本地IP。

**类型：** string

**起始版本：** 14

<!--Device-InterceptedRecord-localIp?: string--><!--Device-InterceptedRecord-localIp?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。

## localPort

```TypeScript
localPort?: number
```

本地端口，默认值为0。

**类型：** number

**起始版本：** 14

<!--Device-InterceptedRecord-localPort?: int--><!--Device-InterceptedRecord-localPort?: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。

## protocol

```TypeScript
protocol?: number
```

传输层协议，默认值为0。

**类型：** number

**起始版本：** 14

<!--Device-InterceptedRecord-protocol?: int--><!--Device-InterceptedRecord-protocol?: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。

## remoteIp

```TypeScript
remoteIp?: string
```

远端IP。

**类型：** string

**起始版本：** 14

<!--Device-InterceptedRecord-remoteIp?: string--><!--Device-InterceptedRecord-remoteIp?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。

## remotePort

```TypeScript
remotePort?: number
```

远端端口，默认值为0。

**类型：** number

**起始版本：** 14

<!--Device-InterceptedRecord-remotePort?: int--><!--Device-InterceptedRecord-remotePort?: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。

## time

```TypeScript
time: number
```

时间戳。

**类型：** number

**起始版本：** 14

<!--Device-InterceptedRecord-time: int--><!--Device-InterceptedRecord-time: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。
