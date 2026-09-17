# ScanReportMode

枚举，扫描结果上报模式。

<!--Table: 20%; 10%; 70%-->

**起始版本：** 15

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## NORMAL

```TypeScript
NORMAL = 1
```

常规扫描上报模式，扫描到符合过滤条件的BLE广播报文后就会立刻上报。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## BATCH

```TypeScript
BATCH = 2
```

批量扫描上报模式。

该模式需要使用[BleScanner](arkts-connectivity-ble-blescanner-i.md)类下的接口发起扫描。该模式可通过降低蓝牙芯片上报扫描结果频率，使系统更长时间地保持在休眠状态，从而降低整机功耗。该模式下，扫描到符合过滤条件的BLE广播报文后不会立刻上报，需要缓存一段时间（[ScanOptions](arkts-connectivity-ble-scanoptions-i.md)中的interval字段）后上报。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## FENCE_SENSITIVITY_LOW

```TypeScript
FENCE_SENSITIVITY_LOW = 10
```

低灵敏度围栏上报模式。

围栏模式表示只在广播进入或离开围栏时上报。扫描到的广播信号强度高且广播数量多时，可进入低灵敏度围栏。首次扫描到广播即进入围栏，触发一次上报。一段时间内扫描不到广播即离开围栏，触发一次上报。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## FENCE_SENSITIVITY_HIGH

```TypeScript
FENCE_SENSITIVITY_HIGH = 11
```

高灵敏度围栏上报模式。

围栏模式表示只在广播进入或离开围栏时上报。扫描到的广播信号强度低且广播数量少时，可进入高灵敏度围栏。首次扫描到广播即进入围栏，触发一次上报。一段时间内扫描不到广播即离开围栏，触发一次上报。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
