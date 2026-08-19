# NetworkInfo（系统接口）

网络信息。

**起始版本：** 23

<!--Device-statistics-export interface NetworkInfo--><!--Device-statistics-export interface NetworkInfo-End-->

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

结束时间戳（单位：秒）。

**类型：** int

**起始版本：** 23

<!--Device-NetworkInfo-endTime: int--><!--Device-NetworkInfo-endTime: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## simId

```TypeScript
simId?: int
```

SIM卡ID。默认值为uint32_t类型最大值。 **注意：** 当type为蜂窝网络时，需指定本字段。

**类型：** int

**起始版本：** 23

<!--Device-NetworkInfo-simId?: int--><!--Device-NetworkInfo-simId?: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## startTime

```TypeScript
startTime: int
```

开始时间戳（单位：秒）。

**类型：** int

**起始版本：** 23

<!--Device-NetworkInfo-startTime: int--><!--Device-NetworkInfo-startTime: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type: NetBearType
```

网络类型。 **注意：** 当type为蜂窝网络时，需指定simId字段。

**类型：** NetBearType

**起始版本：** 23

<!--Device-NetworkInfo-type: NetBearType--><!--Device-NetworkInfo-type: NetBearType-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

