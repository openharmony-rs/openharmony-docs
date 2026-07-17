# getLevel

## 导入模块

```TypeScript
import { thermal } from '@kit.BasicServicesKit';
```

## getLevel

```TypeScript
function getLevel(): ThermalLevel
```

获取当前热档位信息。

**起始版本：** 9

<!--Device-thermal-function getLevel(): ThermalLevel--><!--Device-thermal-function getLevel(): ThermalLevel-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ThermalLevel](arkts-basicservices-thermal-thermallevel-e.md) | 热档位信息。 |

**示例：**

```TypeScript
let level = thermal.getLevel();
console.info('thermal level is: ' + level);

```

