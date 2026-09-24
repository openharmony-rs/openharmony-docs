# createAtManager

## Modules to Import

```TypeScript
import { abilityAccessCtrl, Context, PermissionRequestResult, Permissions } from '@kit.AbilityKit';
```

## createAtManager

```TypeScript
function createAtManager(): AtManager
```

Creates a program access control management instance for scenarios such as permission verification, runtime permission request, settings page authorization guidance, and permission status change monitoring. After the call is successful, an AtManager instance is returned, which can be used for subsequent permission management operations.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.AccessToken

**Return value:**

| Type | Description |
| --- | --- |
| [AtManager](arkts-ability-abilityaccessctrl-atmanager-i.md) | **AtManager** instance obtained. |

**Examples**

```TypeScript
// Create a permission management instance
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
```
