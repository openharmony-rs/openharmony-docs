# WifiLinkedInfo

Wi-Fi连接信息。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## chload

```TypeScript
chload: number
```

连接负载，值越大表示负载越高。

**系统接口：** 此接口为系统接口。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## isHiLinkProNetwork

```TypeScript
isHiLinkProNetwork?: boolean
```

是否是HiLinkPro网络。true表示是HiLinkPro网络，false表示不是HiLinkPro网络。

**系统接口：** 此接口为系统接口。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## networkId

```TypeScript
networkId: number
```

网络配置ID。

**系统接口：** 此接口为系统接口。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## snr

```TypeScript
snr: number
```

信噪比，单位：dB。

**系统接口：** 此接口为系统接口。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## suppState

```TypeScript
suppState: SuppState
```

请求状态。

**系统接口：** 此接口为系统接口。

**类型：** [SuppState](arkts-connectivity-wifimanager-suppstate-e-sys.md)

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## wifiTxRxValid

```TypeScript
wifiTxRxValid?: boolean
```

。用于指示Wi-Fi的发送（Tx, Transmitting）和接收（Rx, Receiving）功能是否都在正常工作。

**系统接口：** 此接口为系统接口。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。
