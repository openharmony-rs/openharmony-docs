# chargingStatus

## chargingStatus

```TypeScript
function chargingStatus(): BatteryChargeState
```

表示当前设备电池的充电状态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-batteryInfo-function chargingStatus(): BatteryChargeState--><!--Device-batteryInfo-function chargingStatus(): BatteryChargeState-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BatteryChargeState](arkts-basicservices-batteryinfo-batterychargestate-e.md) | 返回当前设备电池的充电状态。 |

## 示例

```TypeScript
// ArkTS-Sta示例
let result = batteryInfo.chargingStatus();
console.info("The result is: " + result);
```

