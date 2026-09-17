# ScanReport

上报的扫描数据。

**起始版本：** 15

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## reportType

```TypeScript
reportType: ScanReportType
```

扫描结果上报类型。

**类型：** [ScanReportType](arkts-connectivity-ble-scanreporttype-e.md)

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## scanResult

```TypeScript
scanResult: Array<ScanResult>
```

扫描到符合过滤条件的BLE广播报文后，上报的扫描数据。

**类型：** Array&lt;[ScanResult](arkts-connectivity-ble-scanresult-i.md)&gt;

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
