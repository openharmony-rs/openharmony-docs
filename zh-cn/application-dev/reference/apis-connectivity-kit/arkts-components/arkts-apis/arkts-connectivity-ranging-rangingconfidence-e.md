# RangingConfidence

枚举，测距测量置信度，表示测量结果值的可信程度。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## HIGH

```TypeScript
HIGH = 0
```

高置信度测量，测量值可信度高，可直接使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## MEDIUM

```TypeScript
MEDIUM = 1
```

中置信度测量，测量值有一定可信度，建议结合其他信息综合判断。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## LOW

```TypeScript
LOW = 2
```

低置信度测量，测量值可信度低，建议谨慎使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core
