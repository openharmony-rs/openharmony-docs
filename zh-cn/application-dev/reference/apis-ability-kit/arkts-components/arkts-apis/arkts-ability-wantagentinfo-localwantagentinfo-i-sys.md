# LocalWantAgentInfo（系统接口）

```TypeScript
export interface LocalWantAgentInfo
```

LocalWantAgentInfo定义触发本地WantAgent所需要的信息，可以作为[createLocalWantAgent](../../../reference/apis-ability-kit/js-apis-app-ability-wantAgent-sys.md#wantagentcreatelocalwantagent20)的入参创建指定的本地WantAgent对象。本地WantAgent仅在当前应用进程内有效，适用于进程内的延迟执行场景。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## operationType

```TypeScript
operationType?: abilityWantAgent.OperationType
```

将被执行的动作类型，用于指定WantAgent的触发方式（如启动Ability、发送事件等）。具体取值参见OperationType枚举说明。

**类型：** [abilityWantAgent.OperationType](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-wantagent.md)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## requestCode

```TypeScript
requestCode: number
```

开发者自定义的请求码，用于标识将被执行的动作，便于后续通过该请求码识别和匹配对应的动作。建议使用唯一值以避免混淆。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## wants

```TypeScript
wants: Array<Want>
```

将被执行的动作列表。当前只支持一个Want。传入多个Want时，系统仅使用wants数组的第一个成员，其他成员将被忽略。

**类型：** Array&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt;

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。
