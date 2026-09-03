# @ohos.app.ability.insightIntent (意图框架基础定义)(系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

本模块提供[意图框架](../../application-models/insight-intent-overview.md)基础定义。

> **说明：**
>
> 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口仅可在Stage模型下使用。
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.app.ability.insightIntent (意图框架基础定义)](js-apis-app-ability-insightIntent.md)。

## 导入模块

```ts
import { insightIntent } from '@kit.AbilityKit';
```

## ExecuteMode

意图执行模式。表示系统入口触发意图执行时传递的模式，每个意图支持的执行模式在意图开发时定义。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| SERVICE_EXTENSION_ABILITY | 3 | 拉起ServiceExtensionAbility。<br>**系统接口**：该接口为系统接口。|

## ExecuteResult

意图执行的返回结果。

**起始版本**：26.1.0

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| interactionInfo | [InteractionInfo](#interactioninfo) | 否 | 是 | 意图执行完成后返回的交互信息。|

## InteractionUI

定义当前意图执行完成后需要展示的交互界面的信息。

**起始版本**：26.1.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| interactionUIType | string | 否 | 否 | 交互界面的类型。 |

## InteractionModalUIExtension

定义当意图执行完成时模态UIExtension要显示为交互界面的信息，不支持分布式。继承自[InteractionUI](#interactionui)。

**起始版本**：26.1.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| interactionUIType | string | 否 | 否 | 交互界面的类型，固定为'MODAL_UIEXTENSION'。 |
| bundleName | string | 否 | 否 | 目标UIExtension能力的Bundle名称。 |
| moduleName | string | 否 | 否 | 目标UIExtension能力的模块名称。 |
| abilityName | string | 否 | 否 | 目标UIExtension能力的Ability名称。 |
| uiExtensionType | string | 否 | 否 | UIExtension的类型。 |
| uri | string | 否 | 否 | 传递给目标UIExtension的URI信息。 |
| parameters | Record\<string, Object\> | 否 | 否 | 传递给目标UIExtension的参数。 |

## InteractionInfo

定义当前意图执行完成后返回的交互信息。

**起始版本**：26.1.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| interactionUI | [InteractionUI](#interactionui) | 否 | 是 | 当前意图执行完成后需要展示的交互界面信息。 |

