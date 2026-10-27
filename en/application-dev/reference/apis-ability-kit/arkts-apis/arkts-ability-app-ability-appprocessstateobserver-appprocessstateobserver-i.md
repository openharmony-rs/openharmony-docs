# AppProcessStateObserver

```TypeScript
declare interface AppProcessStateObserver
```

Defines an observer to listen for process state changes within the application. It can be used as an input parameter in [ApplicationContext.onAppProcessStateChange](arkts-ability-applicationcontext-c.md#onappprocessstatechange) to listen for process creation and termination within the application.

**Since:** 26.1.0

<!--Device-unnamed-declare interface AppProcessStateObserver--><!--Device-unnamed-declare interface AppProcessStateObserver-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { AppProcessStateObserver } from '@kit.AbilityKit';
```

## onProcessCreated

```TypeScript
onProcessCreated(processData: ProcessData): void
```

Called when a process is created within the application.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AppProcessStateObserver-onProcessCreated(processData: ProcessData): void--><!--Device-AppProcessStateObserver-onProcessCreated(processData: ProcessData): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| processData | [ProcessData](arkts-ability-processdata-c.md) | Yes | Process data. |

## onProcessDied

```TypeScript
onProcessDied(processData: ProcessData): void
```

Called when a process is destroyed within the application.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AppProcessStateObserver-onProcessDied(processData: ProcessData): void--><!--Device-AppProcessStateObserver-onProcessDied(processData: ProcessData): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| processData | [ProcessData](arkts-ability-processdata-c.md) | Yes | Process data. |
