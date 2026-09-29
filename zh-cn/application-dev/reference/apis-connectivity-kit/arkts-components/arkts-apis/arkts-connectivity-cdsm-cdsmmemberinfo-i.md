# CdsmMemberInfo

```TypeScript
interface CdsmMemberInfo
```

表示合作设备集合的成员信息。

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

成员设备地址。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CdsmMemberInfo-address: string--><!--Device-CdsmMemberInfo-address: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## state

```TypeScript
state: CdsmConnectionState
```

成员设备连接状态。

**类型：** [CdsmConnectionState](arkts-connectivity-cdsm-cdsmconnectionstate-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CdsmMemberInfo-state: CdsmConnectionState--><!--Device-CdsmMemberInfo-state: CdsmConnectionState-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base
