# remainingEnergy（系统接口）

## 导入模块

```TypeScript
import { batteryInfo } from '@kit.BasicServicesKit';
```

## remainingEnergy

```TypeScript
function remainingEnergy(): int
```

获取当前设备电池的剩余容量，单位毫安时。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-batteryInfo-function remainingEnergy(): int--><!--Device-batteryInfo-function remainingEnergy(): int-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回当前设备电池的剩余容量，单位毫安时。 |

**示例**

```TypeScript
// ArkTS-Sta示例
let result = batteryInfo.remainingEnergy();
console.info("The result is: " + result);
```

