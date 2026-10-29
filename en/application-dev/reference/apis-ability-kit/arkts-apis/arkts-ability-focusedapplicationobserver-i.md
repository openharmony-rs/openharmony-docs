# FocusedApplicationObserver

```TypeScript
declare interface FocusedApplicationObserver
```

Defines the observer used to listen for focused application changes. It is used as an input parameter of [appManager.onFocusedApplicationChanged](arkts-ability-appmanager-onfocusedapplicationchanged-f.md) to listen for focused application changes.

**Since:** 26.1.0

<!--Device-unnamed-declare interface FocusedApplicationObserver--><!--Device-unnamed-declare interface FocusedApplicationObserver-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## onFocusedApplicationChanged

```TypeScript
onFocusedApplicationChanged(info: FocusedApplicationInfo): void
```

Called when the focused application changes.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FocusedApplicationObserver-onFocusedApplicationChanged(info: FocusedApplicationInfo): void--><!--Device-FocusedApplicationObserver-onFocusedApplicationChanged(info: FocusedApplicationInfo): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [FocusedApplicationInfo](arkts-ability-focusedapplicationinfo-i.md) | Yes | Focused application information. |
