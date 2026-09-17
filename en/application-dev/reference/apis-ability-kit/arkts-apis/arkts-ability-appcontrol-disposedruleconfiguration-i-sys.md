# DisposedRuleConfiguration (System API)

Describes the configurations for setting disposed rules in batches.

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## appId

```TypeScript
appId: string
```

appId or appIdentifier of the target application. Identical appId and appIdentifier values indicate the same application instance. If a rule is set using appId, it overwrites the one set with appIdentifier, and the reverse is also true.

**NOTE:** 

**appId** is also the unique identifier of an app. For details, see [What is appIdentifier](../../../quick-start/common_problem_of_application.md#what-is-appidentifier). For details about how to obtain **appIdentifier**, see [How do I obtain appIdentifier from application information](../../../quick-start/common_problem_of_application.md#how-do-i-obtain-appidentifier-from-application-information).

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## appIndex

```TypeScript
appIndex: number
```

Index of the application clone. The default value is **0**.

The value **0** means to set the disposed rule for the main application. A value greater than 0 means to set the disposed rule for the application clone with the specified index.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## disposedRule

```TypeScript
disposedRule: DisposedRule
```

Disposal rule of the application, including the type of the ability to be started during disposal.

**Type:** [DisposedRule](arkts-ability-appcontrol-disposedrule-i-sys.md)

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.
