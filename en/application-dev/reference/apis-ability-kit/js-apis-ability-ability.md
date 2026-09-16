# @ohos.ability.ability (Ability Module)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @lidongrui-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=aa0fb9ac9cb84f1c8f057e9ad47e9d44face8fc4 translatedAt=2026-09-03T09:26:01.043Z pushedAt=2026-09-05T10:47:30.167Z -->

The module provides all level-2 module APIs for developers to export.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { ability } from '@kit.AbilityKit';
```

## DataAbilityHelper

type DataAbilityHelper = _DataAbilityHelper

Defines the level-2 module DataAbilityHelper.

**System capability**: SystemCapability.Ability.AbilityRuntime.FAModel

**Model restriction**: This API can be used only in the FA model.

| Type| Description|
| --- | --- |
| [_DataAbilityHelper](js-apis-inner-ability-dataAbilityHelper.md) | Level-2 module DataAbilityHelper.|


## PacMap

type PacMap = _PacMap

Defines the level-2 module PacMap.

**System capability**: SystemCapability.Ability.AbilityRuntime.FAModel

**Model restriction**:
API version 11+: This API can be used under the Stage model and FA model.

| Type| Description|
| --- | --- |
| [_PacMap](js-apis-inner-ability-dataAbilityHelper.md#pacmap) | PacMap type, used to store key-value pair data. |


## DataAbilityOperation

type DataAbilityOperation = _DataAbilityOperation

Defines the level-2 module DataAbilityOperation.

**System capability**: SystemCapability.Ability.AbilityRuntime.FAModel

**Model restriction**: This API can be used only in the FA model.

| Type| Description|
| --- | --- |
| [_DataAbilityOperation](js-apis-inner-ability-dataAbilityOperation.md) | Level-2 module DataAbilityOperation.|


## DataAbilityResult

type DataAbilityResult = _DataAbilityResult

Defines the level-2 module DataAbilityResult.

**System capability**: SystemCapability.Ability.AbilityRuntime.FAModel

**Model restriction**: This API can be used only in the FA model.

| Type| Description|
| --- | --- |
| [_DataAbilityResult](js-apis-inner-ability-dataAbilityResult.md) | Level-2 module DataAbilityResult.|


## AbilityResult

type AbilityResult = _AbilityResult

Defines the level-2 module AbilityResult.

**System capability**: SystemCapability.Ability.AbilityBase

**Model restriction**: This API can be used only in the FA model.

| Type| Description|
| --- | --- |
| [_AbilityResult](js-apis-inner-ability-abilityResult.md) | Level-2 module AbilityResult.|


## ConnectOptions

type ConnectOptions = _ConnectOptions

Defines the level-2 module ConnectOptions.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the FA model.

| Type| Description|
| --- | --- |
| [_ConnectOptions](js-apis-inner-ability-connectOptions.md) | Level-2 module ConnectOptions.|


## StartAbilityParameter

type StartAbilityParameter = _StartAbilityParameter

Defines the level-2 module StartAbilityParameter.

**System capability**: SystemCapability.Ability.AbilityRuntime.FAModel

**Model restriction**: This API can be used only in the FA model.

| Type| Description|
| --- | --- |
| [_StartAbilityParameter](js-apis-inner-ability-startAbilityParameter.md) | Level-2 module StartAbilityParameter.|


**Example**
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