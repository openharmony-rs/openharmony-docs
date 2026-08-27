# LocatingRequiredDataConfig（系统接口）

订阅定位业务所需数据的变化，主要包含WiFi和蓝牙扫描信息；根据入参决定是否启动WiFi和蓝牙扫描。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## arfcn

```TypeScript
arfcn?: number[]
```

表示绝对无线载频信道号（Absolute Radio Frequency Channel Number，ARFCN）

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

## needStartScan

```TypeScript
needStartScan: boolean
```

是否需要发起扫描。 true：需要发起扫描。 false：不需要发起扫描。

**类型：** boolean

**起始版本：** 10

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

## plmnId

```TypeScript
plmnId?: number[]
```

表示SIM卡的PLMN号码（Public Land Mobile Network Identifier，PLMN ID）

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

## scanInterval

```TypeScript
scanInterval?: number
```

表示扫描的时间间隔。单位是毫秒，默认值是10000毫秒，取值范围为大于0。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

## scanTimeout

```TypeScript
scanTimeout?: number
```

表示单次扫描的超时时间。单位是毫秒，默认值是10000毫秒，取值范围为大于0小于600000。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

## slotId

```TypeScript
slotId?: number
```

表示SIM卡的卡槽号。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type: LocatingRequiredDataType
```

表示请求获取数据的类型。

**类型：** [LocatingRequiredDataType](arkts-location-geolocationmanager-locatingrequireddatatype-e-sys.md)

**起始版本：** 10

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。
