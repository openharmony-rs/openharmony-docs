# WifiLinkedInfo

```TypeScript
interface WifiLinkedInfo
```

提供Wi-Fi连接的相关信息。

> **说明：** 
> 
> 从API version 6开始支持，从API version 9开始废弃。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [WifiLinkedInfo](arkts-connectivity-wifimanager-wifilinkedinfo-i.md)

<!--Device-wifi-interface WifiLinkedInfo--><!--Device-wifi-interface WifiLinkedInfo-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## chload

```TypeScript
chload: number
```

连接负载，值越大表示负载越高。

**系统接口：** 此接口为系统接口。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [chload](arkts-connectivity-wifimanager-wifilinkedinfo-i-sys.md#chload)

<!--Device-WifiLinkedInfo-chload: number--><!--Device-WifiLinkedInfo-chload: number-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## networkId

```TypeScript
networkId: number
```

网络配置ID。

**系统接口：** 此接口为系统接口。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [networkId](arkts-connectivity-wifimanager-wifilinkedinfo-i-sys.md#networkid)

<!--Device-WifiLinkedInfo-networkId: number--><!--Device-WifiLinkedInfo-networkId: number-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## snr

```TypeScript
snr: number
```

信噪比，单位：dB。

**系统接口：** 此接口为系统接口。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [snr](arkts-connectivity-wifimanager-wifilinkedinfo-i-sys.md#snr)

<!--Device-WifiLinkedInfo-snr: number--><!--Device-WifiLinkedInfo-snr: number-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## suppState

```TypeScript
suppState: SuppState
```

请求状态。

**系统接口：** 此接口为系统接口。

**类型：** [SuppState](arkts-connectivity-wifi-suppstate-e-sys.md)

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [suppState](arkts-connectivity-wifimanager-wifilinkedinfo-i-sys.md#suppstate)

<!--Device-WifiLinkedInfo-suppState: SuppState--><!--Device-WifiLinkedInfo-suppState: SuppState-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。
