# WantAgentInfo

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The module defines the information required for triggering the WantAgent.

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
| wants          | Array\<[Want](js-apis-app-ability-want.md)\>                   | No| No| Array of all Want objects. Currently, only one Want is supported. The array is reserved for future capability expansion. If multiple values are passed in, only the first member in the array is used.<br>**Atomic service API**: This API can be used in atomic services since API version 12.   |
| operationType<sup>(deprecated)</sup>  | [wantAgent.OperationType](js-apis-wantAgent.md#operationtype)         | No| Yes| Operation type.<br>This attribute is supported since API version 7 and deprecated since API version 11. You are advised to use actionType<sup>11+</sup> instead.<br>**Atomic service API**: This API can be used in atomic services since API version 12.      |
| actionType<sup>11+</sup> | [abilityWantAgent.OperationType](js-apis-app-ability-wantAgent.md#operationtype)         | No| Yes| Operation type.<br>**Atomic service API**: This API can be used in atomic services since API version 12.              |
| requestCode    | number                          | No| No| Custom request code, which is used to identify the operation to execute.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| wantAgentFlags<sup>(deprecated)</sup> | Array<[wantAgent.WantAgentFlags](js-apis-wantAgent.md#wantagentflags)> | No| Yes| Array of flags for using the WantAgent object.<br>This attribute is supported since API version 7 and deprecated since API version 11. You are advised to use actionFlags<sup>11+</sup> instead.<br>**Atomic service API**: This API can be used in atomic services since API version 12.          |
| actionFlags<sup>11+</sup> | Array<[abilityWantAgent.WantAgentFlags](js-apis-app-ability-wantAgent.md#wantagentflags)> | No| Yes| Array of flags for using the WantAgent object.<br>**Atomic service API**: This API can be used in atomic services since API version 12.          |
| extraInfo      | { [key: string]: any }            | No| Yes| Extra information.<br>**Atomic service API**: This API can be used in atomic services since API version 12.          |
| extraInfos<sup>11+</sup> | Record\<string, Object>            | No| Yes| Extra information. You are advised to use this property to replace **extraInfo**. When this property is set, **extraInfo** does not take effect.<br>**Atomic service API**: This API can be used in atomic services since API version 12.              |
