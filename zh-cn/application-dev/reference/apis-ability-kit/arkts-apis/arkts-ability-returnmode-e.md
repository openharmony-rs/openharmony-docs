# ReturnMode

意图执行结果返回给意图拉起方的返回形式。

**起始版本：** 23

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## CALLBACK

```TypeScript
CALLBACK = 0
```

表示意图执行结果将由[意图执行基类](arkts-ability-insightintentexecutor-c.md)中的
[onExecuteInUIAbilityForegroundMode](@ohos.app.ability.InsightIntentExecutor:InsightIntentExecutor#onExecuteInUIAbilityForegroundMode(name: string, param: Record<string, Object>, pageLoader: window.WindowStage))
接口或
[onExecuteInUIExtensionAbility](@ohos.app.ability.InsightIntentExecutor:InsightIntentExecutor#onExecuteInUIExtensionAbility(name: string, param: Record<string, Object>, pageLoader: UIExtensionContentSession))
接口返回。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## FUNCTION

```TypeScript
FUNCTION = 1
```

表示意图执行结果会延迟返回，直到开发者主动调用[意图提供方管理能力](@ohos.app.ability.insightIntentProvider:insightIntentProvider)中的
[sendExecuteResult](@ohos.app.ability.insightIntentProvider:insightIntentProvider.sendExecuteResult)接口或
[sendIntentResult](@ohos.app.ability.insightIntentProvider:insightIntentProvider.sendIntentResult)接口返回意图执行结
果。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

