# WantAgentInfo (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

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

Defines the information required for triggering a WantAgent object. The information can be used as an input parameter in [getWantAgent](js-apis-app-ability-wantAgent.md#wantagentgetwantagent) to obtain a specified WantAgent object.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name          | Type                           | Read-Only| Optional| Description                  |
| -------------- | ------------------------------ | ---- | ---- |---------------------- |
| userId<sup>22+</sup>    | number | No| Yes| User ID.<br>The value must be greater than or equal to 0.<br>The default value is the user ID of the caller. <br>**Model restriction**: This API can be used only in the stage model.|


## LocalWantAgentInfo<sup>20+</sup>

Defines the information required for triggering a local WantAgent object. The information can be used as an input parameter in [createLocalWantAgent](js-apis-app-ability-wantAgent-sys.md#wantagentcreatelocalwantagent20) to obtain a local WantAgent object.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

| Name          | Type                           | Read-Only | Optional | Description                  |
| -------------- | ------------------------------- | --- | ---- | ---------------------- |
| wants          | Array\<[Want](js-apis-app-ability-want.md)\>                          | No  | No  | Array of all Want objects. Currently, only one Want object is supported. If multiple values are passed in, only the first member in the array is used.   |
| operationType  | [abilityWantAgent.OperationType](js-apis-app-ability-wantAgent.md#operationtype)        | No  | Yes  | Type of the operation to execute.     |
| requestCode    | number                          | No  | No  | Custom request code, which is used to identify the operation to execute.|
