# pluggedType

## 导入模块

```TypeScript
import { batteryInfo } from '@kit.BasicServicesKit';
```

## pluggedType

```TypeScript
function pluggedType(): BatteryPluggedType
```

表示当前设备连接的充电器类型。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-batteryInfo-function pluggedType(): BatteryPluggedType--><!--Device-batteryInfo-function pluggedType(): BatteryPluggedType-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BatteryPluggedType](arkts-basicservices-batteryinfo-batterypluggedtype-e.md) | 返回当前设备连接的充电器类型。 |

**示例**

```TypeScript
// ArkTS-Sta示例
let result = batteryInfo.pluggedType();
console.info("The result is: " + result);
```

