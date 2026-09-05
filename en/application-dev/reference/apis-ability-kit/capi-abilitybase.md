# AbilityBase

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b3bc27a342923ac4fafa55153b55c4f3b627330f translatedAt=2026-09-03T08:29:01.775Z pushedAt=2026-09-05T10:47:30.051Z -->

## Overview

As the basic definition module of Ability Kit, AbilityBase provides definitions and APIs for [Want](capi-want-h.md), which can be used to transfer information between application components.

**System capability**: SystemCapability.Ability.AbilityBase

**Since**: 15

## Files

| Name| Description|
| -- | -- |
| [ability_base_common.h](capi-ability-base-common-h.md) | Declares the error codes defined by AbilityBase.|
| [want.h](capi-want-h.md) | Want is a carrier for information transfer between objects, and can be used for information transfer between application components. One of the use scenarios of Want is to serve as a parameter of startAbility. It contains the specified launch target and the related data to carry during startup. For example, the bundleName and abilityName fields respectively indicate the bundle name of the application where the target Ability resides and the Ability name in the corresponding package. When Ability A needs to start Ability B and pass in some data, Want can be used as a carrier to pass the data to Ability B. |
