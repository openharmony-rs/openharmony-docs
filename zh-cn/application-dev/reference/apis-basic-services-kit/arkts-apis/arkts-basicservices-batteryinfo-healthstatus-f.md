# healthStatus

## 导入模块

```TypeScript
import { batteryInfo } from '@kit.BasicServicesKit';
```

## healthStatus

```TypeScript
function healthStatus(): BatteryHealthState
```

表示当前设备电池的健康状态。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-batteryInfo-function healthStatus(): BatteryHealthState--><!--Device-batteryInfo-function healthStatus(): BatteryHealthState-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BatteryHealthState](arkts-basicservices-batteryinfo-batteryhealthstate-e.md) | 返回当前设备电池的健康状态。 |

**示例**

```TypeScript
// ArkTS-Sta示例
let result = batteryInfo.healthStatus();
console.info("The result is: " + result);
```

