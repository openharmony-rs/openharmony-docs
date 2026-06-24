# getPowerMode

## getPowerMode

```TypeScript
function getPowerMode(): DevicePowerMode
```

获取当前设备的电源模式。

**起始版本：** 9

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DevicePowerMode | 电源模式。 |

**示例：**

```TypeScript
let mode = power.getPowerMode();
console.info('power mode: ' + mode);

```

