# @ohos.app.ability.insightIntentProvider(意图提供方管理能力)

本模块为意图提供方提供管理能力，如主动发送指定意图的执行结果。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace insightIntentProvider--><!--Device-unnamed-declare namespace insightIntentProvider-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { insightIntentProvider } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [sendExecuteResult](arkts-ability-insightintentprovider-sendexecuteresult-f.md#sendexecuteresult-1) | 如果意图提供方需要在业务处理的特定流程中主动发送意图执行结果，可以先通过[setReturnModeForUIAbilityForeground接口](arkts-ability-app-ability-insightintentcontext-insightintentcontext-c.md#setreturnmodeforuiabilityforeground)或[setReturnModeForUIExtensionAbility接口](arkts-ability-app-ability-insightintentcontext-insightintentcontext-c.md#setreturnmodeforuiextensionability)将意图执行结果返回形式[ReturnMode](arkts-ability-insightintent-returnmode-e.md)设置为FUNCTION，然后调用该接口发送意图执行结果，适用于[配置类意图](../../../application-models/insight-intent-config-development.md)。使用Promise异步回调。 |
| [sendIntentResult](arkts-ability-insightintentprovider-sendintentresult-f.md#sendintentresult-1) | 如果意图提供方需要在业务处理的特定流程中主动发送意图执行结果，可以先通过[setReturnModeForUIAbilityForeground接口](arkts-ability-app-ability-insightintentcontext-insightintentcontext-c.md#setreturnmodeforuiabilityforeground)或[setReturnModeForUIExtensionAbility接口](arkts-ability-app-ability-insightintentcontext-insightintentcontext-c.md#setreturnmodeforuiextensionability)将意图执行结果返回形式[ReturnMode](arkts-ability-insightintent-returnmode-e.md)设置为FUNCTION，然后调用该接口发送意图执行结果。适用于[@InsightIntentEntry](arkts-ability-app-ability-insightintentdecorator-insightintententry-d.md#insightintententry)修饰的[装饰器类意图](../../../application-models/insight-intent-decorator-development.md)。使用Promise异步回调。 |
