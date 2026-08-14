# batteryTemperature

## batteryTemperature

```TypeScript
function batteryTemperature(): int
```

表示当前设备电池的温度，单位0.1摄氏度。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-batteryInfo-function batteryTemperature(): int--><!--Device-batteryInfo-function batteryTemperature(): int-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回当前设备电池的温度，单位0.1摄氏度。 |

## 示例

```TypeScript
// ArkTS-Sta示例
let result = batteryInfo.batteryTemperature();
console.info("The result is: " + result);
```

