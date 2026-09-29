# ScanResult

```TypeScript
interface ScanResult
```

扫描结果上报数据。

从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ScanResult](arkts-connectivity-bluetoothmanager-scanresult-i.md)

<!--Device-bluetooth-interface ScanResult--><!--Device-bluetooth-interface ScanResult-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## data

```TypeScript
data: ArrayBuffer
```

表示扫描到的设备发送的广播包。

**类型：** ArrayBuffer

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [data](arkts-connectivity-bluetoothmanager-scanresult-i.md#data)

<!--Device-ScanResult-data: ArrayBuffer--><!--Device-ScanResult-data: ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

表示扫描到的设备地址，例如："XX:XX:XX:XX:XX:XX"。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [deviceId](arkts-connectivity-bluetoothmanager-scanresult-i.md#deviceid)

<!--Device-ScanResult-deviceId: string--><!--Device-ScanResult-deviceId: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## rssi

```TypeScript
rssi: number
```

表示扫描到的设备的rssi值。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [rssi](arkts-connectivity-bluetoothmanager-scanresult-i.md#rssi)

<!--Device-ScanResult-rssi: number--><!--Device-ScanResult-rssi: number-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core
