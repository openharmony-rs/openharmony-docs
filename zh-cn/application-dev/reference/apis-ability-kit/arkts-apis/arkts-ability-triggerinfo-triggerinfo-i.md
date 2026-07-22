# TriggerInfo

作为[trigger](../../../reference/apis-ability-kit/js-apis-app-ability-wantAgent.md#wantagenttrigger)的入参定义触发WantAgent所需要的信息。

**起始版本：** 7

<!--Device-unnamed-export interface TriggerInfo--><!--Device-unnamed-export interface TriggerInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## code

```TypeScript
code: number
```

表示传递的公共事件数据，仅当WantAgent实例的[OperationType](../../../reference/apis-ability-kit/js-apis-app-ability-wantAgent.md#operationtype)类型是'SEND_COMMON_EVENT'时有效。该字段与发布者使用[commonEventManager.publish](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-commoneventmanager-publish-f.md#publish)发布公共事件时，传递[CommonEventPublishData](../../../reference/apis-basic-services-kit/js-apis-inner-commonEvent-commonEventPublishData.md#属性)公共事件数据中的`code`字段含义一致。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TriggerInfo-code: int--><!--Device-TriggerInfo-code: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## extraInfo

```TypeScript
extraInfo?: { [key: string]: any }
```

额外数据。

**类型：** { [key: string]: any }

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TriggerInfo-extraInfo?: { [key: string]: any }--><!--Device-TriggerInfo-extraInfo?: { [key: string]: any }-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## extraInfos

```TypeScript
extraInfos?: Record<string, Object>
```

额外数据。推荐使用该属性替代extraInfo，设置该属性后，extraInfo不再生效。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TriggerInfo-extraInfos?: Record<string, Object>--><!--Device-TriggerInfo-extraInfos?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## permission

```TypeScript
permission?: string
```

表示公共事件订阅者的权限。仅当WantAgent实例的[OperationType](../../../reference/apis-ability-kit/js-apis-app-ability-wantAgent.md#operationtype)类型是'SEND_COMMON_EVENT'时，该字段生效。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TriggerInfo-permission?: string--><!--Device-TriggerInfo-permission?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## want

```TypeScript
want?: Want
```

对象间信息传递的载体，可以用于应用组件间的信息传递。

**类型：** Want

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TriggerInfo-want?: Want--><!--Device-TriggerInfo-want?: Want-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

