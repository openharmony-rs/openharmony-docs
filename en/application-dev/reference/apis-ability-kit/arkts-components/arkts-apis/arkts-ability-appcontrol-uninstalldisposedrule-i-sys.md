# UninstallDisposedRule (System API)

Describes an uninstallation disposed rule.

**Since:** 15

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

Priority of the disposed rule, which is used to sort the query results of the rule list. The value is an integer. A smaller value indicates a higher priority.

**Type:** number

**Since:** 15

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## uninstallComponentType

```TypeScript
uninstallComponentType: UninstallComponentType
```

Type of the ability to start during interception.

**Type:** [UninstallComponentType](arkts-ability-appcontrol-uninstallcomponenttype-e-sys.md)

**Since:** 15

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## want

```TypeScript
want: Want
```

Component displayed when the application is disposed of.

**Type:** [Want](arkts-ability-app-ability-want-want-c.md)

**Since:** 15

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.
