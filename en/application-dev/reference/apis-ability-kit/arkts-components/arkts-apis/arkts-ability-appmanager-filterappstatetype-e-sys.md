# FilterAppStateType (System API)

Enumerates the types of application states to filter. It can be used with [AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md) to filter the application state types you want to listen for.

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## CREATE

```TypeScript
CREATE = 1 << 0
```

The application is initializing. It corresponds to the state whose value is **0** in [AppStateData](../../../reference/apis-ability-kit/js-apis-inner-application-appStateData.md#properties).

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## FOREGROUND

```TypeScript
FOREGROUND = 1 << 1
```

The application is running in the foreground. It corresponds to the state whose value is **2** in [AppStateData](../../../reference/apis-ability-kit/js-apis-inner-application-appStateData.md#properties).

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## BACKGROUND

```TypeScript
BACKGROUND = 1 << 2
```

The application is running in the background. It corresponds to the state whose value is **4** in [AppStateData](../../../reference/apis-ability-kit/js-apis-inner-application-appStateData.md#properties).

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## DESTROY

```TypeScript
DESTROY = 1 << 3
```

The application has exited. It corresponds to the state whose value is **5** in [AppStateData](../../../reference/apis-ability-kit/js-apis-inner-application-appStateData.md#properties).

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
