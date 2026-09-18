# getLevel

## Modules to Import

```TypeScript
import { thermal } from '@kit.BasicServicesKit';
```

## getLevel

```TypeScript
function getLevel(): ThermalLevel
```

Obtains the current thermal level.

**Since:** 9

**System capability:** SystemCapability.PowerManager.ThermalManager

**Return value:**

| Type | Description |
| --- | --- |
| [ThermalLevel](arkts-basicservices-thermal-thermallevel-e.md) | Thermal level. |

**Examples**

```TypeScript
let level = thermal.getLevel();
console.info('thermal level is: ' + level);
```
