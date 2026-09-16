# AbilityStageMonitor

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=7e647be53cee0e352795102117faaeb99055eefa translatedAt=2026-09-03T11:37:40.597Z pushedAt=2026-09-05T10:47:30.658Z -->

This module provides the capability to listen for a specified [AbilityStage](js-apis-app-ability-abilityStage.md) object. You can use AbilityStageMonitor as an input parameter of [abilityDelegator.waitAbilityStageMonitor](../apis-test-kit/js-apis-inner-application-abilityDelegator.md#waitabilitystagemonitor) to register the listener.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
```

## AbilityStageMonitor

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description |
| ---- | ---- | ---- | ---- | ---- |
| moduleName | string | No  | No  | Module name of the AbilityStage object.|
| srcEntrance | string | No  | No  | Source path of the AbilityStage object.|

**Example**
```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';

let monitor: abilityDelegatorRegistry.AbilityStageMonitor = {
  moduleName: 'feature_as1',
  srcEntrance: './ets/Application/MyAbilityStage.ts',
};

let abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.waitAbilityStageMonitor(monitor, (error, data) => {
  if (error) {
    console.error(`waitAbilityStageMonitor fail. Code: ${error.code}, message: ${error.message}`);
  } else {
    console.info(`waitAbilityStageMonitor success, data: ${JSON.stringify(data)}`);
  }
});
```
<!--no_check-->