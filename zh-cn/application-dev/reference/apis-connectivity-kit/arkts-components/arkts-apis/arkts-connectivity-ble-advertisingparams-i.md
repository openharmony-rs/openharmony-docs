# AdvertisingParams

首次启动BLE广播时设置的参数。

蓝牙协议规定，在扩展广播模式下（即广播发送参数[isExtended](arkts-connectivity-ble-advertisesetting-i.md)为true时），广播发送参数[connectable](arkts-connectivity-ble-advertisesetting-i.md)和扫描回复广播报文[advResponse](arkts-connectivity-ble-startadvertising-f.md)不能共存（即[connectable](arkts-connectivity-ble-advertisesetting-i.md)为true，[advResponse](arkts-connectivity-ble-startadvertising-f.md)需为空；[connectable](arkts-connectivity-ble-advertisesetting-i.md)为false，[advResponse](arkts-connectivity-ble-startadvertising-f.md)不能为空）。

**起始版本：** 11

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## advertisingData

```TypeScript
advertisingData: AdvertiseData
```

需要发送的广播报文数据内容。

**类型：** [AdvertiseData](arkts-connectivity-ble-advertisedata-i.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## advertisingResponse

```TypeScript
advertisingResponse?: AdvertiseData
```

回复扫描请求的广播报文数据内容。若不填写，则不携带扫描回复广播报文。在扩展广播模式下（isExtended为true时），与connectable不能共存：connectable为true时本参数需为空，connectable为false时本参数不能为空。

**类型：** [AdvertiseData](arkts-connectivity-ble-advertisedata-i.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## advertisingSettings

```TypeScript
advertisingSettings: AdvertiseSetting
```

广播的发送参数。

**类型：** [AdvertiseSetting](arkts-connectivity-ble-advertisesetting-i.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## duration

```TypeScript
duration?: number
```

发送广播的持续时间。取值范围：[1, 65535]，单位：10ms。

如果未指定此参数或者将其设置为0，则会持续发送广播。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
