# IfaceInfo（系统接口）

查询网卡历史流量参数信息。

**起始版本：** 23

<!--Device-statistics-export interface IfaceInfo--><!--Device-statistics-export interface IfaceInfo-End-->

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

<!--Device-IfaceInfo-endTime: int--><!--Device-IfaceInfo-endTime: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## iface

```TypeScript
iface: string
```

查询的网卡名。

**类型：** string

**起始版本：** 23

<!--Device-IfaceInfo-iface: string--><!--Device-IfaceInfo-iface: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## startTime

```TypeScript
startTime: int
```

查询的开始时间(时间戳;单位：秒)。

**类型：** int

**起始版本：** 23

<!--Device-IfaceInfo-startTime: int--><!--Device-IfaceInfo-startTime: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

