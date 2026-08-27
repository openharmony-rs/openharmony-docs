# AcbStateParam

订阅的逻辑链路连接状态变化事件上报结果。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

设备地址，表示和该设备的逻辑链路连接状态发生变化。地址格式参考：11:22:33:AA:BB:FF。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## state

```TypeScript
state: AcbState
```

当前逻辑链路连接状态。

**类型：** AcbState

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base
