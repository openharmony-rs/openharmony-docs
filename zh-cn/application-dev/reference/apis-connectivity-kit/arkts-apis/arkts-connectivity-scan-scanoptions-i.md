# ScanOptions

```TypeScript
interface ScanOptions
```

表示扫描选项。

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

表示扫描持续时间。单位：秒，取值范围[10, 60]，默认值为全时段扫描。取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-ScanOptions-duration?: int--><!--Device-ScanOptions-duration?: int-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## frameType

```TypeScript
frameType?: nearlinkConstant.FrameType
```

表示星闪帧类型。默认值为**FRAME_TYPE_1**。

**类型：** [nearlinkConstant.FrameType](arkts-connectivity-nearlinkconstant-frametype-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-ScanOptions-frameType?: nearlinkConstant.FrameType--><!--Device-ScanOptions-frameType?: nearlinkConstant.FrameType-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## scanMode

```TypeScript
scanMode?: ScanMode
```

表示扫描模式。默认值为'SCAN_MODE_LOW_POWER'。

**类型：** [ScanMode](arkts-connectivity-scan-scanmode-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-ScanOptions-scanMode?: ScanMode--><!--Device-ScanOptions-scanMode?: ScanMode-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base
