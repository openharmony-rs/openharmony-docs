# batterySOC

## 导入模块

```TypeScript
import { batteryInfo } from '@kit.BasicServicesKit';
```

## batterySOC

```TypeScript
function batterySOC(): int
```

表示当前设备剩余电池电量百分比，取值范围是[0，100]。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-batteryInfo-function batterySOC(): int--><!--Device-batteryInfo-function batterySOC(): int-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回当前设备剩余电池电量百分比，取值范围是[0，100]。 |

**示例**

```TypeScript
// ArkTS-Sta示例
let result = batteryInfo.batterySOC();
console.info("The result is: " + result);
```

