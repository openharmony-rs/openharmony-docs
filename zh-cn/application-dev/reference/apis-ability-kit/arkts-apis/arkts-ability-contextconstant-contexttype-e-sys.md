# ContextType

上下文类型

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## SERVICE_EXTENSION_CONTEXT

```TypeScript
SERVICE_EXTENSION_CONTEXT = 5
```

业务扩展上下文类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## UI_SERVICE_EXTENSION_CONTEXT

```TypeScript
UI_SERVICE_EXTENSION_CONTEXT = 6
```

UI服务扩展上下文类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core\

**系统接口：** 此接口为系统接口。

## AUTO_FILL_EXTENSION_CONTEXT

```TypeScript
AUTO_FILL_EXTENSION_CONTEXT = 7
```

自动填充扩展上下文类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { UIAbility, contextConstant } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    hilog.info(0x0000, 'testTag', `%{public}s`, 'Ability onCreate');
    // 判断Context类型是否为UIAbilityContext
    let result = this.context.isContextOf(contextConstant.ContextType.UIABILITY_CONTEXT);
    hilog.info(0x0000, 'testTag', `match contextType result is:%{public}s`, JSON.stringify(result));
  }
}
```
