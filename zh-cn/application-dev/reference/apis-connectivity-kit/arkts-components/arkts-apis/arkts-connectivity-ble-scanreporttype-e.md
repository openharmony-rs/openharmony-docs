# ScanReportType

枚举，扫描结果上报类型。

**起始版本：** 15

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## ON_FOUND

```TypeScript
ON_FOUND = 1
```

扫描到符合过滤条件的BLE广播报文时，触发上报，可搭配常规和围栏上报模式使用。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## ON_LOST

```TypeScript
ON_LOST = 2
```

当不再扫描到符合过滤条件的BLE广播报文时，触发上报，只搭配围栏上报模式使用。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## ON_BATCH

```TypeScript
ON_BATCH = 3
```

扫描到符合过滤条件的BLE广播报文时，以[ScanOptions](arkts-connectivity-ble-scanoptions-i.md)中的interval字段为周期触发上报，只搭配批量上报模式（[BATCH](arkts-connectivity-ble-scanreportmode-e.md)）使用。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
