# WantAgentInfo(系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

定义触发WantAgent所需要的信息。

> **说明：**
> 
> 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 
> 当前页面仅包含本模块的系统接口，其他公开接口参见[WantAgentInfo](js-apis-inner-wantAgent-wantAgentInfo.md)。

## 导入模块

```ts
import { wantAgent as abilityWantAgent } from '@kit.AbilityKit';
```

## WantAgentInfo

WantAgentInfo定义触发WantAgent所需要的信息，可以作为[getWantAgent](js-apis-app-ability-wantAgent.md#wantagentgetwantagent)的入参创建指定的WantAgent对象。WantAgent创建后，可通过系统或其他应用在满足特定条件时触发执行，实现延迟执行指定动作的功能。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称           | 类型                            | 只读 | 可选 | 说明                   |
| -------------- | ------------------------------ | ---- | ---- |---------------------- |
| userId<sup>23+</sup>    | number | 否 | 是 | 用户ID。<br>取值范围：大于等于0。<br>当需要指定特定用户时传入此参数，适用于跨用户操作场景（如系统应用管理其他用户的应用）。不传入时默认为调用方所在用户ID。<br>**模型约束**：此接口仅可在Stage模型下使用。|


## LocalWantAgentInfo<sup>20+</sup>

LocalWantAgentInfo定义触发本地WantAgent所需要的信息，可以作为[createLocalWantAgent](js-apis-app-ability-wantAgent-sys.md#wantagentcreatelocalwantagent20)的入参创建指定的本地WantAgent对象。本地WantAgent仅在当前应用进程内有效，适用于进程内的延迟执行场景。 

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

| 名称           | 类型                            | 只读  | 可选  | 说明                   |
| -------------- | ------------------------------- | --- | ---- | ---------------------- |
| wants          | Array\<[Want](js-apis-app-ability-want.md)\>                          | 否   | 否   | 将被执行的动作列表。当前只支持一个Want。传入多个Want时，系统仅使用wants数组的第一个成员，其他成员将被忽略。    |
| operationType  | [abilityWantAgent.OperationType](js-apis-app-ability-wantAgent.md#operationtype)        | 否   | 是   | 将被执行的动作类型，用于指定WantAgent的触发方式（如启动Ability、发送事件等）。具体取值参见OperationType枚举说明。|
| requestCode    | number                          | 否   | 否   | 开发者自定义的请求码，用于标识将被执行的动作，便于后续通过该请求码识别和匹配对应的动作。建议使用唯一值以避免混淆。|