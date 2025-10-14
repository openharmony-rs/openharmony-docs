# @ohos.ability.ability (Ability模块)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @lidongrui-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

Ability模块将二级模块API组织在一起方便开发者进行导出。

> **说明：**
> 
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { ability } from '@kit.AbilityKit';
```

## DataAbilityHelper

type DataAbilityHelper = _DataAbilityHelper

DataAbilityHelper二级模块。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_DataAbilityHelper](js-apis-inner-ability-dataAbilityHelper.md) | DataAbilityHelper二级模块。 |


## PacMap

type PacMap = _PacMap

PacMap二级模块。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

| 类型 | 说明 |
| --- | --- |
| [_PacMap](js-apis-inner-ability-dataAbilityHelper.md#pacmap) | DataAbilityHelper二级模块。 |


## DataAbilityOperation

type DataAbilityOperation = _DataAbilityOperation

DataAbilityOperation二级模块。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_DataAbilityOperation](js-apis-inner-ability-dataAbilityOperation.md) | DataAbilityOperation二级模块。 |


## DataAbilityResult

type DataAbilityResult = _DataAbilityResult

DataAbilityResult二级模块。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_DataAbilityResult](js-apis-inner-ability-dataAbilityResult.md) | DataAbilityResult二级模块。 |


## AbilityResult

type AbilityResult = _AbilityResult

AbilityResult二级模块。

**系统能力**：SystemCapability.Ability.AbilityBase

**模型约束**：此接口仅可在FA模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_AbilityResult](js-apis-inner-ability-abilityResult.md) | AbilityResult二级模块。 |


## ConnectOptions

type ConnectOptions = _ConnectOptions

ConnectOptions二级模块。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在FA模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_ConnectOptions](js-apis-inner-ability-connectOptions.md) | ConnectOptions二级模块。 |


## StartAbilityParameter

type StartAbilityParameter = _StartAbilityParameter

StartAbilityParameter二级模块。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_StartAbilityParameter](js-apis-inner-ability-startAbilityParameter.md) | StartAbilityParameter二级模块。 |


**示例：**
```ts
import { ability } from '@kit.AbilityKit';

let dataAbilityHelper: ability.DataAbilityHelper;
let pacMap: ability.PacMap;
let dataAbilityOperation: ability.DataAbilityOperation;
let dataAbilityResult: ability.DataAbilityResult;
let abilityResult: ability.AbilityResult;
let connectOptions: ability.ConnectOptions;  
let startAbilityParameter: ability.StartAbilityParameter;
```