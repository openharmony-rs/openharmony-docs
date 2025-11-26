# @ohos.app.ability.insightIntent (意图调用基础能力)

本模块提供意图调用基础能力。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { insightIntent } from '@kit.AbilityKit';
```

## ExecuteMode

意图调用执行模式。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| UI_ABILITY_FOREGROUND | 0 | 将UIAbility在前台显示。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。 |
| UI_ABILITY_BACKGROUND | 1 | 将UIAbility在后台拉起。<br>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。 |
| UI_EXTENSION_ABILITY | 2 | 拉起UIExtensionAbility。 |

## ExecuteResult

意图调用的返回结果。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| code | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否 | 否 | 意图调用返回的错误码。<br/>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 11<br/>**ArkTS-Sta起始版本：** 23 |
| result | ArkTS-Dyn: Record<string, Object><br>ArkTS-Sta: Record<string, RecordData> | 否 | 是 | 意图调用返回的结果。<br/>**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 11<br>**ArkTS-Sta起始版本：** 23 |
| uris<sup>18+</sup> | Array&lt;string&gt; | 否 | 是 | 意图调用时，意图执行方给意图调用方授权的URI列表。<br/>**原子化服务API**：从API version 18开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 18<br/>**ArkTS-Sta起始版本：** 23 |
| flags<sup>18+</sup> | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否 | 是 | 意图调用时，意图执行方给意图调用方授权的uris的[flags](js-apis-app-ability-wantConstant.md#flags)。<br/>**原子化服务API**：从API version 18开始，该接口支持在原子化服务中使用。 <br/>**说明：**<br/>该参数仅支持FLAG_AUTH_READ_URI_PERMISSION、FLAG_AUTH_WRITE_URI_PERMISSION、FLAG_AUTH_READ_URI_PERMISSION\|FLAG_AUTH_WRITE_URI_PERMISSION。<br>**ArkTS-Dyn起始版本：** 18<br/>**ArkTS-Sta起始版本：** 23 |

## IntentEntity<sup>20+</sup>

[@InsightIntentEntity](./js-apis-app-ability-InsightIntentDecorator.md#insightintententity)装饰器的基类，用于定义意图实体。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 20

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| entityId | string | 否 | 否 | 意图实体的ID。<br/>**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。 |

## IntentResult\<T><sup>20+</sup>

用于定义意图执行返回结果。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 20

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| code | number | 否 | 否 | 意图调用返回的错误码。<br/>**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。 |
| result | T | 否 | 是 | 意图调用返回的结果。<br/>**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。 |

## ReturnMode<sup>23+</sup>

意图执行结果返回给意图拉起方的返回形式。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| CALLBACK | 0 | 表示意图执行结果将由[意图执行基类](./js-apis-app-ability-insightIntentExecutor.md)中的[onExecuteInUIAbilityForegroundMode](./js-apis-app-ability-insightIntentExecutor.md#onexecuteinuiabilityforegroundmode)接口或[onExecuteInUIExtensionAbility](./js-apis-app-ability-insightIntentExecutor.md#onexecuteinuiextensionability)接口返回。<br>**原子化服务API**：从API version 23开始，该接口支持在原子化服务中使用。 |
| FUNCTION | 1 | 表示意图执行结果会延迟返回，直到开发者主动调用[意图提供方管理能力](./js-apis-app-ability-insightIntentProvider.md)中的[sendExecuteResult](./js-apis-app-ability-insightIntentProvider.md#insightintentprovidersendexecuteresult)接口或[sendIntentResult](./js-apis-app-ability-insightIntentProvider.md#insightintentprovidersendintentresult)接口返回意图执行结果。<br>**原子化服务API**：从API version 23开始，该接口支持在原子化服务中使用。 |