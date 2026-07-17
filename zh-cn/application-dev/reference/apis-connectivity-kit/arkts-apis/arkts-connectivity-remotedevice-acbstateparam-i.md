# AcbStateParam

ACB连接状态参数。

**起始版本：** 26.0.0

<!--Device-remoteDevice-interface AcbStateParam--><!--Device-remoteDevice-interface AcbStateParam-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

设备地址。长度必须为17，由16进制数字和冒号组成，形如 "11:22:33:AA:BB:FF"。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AcbStateParam-address: string--><!--Device-AcbStateParam-address: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## state

```TypeScript
state: AcbState
```

ACB连接状态

**类型：** AcbState

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AcbStateParam-state: AcbState--><!--Device-AcbStateParam-state: AcbState-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

