# InsightIntentContext

```TypeScript
declare class InsightIntentContext
```

The module provides the context for intent execution. It is used as a property in both the [intent execution base class](arkts-ability-app-ability-insightintentexecutor-insightintentexecutor-c.md) and [base class decorated with @InsightIntentEntry](arkts-ability-app-ability-insightintententryexecutor-insightintententryexecutor-c.md), offering essential capabilities for intent implementation, for example, starting [UIAbility components](arkts-ability-app-ability-uiability-uiability-c.md) within the same application.

**Since:** 11

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { InsightIntentContext } from '@kit.AbilityKit';
```

## toolCallId

```TypeScript
readonly toolCallId?: string
```

Tool call ID passed by the caller, used to associate this intent execute with a test step. It is undefined when the caller does not pass a tool call ID or passes an empty string.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.
