# NetStatsInfo

```TypeScript
export interface NetStatsInfo
```

获取的历史流量信息。

**起始版本：** 22

<!--Device-statistics-export interface NetStatsInfo--><!--Device-statistics-export interface NetStatsInfo-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## rxBytes

```TypeScript
rxBytes: number
```

流量下行数据（单位：字节）。

**类型：** number

**起始版本：** 22

<!--Device-NetStatsInfo-rxBytes: long--><!--Device-NetStatsInfo-rxBytes: long-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## rxPackets

```TypeScript
rxPackets: number
```

流量下行包个数。

**类型：** number

**起始版本：** 22

<!--Device-NetStatsInfo-rxPackets: long--><!--Device-NetStatsInfo-rxPackets: long-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## txBytes

```TypeScript
txBytes: number
```

流量上行数据（单位：字节）。

**类型：** number

**起始版本：** 22

<!--Device-NetStatsInfo-txBytes: long--><!--Device-NetStatsInfo-txBytes: long-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## txPackets

```TypeScript
txPackets: number
```

流量上行包个数。

**类型：** number

**起始版本：** 22

<!--Device-NetStatsInfo-txPackets: long--><!--Device-NetStatsInfo-txPackets: long-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core
