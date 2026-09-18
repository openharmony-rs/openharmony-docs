# @ohos.app.ability.sendableContextManager

The sendableContextManager module provides APIs for converting between Context and [SendableContext](arkts-ability-sendablecontext-i.md) objects.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { sendableContextManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [convertFromContext](arkts-ability-sendablecontextmanager-convertfromcontext-f.md) | Converts a Context object to a SendableContext object. |
| [convertToAbilityStageContext](arkts-ability-sendablecontextmanager-converttoabilitystagecontext-f.md) | Converts a SendableContext object to an AbilityStageContext object. |
| [convertToApplicationContext](arkts-ability-sendablecontextmanager-converttoapplicationcontext-f.md) | Converts a SendableContext object to an ApplicationContext object. |
| [convertToContext](arkts-ability-sendablecontextmanager-converttocontext-f.md) | Converts a SendableContext object to a Context object. |
| [convertToUIAbilityContext](arkts-ability-sendablecontextmanager-converttouiabilitycontext-f.md) | Converts a SendableContext object to a UIAbilityContext object. |
| [setEventHubMultithreadingEnabled](arkts-ability-sendablecontextmanager-seteventhubmultithreadingenabled-f.md) | Enables the cross-thread data transfer feature of [EventHub](arkts-ability-eventhub-c.md) in Context. |

### Types

| Name | Description |
| --- | --- |
| [SendableContext](arkts-ability-sendablecontextmanager-sendablecontext-t.md) | Level-2 module SendableContext. |
