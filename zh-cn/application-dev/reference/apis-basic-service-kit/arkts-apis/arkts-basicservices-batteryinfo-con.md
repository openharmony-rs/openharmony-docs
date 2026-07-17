# 常量

## batteryCapacityLevel

```TypeScript
const batteryCapacityLevel: BatteryCapacityLevel
```

表示当前设备电池电量的等级。

**起始版本：** 9

<!--Device-batteryInfo-const batteryCapacityLevel: BatteryCapacityLevel--><!--Device-batteryInfo-const batteryCapacityLevel: BatteryCapacityLevel-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## batterySOC

```TypeScript
const batterySOC: number
```

表示当前设备剩余电池电量百分比，取值范围是[0，100]。

**起始版本：** 6

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-batteryInfo-const batterySOC: number--><!--Device-batteryInfo-const batterySOC: number-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## batteryTemperature

```TypeScript
const batteryTemperature: number
```

表示当前设备电池的温度，单位0.1摄氏度。

**起始版本：** 6

<!--Device-batteryInfo-const batteryTemperature: number--><!--Device-batteryInfo-const batteryTemperature: number-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## chargingStatus

```TypeScript
const chargingStatus: BatteryChargeState
```

表示当前设备电池的充电状态。

**起始版本：** 6

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-batteryInfo-const chargingStatus: BatteryChargeState--><!--Device-batteryInfo-const chargingStatus: BatteryChargeState-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## healthStatus

```TypeScript
const healthStatus: BatteryHealthState
```

表示当前设备电池的健康状态。

**起始版本：** 6

<!--Device-batteryInfo-const healthStatus: BatteryHealthState--><!--Device-batteryInfo-const healthStatus: BatteryHealthState-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## isBatteryPresent

```TypeScript
const isBatteryPresent: boolean
```

表示当前设备是否支持电池或者电池是否在位。true表示支持电池或电池在位，false表示不支持电池或电池不在位，默认为false。

**起始版本：** 7

<!--Device-batteryInfo-const isBatteryPresent: boolean--><!--Device-batteryInfo-const isBatteryPresent: boolean-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## nowCurrent

```TypeScript
const nowCurrent: number
```

表示当前设备电池的电流，单位毫安。

**起始版本：** 12

<!--Device-batteryInfo-const nowCurrent: number--><!--Device-batteryInfo-const nowCurrent: number-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## pluggedType

```TypeScript
const pluggedType: BatteryPluggedType
```

表示当前设备连接的充电器类型。

**起始版本：** 6

<!--Device-batteryInfo-const pluggedType: BatteryPluggedType--><!--Device-batteryInfo-const pluggedType: BatteryPluggedType-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## technology

```TypeScript
const technology: string
```

表示当前设备电池的技术型号。

**起始版本：** 6

<!--Device-batteryInfo-const technology: string--><!--Device-batteryInfo-const technology: string-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## voltage

```TypeScript
const voltage: number
```

表示当前设备电池的电压，单位微伏。

**起始版本：** 6

<!--Device-batteryInfo-const voltage: number--><!--Device-batteryInfo-const voltage: number-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

