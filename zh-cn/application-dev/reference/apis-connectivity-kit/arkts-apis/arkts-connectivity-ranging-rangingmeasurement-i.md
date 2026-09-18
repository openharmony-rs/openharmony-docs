# RangingMeasurement

描述测量结果，包含测量值和对应的置信度。测量结果可用于距离测量或角度测量。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## 导入模块

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## confidence

```TypeScript
confidence: RangingConfidence
```

测量结果的置信度，表示本次测量值的可信程度。

**类型：** [RangingConfidence](arkts-connectivity-ranging-rangingconfidence-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## value

```TypeScript
value: number
```

测量结果值。距离测量时单位：cm，角度测量时单位：度。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core
