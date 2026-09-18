# @ohos.app.ability.AbilityLifecycleCallback(UIAbility Lifecycle Callback Listener)

The lifecycle of a [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) dynamically changes from creation to
 destruction.
 The AbilityLifecycleCallback module provides the capability to listen for these lifecycle changes, which can be used
 for scenarios such as tracking the runtime duration of each UIAbility and performing data loading decoupled from the
 service logic of UIAbility.

> **NOTE**
 >
 > The APIs provided by this module can listen for lifecycle changes of the UIAbility within the same process.



## Modules to Import

```TypeScript
import { AbilityLifecycleCallback } from '@kit.AbilityKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [AbilityLifecycleCallback](arkts-ability-app-ability-abilitylifecyclecallback-abilitylifecyclecallback-c.md) | The lifecycle of a [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) dynamically changes from creation to destruction. The AbilityLifecycleCallback module provides the capability to listen for these lifecycle changes, which can be used for scenarios such as tracking the runtime duration of each UIAbility and performing data loading decoupled from the service logic of UIAbility. |
