# voltage

## voltage

```TypeScript
function voltage(): int
```

表示当前设备电池的电压，单位微伏。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-batteryInfo-function voltage(): int--><!--Device-batteryInfo-function voltage(): int-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回当前设备电池的电压，单位微伏。 |

## 示例

```TypeScript
// ArkTS-Sta示例
let result = batteryInfo.voltage();
console.info("The result is: " + result);
```

