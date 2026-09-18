# rebootDevice

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## rebootDevice

```TypeScript
function rebootDevice(reason: string): void
```

Restarts the system.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [reboot](arkts-basicservices-power-reboot-f-sys.md)

**Required permissions:** ohos.permission.REBOOT

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reason | string | Yes | Indicates the restart reason. For example, "updater" indicates entering the updater mode after the restart. If the parameter is not specified, the system enters the normal mode after the restart. |

**Examples**

```TypeScript
power.rebootDevice('reboot_test');
```
