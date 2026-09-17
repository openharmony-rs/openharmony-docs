# SceneAnimationParams (System API)

The scene animation form params.

@typedef { SceneAnimationParams }

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## abilityName

```TypeScript
abilityName: string
```

Ability name of the scene animation form.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## disabledDesktopBehaviors

```TypeScript
disabledDesktopBehaviors?: string
```

Indicates disabled desktop behaviors, only takes effect for system app.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## triggerTypes

```TypeScript
triggerTypes?: Array<SceneAnimationTriggerType>
```

The trigger types of the scene animation.

**Type:** Array&lt;[SceneAnimationTriggerType](arkts-form-forminfo-sceneanimationtriggertype-e-sys.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.
