# AtomicServiceStartupRule (System API)

```TypeScript
export interface AtomicServiceStartupRule
```

Describes the rule for launching an embedded atomic service.

**Since:** 18

<!--Device-abilityManager-export interface AtomicServiceStartupRule--><!--Device-abilityManager-export interface AtomicServiceStartupRule-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## isEmbeddedAllowed

```TypeScript
isEmbeddedAllowed: boolean
```

Whether launching the embedded atomic service is allowed. **true** if allowed, **false** otherwise.

**Type:** boolean

**Since:** 18

<!--Device-AtomicServiceStartupRule-isEmbeddedAllowed: boolean--><!--Device-AtomicServiceStartupRule-isEmbeddedAllowed: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## isOpenAllowed

```TypeScript
isOpenAllowed: boolean
```

Whether launching the atomic service is allowed. **true** if allowed, **false** otherwise.

**Type:** boolean

**Since:** 18

<!--Device-AtomicServiceStartupRule-isOpenAllowed: boolean--><!--Device-AtomicServiceStartupRule-isOpenAllowed: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
