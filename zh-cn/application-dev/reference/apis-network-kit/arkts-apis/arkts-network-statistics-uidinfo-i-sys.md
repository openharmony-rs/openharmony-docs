# UidInfo（系统接口）

查询应用历史流量参数信息。

**起始版本：** 23

<!--Device-statistics-export interface UidInfo--><!--Device-statistics-export interface UidInfo-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## ifaceInfo

```TypeScript
ifaceInfo: IfaceInfo
```

需查询的网卡和时间参数信息。

**类型：** [IfaceInfo](arkts-network-statistics-ifaceinfo-i-sys.md)

**起始版本：** 23

<!--Device-UidInfo-ifaceInfo: IfaceInfo--><!--Device-UidInfo-ifaceInfo: IfaceInfo-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid: int
```

需查询的应用 uid。

**类型：** int

**起始版本：** 23

<!--Device-UidInfo-uid: int--><!--Device-UidInfo-uid: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

