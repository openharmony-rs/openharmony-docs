# batteryCapacityLevel

## 导入模块

```TypeScript
import { batteryInfo } from '@kit.BasicServicesKit';
```

## batteryCapacityLevel

```TypeScript
function batteryCapacityLevel(): BatteryCapacityLevel
```

表示当前设备电池电量的等级。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-batteryInfo-function batteryCapacityLevel(): BatteryCapacityLevel--><!--Device-batteryInfo-function batteryCapacityLevel(): BatteryCapacityLevel-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BatteryCapacityLevel](arkts-basicservices-batteryinfo-batterycapacitylevel-e.md) | 返回当前设备电池电量的等级。 |

**示例**

```TypeScript
// ArkTS-Sta示例
let result = batteryInfo.batteryCapacityLevel();
console.info("The result is: " + result);
```

