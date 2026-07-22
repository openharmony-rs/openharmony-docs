# StartAbilityParameter

定义启动Ability参数，可以作为入参，调用[startAbility](arkts-ability-featureability-startability-f.md#startability)启动指定的Ability。

**起始版本：** 6

<!--Device-unnamed-export interface StartAbilityParameter--><!--Device-unnamed-export interface StartAbilityParameter-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## abilityStartSetting

```TypeScript
abilityStartSetting?: { [key: string]: any }
```

启动Ability的特殊属性，当开发者启动Ability时，该属性可以作为调用中的输入参数传递。

**类型：** { [key: string]: any }

**起始版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-StartAbilityParameter-abilityStartSetting?: { [key: string]: any }--><!--Device-StartAbilityParameter-abilityStartSetting?: { [key: string]: any }-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## abilityStartSettings

```TypeScript
abilityStartSettings?: Record<string, Object>
```

启动Ability的特殊属性，当开发者启动Ability时，该属性可以作为调用中的输入参数传递。推荐使用该属性替代abilityStartSetting，设置该属性后，abilityStartSetting不再生效。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 11

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-StartAbilityParameter-abilityStartSettings?: Record<string, Object>--><!--Device-StartAbilityParameter-abilityStartSettings?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## want

```TypeScript
want: Want
```

启动Ability的want信息。

**类型：** Want

**起始版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-StartAbilityParameter-want: Want--><!--Device-StartAbilityParameter-want: Want-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

