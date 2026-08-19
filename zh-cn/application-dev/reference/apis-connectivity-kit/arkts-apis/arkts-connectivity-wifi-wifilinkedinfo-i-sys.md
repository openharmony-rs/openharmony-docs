# WifiLinkedInfo

WLAN连接信息。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [WifiLinkedInfo](arkts-connectivity-wifimanager-wifilinkedinfo-i.md)

<!--Device-wifi-interface WifiLinkedInfo--><!--Device-wifi-interface WifiLinkedInfo-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## chload

```TypeScript
chload: number
```

此WLAN连接的负载值。值越大表示负载越高。

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

WLAN连接的ID(唯一标识)。

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

此WLAN连接的信噪比(SNR)。

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

此WLAN连接的 supplicant 状态。

**类型：** SuppState

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [suppState](arkts-connectivity-wifimanager-wifilinkedinfo-i-sys.md#suppstate)

<!--Device-WifiLinkedInfo-suppState: SuppState--><!--Device-WifiLinkedInfo-suppState: SuppState-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

