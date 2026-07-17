# ScanOptions

扫描参数。

**起始版本：** 26.0.0

<!--Device-scan-interface ScanOptions--><!--Device-scan-interface ScanOptions-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { scan } from '@kit.ConnectivityKit';
```

## duration

```TypeScript
duration?: number
```

扫描时长。“持续时间”，单位为秒，有效范围为10s~60s。如果不设置“持续时间”，则会一直扫描。单位为： 秒，取值应为[10,60]内的整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScanOptions-duration?: int--><!--Device-ScanOptions-duration?: int-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## scanMode

```TypeScript
scanMode?: ScanMode
```

扫描模式。如果未设置“scanMode”，则默认值为“SCAN_MODE_LOW_POWER”。默认值： SCAN_MODE_LOW_POWER。

**类型：** ScanMode

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScanOptions-scanMode?: ScanMode--><!--Device-ScanOptions-scanMode?: ScanMode-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

