# convertToUIAbilityContext

## Modules to Import

```TypeScript
import { sendableContextManager } from '@kit.AbilityKit';
```

## convertToUIAbilityContext

```TypeScript
function convertToUIAbilityContext(sendableContext: SendableContext): common.UIAbilityContext
```

Converts a SendableContext object to a UIAbilityContext object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sendableContext | [SendableContext](arkts-ability-sendablecontextmanager-sendablecontext-t.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [common.UIAbilityContext](arkts-ability-common-uiabilitycontext-t.md) | [UIAbilityContext](arkts-ability-uiabilitycontext-c.md) object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | If the input parameter invalid. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |

**Examples**

```TypeScript
Context passed by the main thread:
```

```TypeScript
Context received by the Worker thread:
```
