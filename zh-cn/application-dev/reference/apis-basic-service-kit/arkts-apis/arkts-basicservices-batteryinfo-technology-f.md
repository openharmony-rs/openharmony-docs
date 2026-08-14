# technology

## technology

```TypeScript
function technology(): string
```

表示当前设备电池的技术型号。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-batteryInfo-function technology(): string--><!--Device-batteryInfo-function technology(): string-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回当前设备电池的技术型号。 |

## 示例

```TypeScript
// ArkTS-Sta示例
let result = batteryInfo.technology();
console.info("The result is: " + result);
```

