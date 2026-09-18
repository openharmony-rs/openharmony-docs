# ScanOptions

BLE扫描的配置参数。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## dutyMode

```TypeScript
dutyMode?: ScanDuty
```

扫描模式，默认值为SCAN_MODE_LOW_POWER。

**类型：** [ScanDuty](arkts-connectivity-ble-scanduty-e.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## interval

```TypeScript
interval?: number
```

扫描结果上报的延迟时间，单位：ms，默认值为0。搭配[ScanReportMode](arkts-connectivity-ble-scanreportmode-e.md)使用。

在常规或围栏扫描上报模式下，该值不生效，扫描到符合过滤条件的广播报文后立即上报。在批量扫描上报模式下，该值生效，扫描到符合过滤条件的广播报文后，会存入缓存队列，延迟上报。若不设置该值或设置在[0, 5000)范围内，蓝牙子系统会默认设置延迟时间为5000ms。延迟时间内，若符合过滤条件的广播报文数量超过硬件缓存能力，蓝牙子系统会提前上报扫描结果。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## isExtended

```TypeScript
isExtended?: boolean
```

是否使用扩展扫描。false表示使用传统扫描；true表示使用扩展扫描。默认值为false。

**起始版本**：26.0.0

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## matchMode

```TypeScript
matchMode?: MatchMode
```

硬件的过滤匹配模式，默认值为MATCH_MODE_AGGRESSIVE。

**类型：** [MatchMode](arkts-connectivity-ble-matchmode-e.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## phyType

```TypeScript
phyType?: PhyType
```

扫描中使用的物理通道类型，默认值为PHY_LE_1M。

**类型：** [PhyType](arkts-connectivity-ble-phytype-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## reportMode

```TypeScript
reportMode?: ScanReportMode
```

扫描结果数据上报模式，默认值为NORMAL。

**类型：** [ScanReportMode](arkts-connectivity-ble-scanreportmode-e.md)

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
