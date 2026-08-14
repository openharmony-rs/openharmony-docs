# estimatedRemainingChargeTime（系统接口）

## estimatedRemainingChargeTime

```TypeScript
function estimatedRemainingChargeTime(): long
```

获取当前设备充满电的预估时间，单位毫秒。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-batteryInfo-function estimatedRemainingChargeTime(): long--><!--Device-batteryInfo-function estimatedRemainingChargeTime(): long-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 返回当前设备充满电的预估时间，单位毫秒。 |

## 示例

```TypeScript
// ArkTS-Sta示例
let result = batteryInfo.estimatedRemainingChargeTime();
console.info("The result is: " + result);
```

