# TriggerInfo

作为[trigger](arkts-ability-wantagent-trigger-f.md)的入参定义触发WantAgent所需要的信息。

**起始版本：** 7

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## code

```TypeScript
code: number
```

表示传递的公共事件代码，仅当WantAgent实例的[OperationType](arkts-ability-wantagent-operationtype-e.md)类型是'SEND_COMMON_EVENT'时有效。该字段与发布者使用[commonEventManager.publish](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-commoneventmanager-publish-f.md)发布公共事件时，传递[CommonEventPublishData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-commoneventpublishdata-commoneventpublishdata-i.md)公共事件数据中的`code`字段含义一致。取值根据公共事件类型确定。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## extraInfo

```TypeScript
extraInfo?: { [key: string]: any }
```

额外数据，用于传递自定义扩展信息。参数为键值对对象，key为字符串类型的键名，value为任意类型的值。建议使用类型安全的extraInfos属性替代本属性。如果同时设置了extraInfo和extraInfos，extraInfos将生效，extraInfo将被忽略。

**类型：** { [key: string]: any }

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## extraInfos

```TypeScript
extraInfos?: Record<string, Object>
```

额外数据，用于传递自定义键值对信息，类型安全。推荐使用该属性替代extraInfo。与extraInfo同时设置时，本属性优先生效。当需要在触发WantAgent时携带额外的自定义数据时传入此参数，不传入时默认为null，不会携带额外数据。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## permission

```TypeScript
permission?: string
```

表示公共事件订阅者的权限。仅当WantAgent实例的[OperationType](arkts-ability-wantagent-operationtype-e.md)类型是'SEND_COMMON_EVENT'时，该字段生效。若权限为null，则接收方无需具备任何权限。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## want

```TypeScript
want?: Want
```

对象间信息传递的载体，可以用于应用组件间的信息传递。

**类型：** [Want](arkts-ability-app-ability-want-want-c.md)

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
