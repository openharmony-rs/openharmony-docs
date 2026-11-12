# RecoverDisposedRule (System API)

```TypeScript
export interface RecoverDisposedRule
```

Describes an application recovery disposed rule.

**Since:** 26.1.0

<!--Device-appControl-export interface RecoverDisposedRule--><!--Device-appControl-export interface RecoverDisposedRule-End-->

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

Priority of the disposed rule, which is used to sort the query results of the rule list. The value is an integer. A smaller value indicates a higher priority. The value should be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RecoverDisposedRule-priority: int--><!--Device-RecoverDisposedRule-priority: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## recoverComponentType

```TypeScript
recoverComponentType: RecoverComponentType
```

Type of the ability to start during interception.

**Type:** [RecoverComponentType](arkts-ability-appcontrol-recovercomponenttype-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RecoverDisposedRule-recoverComponentType: RecoverComponentType--><!--Device-RecoverDisposedRule-recoverComponentType: RecoverComponentType-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## want

```TypeScript
want: Want
```

Component displayed when the application is disposed of.

**Type:** [Want](arkts-ability-app-ability-want-want-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RecoverDisposedRule-want: Want--><!--Device-RecoverDisposedRule-want: Want-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.
