# getPowerMode

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

<a id="getpowermode"></a>
## getPowerMode

```TypeScript
function getPowerMode(): DevicePowerMode
```

获取当前设备的电源模式。

**起始版本：** 9

<!--Device-power-function getPowerMode(): DevicePowerMode--><!--Device-power-function getPowerMode(): DevicePowerMode-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DevicePowerMode](arkts-basicservices-power-devicepowermode-e.md) | 电源模式。 |

**示例：**

```TypeScript
let mode = power.getPowerMode();
console.info('power mode: ' + mode);

```

