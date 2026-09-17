# ChangeSceneAnimationStateRequest (System API)

ChangeSceneAnimationStateRequest

@typedef { ChangeSceneAnimationStateRequest }

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## formId

```TypeScript
formId: string
```

The form id about request change scene animation state

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## state

```TypeScript
state: number
```

The state of scene animation. 0 means deactivate, 1 means activate The value must be an integer within [0,1].

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.
