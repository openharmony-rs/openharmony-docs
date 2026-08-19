# TriggerInfo

作为trigger的入参定义触发WantAgent所需 要的信息。

**起始版本：** 23

<!--Device-unnamed-export interface TriggerInfo--><!--Device-unnamed-export interface TriggerInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## code

```TypeScript
code: int
```

表示传递的公共事件数据，仅当WantAgent实例的 OperationType类型是' SEND_COMMON_EVENT'时有效。该字段与发布者使用 [commonEventManager.publish](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-commoneventmanager-publish-f.md) 发布公共事件时，传递 [CommonEventPublishData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-commoneventpublishdata-commoneventpublishdata-i.md) 公共事件数据中的`code`字段含义一致。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TriggerInfo-code: int--><!--Device-TriggerInfo-code: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## extraInfo

```TypeScript
extraInfo?: Record<string, RecordData>
```

额外数据。

**类型：** Record&lt;string, [RecordData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt;

**起始版本：** 23

<!--Device-TriggerInfo-extraInfo?: Record<string, RecordData>--><!--Device-TriggerInfo-extraInfo?: Record<string, RecordData>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## extraInfos

```TypeScript
extraInfos?: Record<string, RecordData>
```

额外数据。推荐使用该属性替代extraInfo，设置该属性后，extraInfo不再生效。

**类型：** Record&lt;string, [RecordData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt;

**起始版本：** 23

<!--Device-TriggerInfo-extraInfos?: Record<string, RecordData>--><!--Device-TriggerInfo-extraInfos?: Record<string, RecordData>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## permission

```TypeScript
permission?: string
```

表示公共事件订阅者的权限。仅当WantAgent实例的 OperationType类型是' SEND_COMMON_EVENT'时，该字段生效。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TriggerInfo-permission?: string--><!--Device-TriggerInfo-permission?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## want

```TypeScript
want?: Want
```

对象间信息传递的载体，可以用于应用组件间的信息传递。

**类型：** [Want](arkts-ability-app-ability-want-want-c.md)

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TriggerInfo-want?: Want--><!--Device-TriggerInfo-want?: Want-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

