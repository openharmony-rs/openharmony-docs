# LifecycleApp

interface of app lifecycle.

@interface LifecycleApp

**Since:** 7

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## Modules to Import

```TypeScript
```

## onWindowDisplayModeChanged

```TypeScript
onWindowDisplayModeChanged?(isShownInMultiWindow: boolean, newConfig: resourceManager.Configuration): void
```

Called when the window display mode of this ability changes, for example, from fullscreen mode to multi-window mode or from multi-window mode to fullscreen mode.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isShownInMultiWindow | boolean | Yes | Specifies whether this ability is currently in multi-window mode.The value `true` indicates the multi-window mode, and `false` indicates another mode. |
| newConfig | [resourceManager.Configuration](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-configuration-c.md) | Yes | Indicates the new configuration information about Page ability. |
