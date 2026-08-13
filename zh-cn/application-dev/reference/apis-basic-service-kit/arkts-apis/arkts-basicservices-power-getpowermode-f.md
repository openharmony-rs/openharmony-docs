# getPowerMode

## getPowerMode

```TypeScript
function getPowerMode(): DevicePowerMode
```

获取当前设备的电源模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-power-function getPowerMode(): DevicePowerMode--><!--Device-power-function getPowerMode(): DevicePowerMode-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DevicePowerMode](arkts-basicservices-power-devicepowermode-e.md) | 电源模式。 |

## 示例

```TypeScript
let mode = power.getPowerMode();
console.info('power mode: ' + mode);
```

