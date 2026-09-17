# AbilityStageMonitor

The module provides the capability to listen for a specified [AbilityStage](arkts-ability-app-ability-abilitystage-abilitystage-c.md) object. You can use AbilityStageMonitor as an input parameter of [abilityDelegator.waitAbilityStageMonitor](arkts-ability-abilitydelegator-i.md#waitabilitystagemonitor) to register a listener.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## moduleName

```TypeScript
moduleName: string
```

Module name of the AbilityStage object.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## srcEntrance

```TypeScript
srcEntrance: string
```

Source path of the AbilityStage object.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

```TypeScript
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
