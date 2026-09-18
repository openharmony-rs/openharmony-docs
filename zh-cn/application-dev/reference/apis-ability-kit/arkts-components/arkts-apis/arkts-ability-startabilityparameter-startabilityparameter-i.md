# StartAbilityParameter

定义启动Ability参数，可以作为入参，调用[startAbility](arkts-ability-featureability-startability-f.md)启动指定的Ability。

**起始版本：** 6

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## abilityStartSetting

```TypeScript
abilityStartSetting?: { [key: string]: any }
```

启动Ability的特殊属性，用于配置窗口显示等相关参数。不配置时不应用特殊启动属性。支持abilityBounds、windowMode、displayId等配置项。

**类型：** { [key: string]: any }

**起始版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## abilityStartSettings

```TypeScript
abilityStartSettings?: Record<string, Object>
```

启动Ability的特殊属性（如abilityBounds、windowMode、displayId等）。不配置时不应用特殊启动属性。推荐使用该属性替代abilityStartSetting，设置该属性后，abilityStartSetting不再生效。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 11

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## want

```TypeScript
want: Want
```

启动Ability的want信息。

**类型：** [Want](arkts-ability-app-ability-want-want-c.md)

**起始版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel
