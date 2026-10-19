# WantAgentInfo

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=acba00b4edca6db1d20615b479cf478c7de4ec19 translatedAt=2026-09-03T12:22:39.190Z pushedAt=2026-09-05T10:47:30.907Z -->

WantAgentInfo defines the information required for triggering a WantAgent. It can be used as an input parameter of [getWantAgent](js-apis-app-ability-wantAgent.md#wantagentgetwantagent) to create a specified WantAgent object. It applies to scenarios where delayed execution of Ability startup, publishing of common events, and the like are required. It supports custom request codes and action execution attributes, helping developers flexibly control the behavior of a WantAgent.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { wantAgent as abilityWantAgent } from '@kit.AbilityKit';
```

## WantAgentInfo

Defines the information required for triggering a WantAgent object. The information can be used as an input parameter in [getWantAgent](js-apis-app-ability-wantAgent.md#wantagentgetwantagent) to obtain a specified WantAgent object.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name          | Type                           | Read-Only| Optional| Description                  |
| -------------- | ------------------------------ | ---- | ---- |---------------------- |
| wants          | Array\<[Want](js-apis-app-ability-want.md)\>                   | No | No | The wants array is a reserved capability. Currently, only one want is supported. If multiple wants are passed in, only the first member of the wants array is used.<br>**Atomic service API**: Since API version 12, this API is supported in atomic services.    |
|operationType<sup>(deprecated)</sup>  | [wantAgent.OperationType](js-apis-wantAgent.md#operationtype)         | No | Yes | Operation type. If this parameter is not set, no default operation type is used.<br/>Supported since API version 7 and deprecated since API version 11. You are advised to use actionType<sup>11+</sup> instead.<br>**Atomic service API**: Since API version 12, this API is supported in atomic services.|
|actionType<sup>11+</sup> | [abilityWantAgent.OperationType](js-apis-app-ability-wantAgent.md#operationtype)         | No | Yes | Action type. If this parameter is not set, no default action type is used.<br>**Atomic service API**: Since API version 12, this API is supported in atomic services.|
| requestCode    | number                          | No | No | Request code defined by the developer, used to identify the action to be executed. Supported since API version 7.<br>**Atomic service API**: Since API version 12, this API is supported in atomic services. |
|wantAgentFlags<sup>(deprecated)</sup> | Array<[wantAgent.WantAgentFlags](js-apis-wantAgent.md#wantagentflags)> | No | Yes | Action execution attribute. If this parameter is not set, no execution attribute is used.<br/>Supported since API version 7 and deprecated since API version 11. You are advised to use actionFlags<sup>11+</sup> instead.<br>**Atomic service API**: Since API version 12, this API is supported in atomic services.|
|actionFlags<sup>11+</sup> | Array<[abilityWantAgent.WantAgentFlags](js-apis-app-ability-wantAgent.md#wantagentflags)> | No | Yes | Action execution attribute. If this parameter is not set, no execution attribute is used.<br>**Atomic service API**: Since API version 12, this API is supported in atomic services.|
| extraInfo      | { [key: string]: any }            | No | Yes | Extra data used to pass custom extended information. This parameter is a key-value pair object, where key is a string key name and value is a value of any type. You are advised to use the type-safe extraInfos attribute instead. If both extraInfo and extraInfos are set, extraInfos takes effect and extraInfo is ignored.<br>**Atomic service API**: Since API version 12, this API is supported in atomic services.       |
| extraInfos<sup>11+</sup> | Record\<string, Object>            | No | Yes | Extra data used to pass custom key-value pair information in a type-safe manner. You are advised to use this attribute instead of extraInfo. When both are set, this attribute takes precedence. Pass this parameter when you need to carry additional custom data when triggering the WantAgent. If this parameter is not passed, it defaults to null and no extra data is carried.<br>**Atomic service API**: Since API version 12, this API is supported in atomic services. |
