# totalEnergy（系统接口）

## totalEnergy

```TypeScript
function totalEnergy(): int
```

获取当前设备电池的总容量，单位毫安时。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-batteryInfo-function totalEnergy(): int--><!--Device-batteryInfo-function totalEnergy(): int-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回当前设备电池的总容量，单位毫安时。 |

## 示例

```TypeScript
// ArkTS-Sta示例
let result = batteryInfo.totalEnergy();
console.info("The result is: " + result);
```

