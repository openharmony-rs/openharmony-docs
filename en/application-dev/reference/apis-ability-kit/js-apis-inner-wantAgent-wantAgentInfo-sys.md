# WantAgentInfo (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=115c4befa0ce664a3634abae6b31f62f9b5ae3cf translatedAt=2026-09-03T12:22:06.571Z pushedAt=2026-09-05T10:47:30.905Z -->

The module defines the information required for triggering a WantAgent.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> This topic describes only system APIs provided by the module. For details about its public APIs, see [WantAgentInfo](js-apis-inner-wantAgent-wantAgentInfo.md).

## Modules to Import

```ts
import { wantAgent as abilityWantAgent } from '@kit.AbilityKit';
```

## WantAgentInfo

WantAgentInfo defines the information required to trigger a WantAgent. It can be used as an input parameter of [getWantAgent](js-apis-app-ability-wantAgent.md#wantagentgetwantagent) to create a specified WantAgent object. After a WantAgent is created, it can be triggered and executed by the system or other applications when specific conditions are met, implementing delayed execution of a specified action.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name          | Type                           | Read-Only| Optional| Description                  |
| -------------- | ------------------------------ | ---- | ---- |---------------------- |
| userId<sup>23+</sup>    | number | No | Yes | User ID.<br>Value range: greater than or equal to 0.<br>Pass this parameter when a specific user needs to be specified. It applies to cross-user operation scenarios (for example, a system application manages applications of other users). If not passed, the default is the user ID of the caller.<br>**Model constraint:** This API can be used only in the stage model.|


## LocalWantAgentInfo<sup>20+</sup>

LocalWantAgentInfo defines the information required to trigger a local WantAgent. It can be used as an input parameter of [createLocalWantAgent](js-apis-app-ability-wantAgent-sys.md#wantagentcreatelocalwantagent20) to create a specified local WantAgent object. A local WantAgent is valid only within the current application process and is suitable for delayed execution scenarios within the process. 

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

| Name          | Type                           | Read-Only | Optional | Description                  |
| -------------- | ------------------------------- | --- | ---- | ---------------------- |
| wants          | Array\<[Want](js-apis-app-ability-want.md)\>                          | No   | No   | List of actions that will be executed. Currently, only one Want is supported. When multiple Wants are passed in, the system uses only the first member of the wants array and ignores the others.    |
| operationType  | [abilityWantAgent.OperationType](js-apis-app-ability-wantAgent.md#operationtype)        | No   | Yes   | Type of the action that will be executed, used to specify the trigger mode of the WantAgent (for example, starting an ability or sending an event). For details about the values, see the OperationType enum description.|
| requestCode    | number                          | No   | No   | Request code defined by the developer, used to identify the action that will be executed, so that the corresponding action can be identified and matched by this request code later. A unique value is recommended to avoid confusion.|