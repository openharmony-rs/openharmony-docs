# ExecuteModeForConfiguration (System API)

Enumerates the execution modes supported by an [intent developed using a configuration file](../../../application-models/insight-intent-config-development.md). For example, if **executeMode** in the [insight_intent.json configuration file] (../../../application-models/insight-intent-config-development.md#description-of-the-insight_intentjson-file) is set to **foreground**, the intent bound to the UIAbility can run in the foreground.

**Since:** 23

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## FOREGROUND

```TypeScript
FOREGROUND = 0
```

The intent bound to the UIAbility can run in the foreground.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## BACKGROUND

```TypeScript
BACKGROUND = 1
```

The intent bound to the UIAbility can run in the background.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
