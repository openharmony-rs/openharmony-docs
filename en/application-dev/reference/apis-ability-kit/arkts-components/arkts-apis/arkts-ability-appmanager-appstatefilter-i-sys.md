# AppStateFilter (System API)

Describes the filter for application lifecycle change events. It can be used as a parameter of [on](arkts-ability-appmanager-on-f-sys.md#onapplicationstate) to filter application lifecycle change events you want to listen for.

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## abilityStateTypes

```TypeScript
abilityStateTypes?: number
```

Type of ability state to filter. The options are as follows:

- **0**: Do not listen for any ability state.  
- A bitwise OR combination of the enumerated values of [FilterAbilityStateType](arkts-ability-appmanager-filterabilitystatetype-e-sys.md), for  
example, "appManager.FilterAbilityStateType.CREATE | appManager.FilterAbilityStateType.FOREGROUND" listens for both the creating and foreground states of ability components.  
- If this parameter is not set, all ability state types are listened for by default.

**Type:** number

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## appStateTypes

```TypeScript
appStateTypes?: number
```

Type of application state to filter. The options are as follows:

- **0**: Do not listen for any application state.  
- A bitwise OR combination of the enumerated values of [FilterAppStateType](arkts-ability-appmanager-filterappstatetype-e-sys.md), for example,  
"appManager.FilterAppStateType.CREATE | appManager.FilterAppStateType.FOREGROUND" listens for both the creating and foreground states of applications.  
- If this parameter is not set, all application state types are listened for by default.

**Type:** number

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## bundleTypes

```TypeScript
bundleTypes?: number
```

Type of application to filter. The options are as follows:

- **0**: Do not listen for any application type.  
- A bitwise OR combination of the enumerated values of [FilterBundleType](arkts-ability-appmanager-filterbundletype-e-sys.md), for example, "  
appManager.FilterBundleType.APP | appManager.FilterBundleType.ATOMIC_SERVICE" listens for lifecycle change events for both applications and atomic services.  
- If this parameter is not set, all application types are listened for by default.

**Type:** number

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## callbacks

```TypeScript
callbacks?: number
```

Callback to filter. The options are as follows:

- **0**: Do not listen for any callback.  
- A bitwise OR combination of the enumerated values of [FilterCallback](arkts-ability-appmanager-filtercallback-e-sys.md), for example, "  
appManager.FilterCallback.ON_ABILITY_STATE_CHANGED | appManager.FilterCallback.ON_PROCESS_STATE_CHANGED" listens for both [ApplicationStateObserver.onAbilityStateChanged](arkts-ability-applicationstateobserver-c.md#onabilitystatechanged) and [ApplicationStateObserver.onProcessStateChanged](arkts-ability-applicationstateobserver-c.md#onprocessstatechanged).  
- If this parameter is not set, all callbacks enumerated in [FilterCallback](arkts-ability-appmanager-filtercallback-e-sys.md) are listened for  
by default.

**Type:** number

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## processStateTypes

```TypeScript
processStateTypes?: number
```

Type of process state to filter. The options are as follows:

- **0**: Do not listen for any process state.  
- A bitwise OR combination of the enumerated values of [FilterProcessStateType](arkts-ability-appmanager-filterprocessstatetype-e-sys.md), for  
example, "appManager.FilterProcessStateType.CREATE | appManager.FilterProcessStateType.FOREGROUND" listens for both the creating and foreground states of processes.  
- If this parameter is not set, all process state types are listened for by default.

**Type:** number

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
