# getPowerMode

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## getPowerMode

```TypeScript
function getPowerMode(): DevicePowerMode
```

获取当前设备的电源模式。不同电源模式对应不同的设备行为策略，开发者可根据返回的模式值调整应用行为以适配当前模式。各模式定义及说明请参见DevicePowerMode。

**起始版本：** 9

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DevicePowerMode](arkts-basicservices-power-devicepowermode-e.md) | 当前设备的电源模式，取值包括标准模式、省电模式、性能模式、超级省电模式等。 |

**示例**

```TypeScript
let mode = power.getPowerMode();
console.info('power mode: ' + mode);
```
