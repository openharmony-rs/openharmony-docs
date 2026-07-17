# EnvironmentCallback

EnvironmentCallback模块提供对系统环境变化监听回调的能力。

**起始版本：** 9

<!--Device-unnamed-export default class EnvironmentCallback--><!--Device-unnamed-export default class EnvironmentCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { EnvironmentCallback } from '@kit.AbilityKit';
```

## onConfigurationUpdated

```TypeScript
onConfigurationUpdated(config: Configuration): void
```

[注册系统环境变化的监听](arkts-ability-applicationcontext-c.md#on-2)后，在系统环境变化时触发回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-EnvironmentCallback-onConfigurationUpdated(config: Configuration): void--><!--Device-EnvironmentCallback-onConfigurationUpdated(config: Configuration): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [Configuration](../../apis-arkui/arkts-components/arkts-arkui-common-configuration-i.md) | 是 | 变化后的Configuration对象。 |

**示例：**

参见[EnvironmentCallback使用](#environmentcallback使用)。

## onMemoryLevel

```TypeScript
onMemoryLevel(level: AbilityConstant.MemoryLevel): void
```

[注册系统环境变化的监听](arkts-ability-applicationcontext-c.md#on-2)后，在系统内存变化时触发回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-EnvironmentCallback-onMemoryLevel(level: AbilityConstant.MemoryLevel): void--><!--Device-EnvironmentCallback-onMemoryLevel(level: AbilityConstant.MemoryLevel): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | AbilityConstant.MemoryLevel | 是 | 整机可用内存级别，对应的触发场景详见[AbilityConstant.MemoryLevel](arkts-ability-abilityconstant-memorylevel-e.md)。 |

**示例：**

参见[EnvironmentCallback使用](#environmentcallback使用)。

