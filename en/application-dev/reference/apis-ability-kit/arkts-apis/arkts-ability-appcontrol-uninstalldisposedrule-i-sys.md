# UninstallDisposedRule (System API)

```TypeScript
export interface UninstallDisposedRule
```

Describes an uninstallation disposed rule.

**Since:** 15

<!--Device-appControl-export interface UninstallDisposedRule--><!--Device-appControl-export interface UninstallDisposedRule-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## priority

```TypeScript
priority: number
```

Priority of the uninstall disposition rule, used to sort the query results of the rule list. The value is an integer. A smaller value indicates a higher priority and an earlier position in the sorting.

**Type:** number

**Since:** 15

<!--Device-UninstallDisposedRule-priority: int--><!--Device-UninstallDisposedRule-priority: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## uninstallComponentType

```TypeScript
uninstallComponentType: UninstallComponentType
```

Type of the ability to be started upon interception.

**Type:** [UninstallComponentType](arkts-ability-appcontrol-uninstallcomponenttype-e-sys.md)

**Since:** 15

<!--Device-UninstallDisposedRule-uninstallComponentType: UninstallComponentType--><!--Device-UninstallDisposedRule-uninstallComponentType: UninstallComponentType-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## want

```TypeScript
want: Want
```

Component displayed when the application is disposed of.

**Type:** [Want](arkts-ability-app-ability-want-want-c.md)

**Since:** 15

<!--Device-UninstallDisposedRule-want: Want--><!--Device-UninstallDisposedRule-want: Want-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.
