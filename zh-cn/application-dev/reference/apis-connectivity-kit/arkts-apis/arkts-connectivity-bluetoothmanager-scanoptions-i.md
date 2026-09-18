# ScanOptions

扫描的配置参数。

从API version 9开始支持，从API version 10开始废弃。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [ScanOptions](arkts-connectivity-ble-scanoptions-i.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## dutyMode

```TypeScript
dutyMode?: ScanDuty
```

表示扫描模式，默认值为SCAN_MODE_LOW_POWER。

**类型：** [ScanDuty](arkts-connectivity-bluetoothmanager-scanduty-e.md)

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [dutyMode](arkts-connectivity-ble-scanoptions-i.md#dutymode)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## interval

```TypeScript
interval?: number
```

表示扫描结果上报延迟时间，默认值为0。

**类型：** number

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [interval](arkts-connectivity-ble-scanoptions-i.md#interval)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## matchMode

```TypeScript
matchMode?: MatchMode
```

表示硬件的过滤匹配模式，默认值为MATCH_MODE_AGGRESSIVE。

**类型：** [MatchMode](arkts-connectivity-bluetoothmanager-matchmode-e.md)

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [matchMode](arkts-connectivity-ble-scanoptions-i.md#matchmode)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
