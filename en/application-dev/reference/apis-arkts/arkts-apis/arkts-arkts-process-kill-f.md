# kill

## Modules to Import

```TypeScript
import { process } from '@kit.ArkTS';
```

## kill

```TypeScript
function kill(signal: number, pid: number): boolean
```

Sends a signal to a specified process to terminate it.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [kill](arkts-arkts-process-processmanager-c.md#kill)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| signal | number | Yes | Signal to send. |
| pid | number | Yes | PID of the process, to which the signal will be sent. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | If the signal is sent successfully, **true** is returned. Other, **false** is returned. |

**Examples**

```TypeScript
let pres = process.pid;
let result = process.kill(28, pres);
```
