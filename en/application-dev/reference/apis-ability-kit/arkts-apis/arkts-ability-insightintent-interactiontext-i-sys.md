# InteractionText (System API)

```TypeScript
interface InteractionText extends InteractionUI
```

Defines the information of the Text to be displayed as the interaction UI after the current intent execution completes. Does not support distributed scenarios.

**Inheritance/Implementation:** InteractionText extends [InteractionUI](arkts-ability-insightintent-interactionui-i-sys.md)

**Since:** 26.0.1

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## buttons

```TypeScript
buttons?: Array<string>
```

Buttons passed to the target TEXT.

**Type:** Array&lt;string&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## interactionUIType

```TypeScript
interactionUIType: 'TEXT'
```

Type of the interaction UI. The value is fixed to 'TEXT'.

**Type:** 'TEXT'

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## parameters

```TypeScript
parameters: Record<string, Object>
```

Parameters passed to the target TEXT.

**Type:** Record&lt;string, Object&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
