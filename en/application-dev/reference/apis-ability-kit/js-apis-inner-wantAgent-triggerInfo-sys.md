# TriggerInfo (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b3bc27a342923ac4fafa55153b55c4f3b627330f translatedAt=2026-09-03T12:20:45.633Z pushedAt=2026-09-05T10:47:30.901Z -->

As an input parameter of [trigger](js-apis-app-ability-wantAgent.md#wantagenttrigger), defines the information required to trigger the execution of a wantAgent.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only system APIs provided by the module. For details about its public APIs, see [TriggerInfo](js-apis-inner-wantAgent-triggerInfo.md).

## Modules to Import

```ts
import { wantAgent } from '@kit.AbilityKit';
```

## Properties

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name      | Type                | Read-Only| Optional| Description       |
| ---------- | ------------------- | ---- | ---- | ----------- |
| startOptions<sup>12+</sup>|[StartOptions](js-apis-app-ability-startOptions.md)         | No | Yes | Specifies the startup parameters when the wantAgent is triggered to start an Ability.<br>**Model restriction**: This API can be used only in the stage model. |