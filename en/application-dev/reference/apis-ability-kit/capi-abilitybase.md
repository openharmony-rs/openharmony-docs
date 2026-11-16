# AbilityBase

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=e01350d88b673bbd3dab4c76e0fbd0aea5a52870 translatedAt=2026-11-04T09:48:06.201Z pushedAt=2026-11-04T09:51:09.693Z nl=1 -->

## Overview

As the basic definition module of Ability Kit, AbilityBase provides definitions and APIs for [Want](capi-want-h.md), which can be used to transfer information between application components.

**System capability**: SystemCapability.Ability.AbilityBase

**Since**: 15

## Files

| Name| Description|
| -- | -- |
| [ability_base_common.h](capi-ability-base-common-h.md) | Declares the error codes defined by AbilityBase.|
| [want.h](capi-want-h.md) | Want is a carrier for information transfer between objects and can be used for information transfer between application components. One use case of Want is as a parameter for startAbility, which contains the specified launch target and the related data to be carried at launch. For example, the bundleName and abilityName fields indicate the Bundle name of the application where the target Ability resides and the Ability name within the corresponding package, respectively. When Ability A needs to launch Ability B and pass some data, Want can be used as a carrier to pass the data to Ability B. |
