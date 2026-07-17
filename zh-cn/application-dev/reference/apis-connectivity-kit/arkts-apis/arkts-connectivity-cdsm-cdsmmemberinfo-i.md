# CdsmMemberInfo

描述合作设备集的成员信息。

**起始版本：** 26.0.0

<!--Device-cdsm-interface CdsmMemberInfo--><!--Device-cdsm-interface CdsmMemberInfo-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { cdsm } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

设备地址。长度必须为17，由16进制数字和冒号组成，形如 "11:22:33:AA:BB:FF"。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CdsmMemberInfo-address: string--><!--Device-CdsmMemberInfo-address: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## state

```TypeScript
state: CdsmConnectionState
```

成员的连接状态。

**类型：** CdsmConnectionState

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CdsmMemberInfo-state: CdsmConnectionState--><!--Device-CdsmMemberInfo-state: CdsmConnectionState-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

