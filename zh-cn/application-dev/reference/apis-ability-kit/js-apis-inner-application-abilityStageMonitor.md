# AbilityStageMonitor

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

本模块提供监听指定[AbilityStage](js-apis-app-ability-abilityStage.md)对象的能力。开发者可以将AbilityStageMonitor作为[abilityDelegator.waitAbilityStageMonitor](../apis-test-kit/js-apis-inner-application-abilityDelegator.md#waitabilitystagemonitor9)的入参来注册监听。

> **说明：**
> 
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。  

## AbilityStageMonitor

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 类型 | 只读 | 可选 | 说明  |
| ---- | ---- | ---- | ---- | ---- |
| moduleName | string | 否   | 否   | 被监听的AbilityStage的模块名。 |
| srcEntrance | string | 否   | 否   | 被监听的AbilityStage的源路径。 |

**示例：**
```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';

let monitor: abilityDelegatorRegistry.AbilityStageMonitor = {
  moduleName: 'feature_as1',
  srcEntrance: './ets/Application/MyAbilityStage.ts',
}

let abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.waitAbilityStageMonitor(monitor, (error, data) => {
  if (error) {
    console.error(`waitAbilityStageMonitor fail, error: ${JSON.stringify(error)}`);
  } else {
    console.log(`waitAbilityStageMonitor success, data: ${JSON.stringify(data)}`);
  }
});
```