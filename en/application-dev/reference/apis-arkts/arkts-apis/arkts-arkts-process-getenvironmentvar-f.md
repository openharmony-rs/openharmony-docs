# getEnvironmentVar

## Modules to Import

```TypeScript
import { process } from '@kit.ArkTS';
```

## getEnvironmentVar

```TypeScript
function getEnvironmentVar(name: string): string
```

Obtains the value of an environment variable.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getEnvironmentVar](arkts-arkts-process-processmanager-c.md#getenvironmentvar)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Environment variable name. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Value of the environment variable. |

**Examples**

```TypeScript
let pres = process.getEnvironmentVar("PATH");
```
