# EnvironmentCallback

EnvironmentCallback模块提供对系统环境变化监听回调的能力。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-declare interface EnvironmentCallback--><!--Device-unnamed-declare interface EnvironmentCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onConfigurationUpdated

```TypeScript
onConfigurationUpdated(config: Configuration): void
```

[注册系统环境变化的监听]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 后，在系统环境变化时触发回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-EnvironmentCallback-onConfigurationUpdated(config: Configuration): void--><!--Device-EnvironmentCallback-onConfigurationUpdated(config: Configuration): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 变化后的Configuration对象。 |

## onMemoryLevel

```TypeScript
onMemoryLevel(level: AbilityConstant.MemoryLevel): void
```

[注册系统环境变化的监听]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 后，在系统内存变化时触发回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-EnvironmentCallback-onMemoryLevel(level: AbilityConstant.MemoryLevel): void--><!--Device-EnvironmentCallback-onMemoryLevel(level: AbilityConstant.MemoryLevel): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | AbilityConstant.MemoryLevel | 是 | 整机可用内存级别，对应的触发场景详见[AbilityConstant.MemoryLevel]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

