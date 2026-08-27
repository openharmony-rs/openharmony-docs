# getLevel

## 导入模块

```TypeScript
import { thermal } from '@kit.BasicServicesKit';
```

## getLevel

```TypeScript
function getLevel(): ThermalLevel
```

获取当前热档位信息。系统根据设备温度实时判定当前所处的热档位层级并返回对应等级，开发者可据此执行相应的业务降级策略。

**起始版本：** 9

**系统能力：** SystemCapability.PowerManager.ThermalManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ThermalLevel](arkts-basicservices-thermal-thermallevel-e.md) | 当前设备的热档位等级，反映设备的温度状态，可用于指导业务的热控策略调整。 |

**示例**

```TypeScript
let level = thermal.getLevel();
console.info('thermal level is: ' + level);
```
