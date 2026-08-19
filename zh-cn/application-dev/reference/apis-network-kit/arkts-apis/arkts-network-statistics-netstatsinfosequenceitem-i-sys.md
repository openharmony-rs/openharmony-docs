# NetStatsInfoSequenceItem（系统接口）

包含开始时间和结束时间的[NetStatsInfo](arkts-network-statistics-netstatsinfo-i-sys.md)参数。

**起始版本：** 23

<!--Device-statistics-export interface NetStatsInfoSequenceItem--><!--Device-statistics-export interface NetStatsInfoSequenceItem-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## endTime

```TypeScript
endTime: int
```

查询的结束时间(时间戳;单位：秒)。

**类型：** int

**起始版本：** 23

<!--Device-NetStatsInfoSequenceItem-endTime: int--><!--Device-NetStatsInfoSequenceItem-endTime: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## info

```TypeScript
info: NetStatsInfo
```

获取的历史流量信息。

**类型：** [NetStatsInfo](arkts-network-statistics-netstatsinfo-i-sys.md)

**起始版本：** 23

<!--Device-NetStatsInfoSequenceItem-info: NetStatsInfo--><!--Device-NetStatsInfoSequenceItem-info: NetStatsInfo-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## startTime

```TypeScript
startTime: int
```

查询的开始时间(时间戳;单位：秒)。

**类型：** int

**起始版本：** 23

<!--Device-NetStatsInfoSequenceItem-startTime: int--><!--Device-NetStatsInfoSequenceItem-startTime: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

