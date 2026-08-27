# WifiLinkedInfo

WLAN连接信息。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## chload

```TypeScript
chload: number
```

此WLAN连接的负载值。值越大表示负载越高。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## isHiLinkProNetwork

```TypeScript
isHiLinkProNetwork?: boolean
```

WLAN热点是否是HiLinkPro网络。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## networkId

```TypeScript
networkId: number
```

WLAN连接的唯一标识ID。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## snr

```TypeScript
snr: number
```

此WLAN连接的信噪比（SNR）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## suppState

```TypeScript
suppState: SuppState
```

此WLAN连接的supplicant状态。

**类型：** SuppState

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## wifiTxRxValid

```TypeScript
wifiTxRxValid?: boolean
```

WLAN的Tx和Rx是否都正常工作

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。
