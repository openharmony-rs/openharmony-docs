# BatteryResponse

包含充电状态及剩余电量的对象。

**起始版本：** 3

**废弃版本：** 6

**系统能力：** SystemCapability.PowerManager.BatteryManager.Lite

## charging

```TypeScript
charging: boolean
```

当前电池是否在充电中。true表示在充电，false表示没有充电，默认为false。

**说明：** 除Lite Wearable外，从API Version 6开始不再维护，建议使用
[`batteryInfo.chargingStatus`](../../../../reference/apis-basic-services-kit/js-apis-battery-info.md#常量)替代。

**类型：** boolean

**起始版本：** 3

**废弃版本：** 6

**替代接口：** [chargingStatus](arkts-basicservices-batteryinfo-con.md#chargingstatus)

**系统能力：** SystemCapability.PowerManager.BatteryManager.Lite

## level

```TypeScript
level: number
```

当前电池的电量百分比，取值范围：0.00~1.00。

**说明：** 除Lite Wearable外，从API Version 6开始不再维护，建议使用
[`batteryInfo.batterySOC`](../../../../reference/apis-basic-services-kit/js-apis-battery-info.md#常量)替代。

**类型：** number

**起始版本：** 3

**废弃版本：** 6

**替代接口：** [batterySOC](arkts-basicservices-batteryinfo-con.md#batterysoc)

**系统能力：** SystemCapability.PowerManager.BatteryManager.Lite

