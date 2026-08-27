# Scenarios

表示不触发[onNewWant](arkts-ability-app-ability-uiability-uiability-c.md#onnewwant)生命周期回调场景的枚举，用于 [setOnNewWantSkipScenarios](arkts-ability-uiabilitycontext-c.md#setonnewwantskipscenarios)接口。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## SCENARIO_MOVE_MISSION_TO_FRONT

```TypeScript
SCENARIO_MOVE_MISSION_TO_FRONT = 0x00000001
```

<!--RP1-->系统接口missionManager.moveMissionToFront接口触发的UIAbility到前台场景。<!--RP1End-->

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## SCENARIO_SHOW_ABILITY

```TypeScript
SCENARIO_SHOW_ABILITY = 0x00000002
```

[showAbility](arkts-ability-uiabilitycontext-c.md#showability)接口触发的UIAbility到前台场景。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## SCENARIO_BACK_TO_CALLER_ABILITY_WITH_RESULT

```TypeScript
SCENARIO_BACK_TO_CALLER_ABILITY_WITH_RESULT = 0x00000004
```

[backToCallerAbilityWithResult](arkts-ability-uiabilitycontext-c.md#backtocallerabilitywithresult) 接口触发的UIAbility到前台场景。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例**

```TypeScript
import { AbilityConstant, contextConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    // 设置不触发onNewWant的场景，组合多个场景标志位
    let scenarios: number = contextConstant.Scenarios.SCENARIO_MOVE_MISSION_TO_FRONT |
      contextConstant.Scenarios.SCENARIO_SHOW_ABILITY |
      contextConstant.Scenarios.SCENARIO_BACK_TO_CALLER_ABILITY_WITH_RESULT;

    try {
      // 设置跳过onNewWant的场景
      this.context.setOnNewWantSkipScenarios(scenarios).then(() => {
        // 执行正常业务
        console.info('setOnNewWantSkipScenarios succeed');
      }).catch((err: BusinessError) => {
        // 处理业务逻辑错误
        console.error(`setOnNewWantSkipScenarios failed, code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`setOnNewWantSkipScenarios failed, code is ${code}, message is ${message}`);
    }
  }
}
```
