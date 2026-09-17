# AdvertisingStateChangeInfo

表示广播启停状态变化信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { advertising } from '@kit.ConnectivityKit';
```

## advertisingId

```TypeScript
advertisingId: number
```

表示广播ID。取值范围[0, 255]。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## state

```TypeScript
state: AdvertisingState
```

表示当前广播状态。

**类型：** [AdvertisingState](arkts-connectivity-advertising-advertisingstate-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base
