# BaseContext

BaseContext抽象类用于表示继承的子类Context是Stage模型还是FA模型，是所有Context类型的父类。

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## stageMode

```TypeScript
stageMode: boolean
```

表示是否Stage模型。<br>true：[Stage模型](../../../../application-models/ability-terminology.md#stage模型)。<br>false：
[FA模型](../../../../application-models/ability-terminology.md#fa模型)。

**类型：** boolean

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

