# AbilityStageMonitor

本模块提供监听指定[AbilityStage](arkts-ability-app-ability-abilitystage-abilitystage-c.md)对象的能力。开发者可以将AbilityStageMonitor作为 [abilityDelegator.waitAbilityStageMonitor](arkts-ability-abilitydelegator-i.md#waitabilitystagemonitor) 的入参来注册监听。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## moduleName

```TypeScript
moduleName: string
```

被监听的AbilityStage的模块名。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## srcEntrance

```TypeScript
srcEntrance: string
```

被监听的AbilityStage的源路径。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例**

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
