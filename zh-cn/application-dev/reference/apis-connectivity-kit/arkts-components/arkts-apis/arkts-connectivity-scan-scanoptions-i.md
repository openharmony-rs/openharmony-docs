# ScanOptions

表示扫描选项。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { scan } from '@kit.ConnectivityKit';
```

## duration

```TypeScript
duration?: number
```

表示扫描持续时间。单位：秒，取值范围[10, 60]，默认值为全时段扫描。取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## scanMode

```TypeScript
scanMode?: ScanMode
```

表示扫描模式。默认值为'SCAN_MODE_LOW_POWER'。

**类型：** [ScanMode](arkts-connectivity-scan-scanmode-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base
