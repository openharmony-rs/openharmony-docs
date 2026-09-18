# PreloadedUIExtensionAbilityLoadedFn (System API)

```TypeScript
export type PreloadedUIExtensionAbilityLoadedFn = (preloadId: number) => void
```

Defines the callback function when the preloaded [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) instance is loaded.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| preloadId | number | Yes | The preload UIExtensionAbility ID. |
