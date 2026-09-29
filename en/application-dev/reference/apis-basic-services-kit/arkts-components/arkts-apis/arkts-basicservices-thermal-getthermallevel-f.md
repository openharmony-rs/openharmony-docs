# getThermalLevel

## Modules to Import

```TypeScript
import { thermal } from '@kit.BasicServicesKit';
```

## getThermalLevel

```TypeScript
function getThermalLevel(): ThermalLevel
```

Obtains the current thermal level.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getLevel](arkts-basicservices-thermal-getlevel-f.md)

<!--Device-thermal-function getThermalLevel(): ThermalLevel--><!--Device-thermal-function getThermalLevel(): ThermalLevel-End-->

**System capability:** SystemCapability.PowerManager.ThermalManager

**Return value:**

| Type | Description |
| --- | --- |
| [ThermalLevel](arkts-basicservices-thermal-thermallevel-e.md) | Thermal level. |

**Examples**

```TypeScript
let level = thermal.getThermalLevel();
console.info('thermal level is: ' + level);
```
