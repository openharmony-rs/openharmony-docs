# ScanOptions

扫描的配置参数。

从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ScanOptions](arkts-connectivity-bluetoothmanager-scanoptions-i.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## dutyMode

```TypeScript
dutyMode?: ScanDuty
```

表示扫描模式，默认值为SCAN_MODE_LOW_POWER。

**类型：** [ScanDuty](arkts-connectivity-bluetooth-scanduty-e.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [dutyMode](arkts-connectivity-bluetoothmanager-scanoptions-i.md#dutymode)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## interval

```TypeScript
interval?: number
```

表示扫描结果上报延迟时间，默认值为0。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [interval](arkts-connectivity-bluetoothmanager-scanoptions-i.md#interval)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## matchMode

```TypeScript
matchMode?: MatchMode
```

表示硬件的过滤匹配模式，默认值为MATCH_MODE_AGGRESSIVE。

**类型：** [MatchMode](arkts-connectivity-bluetooth-matchmode-e.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [matchMode](arkts-connectivity-bluetoothmanager-scanoptions-i.md#matchmode)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
