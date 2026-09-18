# 常量

## batteryCapacityLevel

```TypeScript
const batteryCapacityLevel: BatteryCapacityLevel
```

表示当前设备电池电量的等级。

**类型：** [BatteryCapacityLevel](arkts-basicservices-batteryinfo-batterycapacitylevel-e.md)

**起始版本：** 9

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## batterySOC

```TypeScript
const batterySOC: number
```

表示当前设备剩余电池电量百分比，取值范围是[0，100]。

**类型：** number

**起始版本：** 6

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## batteryTemperature

```TypeScript
const batteryTemperature: number
```

表示当前设备电池的温度，单位0.1摄氏度。

**类型：** number

**起始版本：** 6

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## chargingStatus

```TypeScript
const chargingStatus: BatteryChargeState
```

表示当前设备电池的充电状态。

**类型：** [BatteryChargeState](arkts-basicservices-batteryinfo-batterychargestate-e.md)

**起始版本：** 6

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## healthStatus

```TypeScript
const healthStatus: BatteryHealthState
```

表示当前设备电池的健康状态。

**类型：** [BatteryHealthState](arkts-basicservices-batteryinfo-batteryhealthstate-e.md)

**起始版本：** 6

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## isBatteryPresent

```TypeScript
const isBatteryPresent: boolean
```

表示当前设备是否支持电池以及电池是否在位。true表示设备支持电池且电池在位，false表示设备不支持电池或电池不在位，默认为false。

**类型：** boolean

**起始版本：** 7

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## nowCurrent

```TypeScript
const nowCurrent: number
```

表示当前设备电池的电流，单位毫安。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## pluggedType

```TypeScript
const pluggedType: BatteryPluggedType
```

表示当前设备连接的充电器类型。

**类型：** [BatteryPluggedType](arkts-basicservices-batteryinfo-batterypluggedtype-e.md)

**起始版本：** 6

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## technology

```TypeScript
const technology: string
```

表示当前设备电池的技术型号。

**类型：** string

**起始版本：** 6

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## voltage

```TypeScript
const voltage: number
```

表示当前设备电池的电压，单位微伏。

**类型：** number

**起始版本：** 6

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core
