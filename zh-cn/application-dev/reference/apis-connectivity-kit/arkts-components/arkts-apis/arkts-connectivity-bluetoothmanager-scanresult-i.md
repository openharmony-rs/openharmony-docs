# ScanResult

扫描结果上报数据。

从API version 9开始支持，从API version 10开始废弃。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [ScanResult](arkts-connectivity-ble-scanresult-i.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## data

```TypeScript
data: ArrayBuffer
```

表示扫描到的设备发送的广播包。

**类型：** ArrayBuffer

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [data](arkts-connectivity-ble-scanresult-i.md#data)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

表示扫描到的设备地址，例如："XX:XX:XX:XX:XX:XX"。

**类型：** string

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [deviceId](arkts-connectivity-ble-scanresult-i.md#deviceid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## rssi

```TypeScript
rssi: number
```

表示扫描到的设备的rssi值。

**类型：** number

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [rssi](arkts-connectivity-ble-scanresult-i.md#rssi)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
