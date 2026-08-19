# nowCurrent

## 导入模块

```TypeScript
import { batteryInfo } from '@kit.BasicServicesKit';
```

## nowCurrent

```TypeScript
function nowCurrent(): int
```

表示当前设备电池的电流，单位毫安。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-batteryInfo-function nowCurrent(): int--><!--Device-batteryInfo-function nowCurrent(): int-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回当前设备电池的电流，单位毫安。 |

**示例**

```TypeScript
// ArkTS-Sta示例
let result = batteryInfo.nowCurrent();
console.info("The result is: " + result);
```

