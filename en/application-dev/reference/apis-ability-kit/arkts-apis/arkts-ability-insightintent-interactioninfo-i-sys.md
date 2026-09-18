# InteractionInfo (System API)

Defines the interaction information returned after the current intent execution completes, including the next intent to be triggered and the interaction UI to be displayed.

**Since:** 26.1.0

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## interactionUI

```TypeScript
interactionUI?: InteractionUI
```

Information of the interaction UI to be displayed after the current intent execution completes.

**Type:** [InteractionUI](arkts-ability-insightintent-interactionui-i-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
