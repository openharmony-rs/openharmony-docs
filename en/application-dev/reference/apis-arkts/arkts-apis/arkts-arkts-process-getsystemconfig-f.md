# getSystemConfig

## Modules to Import

```TypeScript
import { process } from '@kit.ArkTS';
```

## getSystemConfig

```TypeScript
function getSystemConfig(name: number): number
```

Obtains the system configuration.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getSystemConfig](arkts-arkts-process-processmanager-c.md#getsystemconfig)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | number | Yes | System configuration parameter name. |

**Return value:**

| Type | Description |
| --- | --- |
| number | System configuration obtained. |

**Examples**

```TypeScript
let _SC_ARG_MAX = 0;
let pres = process.getSystemConfig(_SC_ARG_MAX);
```
