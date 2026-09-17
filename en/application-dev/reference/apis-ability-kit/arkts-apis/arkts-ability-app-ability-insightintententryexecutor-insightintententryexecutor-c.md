# InsightIntentEntryExecutor

The class of insight intent entry executor.

@class InsightIntentEntryExecutor&lt;T&gt;

**Since:** 20

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { InsightIntentEntryExecutor } from '@kit.AbilityKit';
```

## onExecute

```TypeScript
onExecute(): Promise<insightIntent.IntentResult<T>>
```

Called when insight intent execute.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[insightIntent.IntentResult](arkts-ability-insightintent-intentresult-i.md)&lt;T&gt;&gt; | The result of insight intent execution, support promise. |

## context

```TypeScript
context: InsightIntentContext
```

The insight intent context.

**Type:** [InsightIntentContext](arkts-ability-app-ability-insightintentcontext-insightintentcontext-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## executeMode

```TypeScript
executeMode: insightIntent.ExecuteMode
```

The insight intent execute mode.

**Type:** [insightIntent.ExecuteMode](arkts-ability-insightintent-executemode-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## uiExtensionSession

```TypeScript
uiExtensionSession?: UIExtensionContentSession
```

The UIExtension content session.

**Type:** [UIExtensionContentSession](arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## windowStage

```TypeScript
windowStage?: window.WindowStage
```

The window stage.

**Type:** [window.WindowStage](../../apis-arkui/arkts-apis/arkts-arkui-window-windowstage-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
