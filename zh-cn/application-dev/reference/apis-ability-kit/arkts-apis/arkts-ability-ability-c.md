# Ability

Ability类是应用生命周期调度的基本单元，是[UIAbility](arkts-app-ability-uiability.md)和
[ExtensionAbility](arkts-ability-extensionability-c.md)的基类，提供系统配置更新回调和系统内存级别变化回调能力。该基类不支持开发者直接继
承，开发者应根据具体的业务场景选择使用[UIAbility](arkts-app-ability-uiability.md)或
[ExtensionAbility](arkts-ability-extensionability-c.md)，相关指南参见
[Ability Kit简介](../../../../application-models/abilitykit-overview.md)。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onConfigurationUpdate

```TypeScript
onConfigurationUpdate(newConfig: Configuration): void
```

当系统环境变量发生变化时，系统会触发该回调。开发者可以重写该回调实现对系统环境变量变化时的响应，例如当系统语言类型发生变化时，应用可以在回调中进行定制化的处理等。

> **说明：**
>
> 该回调方法在实际触发时存在一定限制。例如如果开发者通过[setLanguage](arkts-ability-applicationcontext-c.md#setlanguage-1)接口设置
> 应用的语言，即便系统语言发生变化，系统也不再触发onConfigurationUpdate回调。详见
> [使用场景](../../../../application-models/subscribe-system-environment-variable-changes.md#使用场景)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newConfig | Configuration | 是 | 表示更新后的配置信息。 |

**示例：**

```TypeScript
// Ability是顶层基类，不支持开发者直接继承。故以派生类UIAbility举例说明。
import { UIAbility, Configuration } from '@kit.AbilityKit';

class MyUIAbility extends UIAbility {
  onConfigurationUpdate(config: Configuration) {
    console.info(`onConfigurationUpdate, config: ${JSON.stringify(config)}`);
  }
}

```

## onMemoryLevel

```TypeScript
onMemoryLevel(level: AbilityConstant.MemoryLevel): void
```

当整机可用内存变化到指定程度时，系统会触发该回调。开发者可以重写该回调实现对内存级别变化的响应，例如释放缓存数据等。

> **说明：**
>
> onMemoryLevel回调运行在当前进程的主线程中，如果在该回调中做耗时的UI组件释放，会阻塞主线程任务，因此不建议在该回调中释放UI组件。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | AbilityConstant.MemoryLevel | 是 | 整机可用内存级别，对应的触发场景详见[AbilityConstant.MemoryLevel](arkts-ability-memorylevel-e.md)。 |

**示例：**

```TypeScript
// Ability是顶层基类，不支持开发者直接继承。故以派生类UIAbility举例说明。
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

class MyUIAbility extends UIAbility {
  onMemoryLevel(level: AbilityConstant.MemoryLevel) {
    console.info(`onMemoryLevel, level: ${JSON.stringify(level)}`);
  }
}

```

