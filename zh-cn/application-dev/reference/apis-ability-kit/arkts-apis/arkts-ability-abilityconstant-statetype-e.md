# StateType

保存应用数据场景原因，该类型为枚举。配合UIAbility的 [onSaveState()](arkts-ability-app-ability-uiability-uiability-c.md#onsavestate) 方法使用，可以实现[UIAbility备份恢复](../../../application-models/ability-recover-guideline.md)。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## CONTINUATION

```TypeScript
CONTINUATION = 0
```

应用迁移场景。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## APP_RECOVERY

```TypeScript
APP_RECOVERY = 1
```

应用故障恢复场景。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例**

```TypeScript
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onSaveState(reason: AbilityConstant.StateType, wantParam: Record<string, Object>) {
    if (reason === AbilityConstant.StateType.CONTINUATION) {
      console.info('Save the ability data when the ability is continuing.');
    }
    return AbilityConstant.OnSaveResult.ALL_AGREE;
  }
}
```
