# AdvertiseSetting

描述蓝牙低功耗设备发送广播的参数。

从API version 9开始支持，从API version 10开始废弃。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [AdvertiseSetting](arkts-connectivity-ble-advertisesetting-i.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## connectable

```TypeScript
connectable?: boolean
```

表示是否是可连接广播，默认值设置为true。

**类型：** boolean

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [connectable](arkts-connectivity-ble-advertisesetting-i.md#connectable)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## interval

```TypeScript
interval?: number
```

表示广播间隔，最小值设置32个slot表示20ms，最大值设置16384个slot，默认值设置为1600个slot表示1s。

**类型：** number

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [interval](arkts-connectivity-ble-advertisesetting-i.md#interval)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## txPower

```TypeScript
txPower?: number
```

表示发送功率，最小值设置-127，最大值设置1，默认值设置-7，单位dBm。

**类型：** number

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [txPower](arkts-connectivity-ble-advertisesetting-i.md#txpower)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
