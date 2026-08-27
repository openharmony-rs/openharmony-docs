# NetworkInfo

网络信息。

**起始版本：** 22

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
```

## endTime

```TypeScript
endTime: number
```

结束时间戳（单位：秒）。

**类型：** number

**起始版本：** 22

**系统能力：** SystemCapability.Communication.NetManager.Core

## simId

```TypeScript
simId?: number
```

SIM卡ID。默认值为uint32_t类型最大值。  
**注意：** 当type为蜂窝网络时，需指定本字段。

**类型：** number

**起始版本：** 22

**系统能力：** SystemCapability.Communication.NetManager.Core

## startTime

```TypeScript
startTime: number
```

开始时间戳（单位：秒）。

**类型：** number

**起始版本：** 22

**系统能力：** SystemCapability.Communication.NetManager.Core

## type

```TypeScript
type: NetBearType
```

网络类型。  
**注意：** 当type为蜂窝网络时，需指定simId字段。

**类型：** NetBearType

**起始版本：** 22

**系统能力：** SystemCapability.Communication.NetManager.Core
