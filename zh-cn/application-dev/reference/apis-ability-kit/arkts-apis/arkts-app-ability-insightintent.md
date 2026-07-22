# @ohos.app.ability.insightIntent

本模块提供[意图框架](../../../application-models/insight-intent-overview.md)基础定义。

**起始版本：** 11

<!--Device-unnamed-declare namespace insightIntent--><!--Device-unnamed-declare namespace insightIntent-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AppIntentEntity](arkts-ability-insightintent-appintententity-c.md) | 定义AppIntentEntity。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ExecuteResult](arkts-ability-insightintent-executeresult-i.md) | 意图执行的返回结果。 |
| [IntentEntity](arkts-ability-insightintent-intententity-i.md) | 意图实体结构体定义，用于定义意图执行过程中涉及的关键信息对象，包括意图参数和意图执行结果等。  开发者通过继承该类来定义意图实体，继承类需使用[@InsightIntentEntity](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententity)装饰。 |
| [IntentResult](arkts-ability-insightintent-intentresult-i.md) | 意图执行的返回结果，支持[泛型类型](../../../quick-start/introduction-to-arkts.md#泛型类和接口)。 |
| [QueryEntityParam](arkts-ability-insightintent-queryentityparam-i.md) | 查询实体的参数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ExecuteMode](arkts-ability-insightintent-executemode-e.md) | 意图执行模式。表示系统入口触发意图执行时传递的执行模式，每个意图支持的执行模式在意图开发时定义。 |
| [QueryType](arkts-ability-insightintent-querytype-e.md) | 查询实体模式的枚举。 |
| [ReturnMode](arkts-ability-insightintent-returnmode-e.md) | 意图执行结果返回给意图拉起方的返回形式。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ExecuteMode](arkts-ability-insightintent-executemode-e-sys.md) | 意图执行模式。表示系统入口触发意图执行时传递的执行模式，每个意图支持的执行模式在意图开发时定义。 |
<!--DelEnd-->

