# CdsmInfo

```TypeScript
interface CdsmInfo
```

表示合作设备集合信息。

**起始版本：** 26.0.0

<!--Device-cdsm-interface CdsmInfo--><!--Device-cdsm-interface CdsmInfo-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { cdsm } from '@kit.ConnectivityKit';
```

## members

```TypeScript
members: CdsmMemberInfo[]
```

合作设备集合的成员信息数组，每个成员包含设备地址及其连接状态。

**类型：** [CdsmMemberInfo](arkts-connectivity-cdsm-cdsmmemberinfo-i.md)[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CdsmInfo-members: CdsmMemberInfo[]--><!--Device-CdsmInfo-members: CdsmMemberInfo[]-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base
