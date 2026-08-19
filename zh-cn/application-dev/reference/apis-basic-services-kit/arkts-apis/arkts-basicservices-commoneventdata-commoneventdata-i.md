# CommonEventData

表示公共事件的数据。CommonEventData用于在公共事件订阅场景中承载 订阅者接收到的公共事件数据，包含事件名称、发布者包名、code数据、 data数据及附加参数等信息，适用于应用订阅并处理公共事件、 解析事件携带数据的场景。

**起始版本：** 23

<!--Device-unnamed-export interface CommonEventData--><!--Device-unnamed-export interface CommonEventData-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## bundleName

```TypeScript
bundleName?: string
```

表示发布公共事件的应用包名，默认为空字符串。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventData-bundleName?: string--><!--Device-CommonEventData-bundleName?: string-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## code

```TypeScript
code?: int
```

表示订阅者接收到的公共事件数据。该字段取值与发布者使用 [commonEventManager.publish](arkts-basicservices-commoneventmanager-publish-f.md) 发布公共事件时，通过[CommonEventPublishData](arkts-basicservices-commoneventpublishdata-commoneventpublishdata-i.md)中的`code`字段传递的数据一致。取值范围[-2147483648, 2147483647]，默认值为0。

**类型：** int

**默认值：** 0

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventData-code?: int--><!--Device-CommonEventData-code?: int-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## data

```TypeScript
data?: string
```

表示订阅者接收到的公共事件数据，数据大小不超过64KB。该字段取值与发布者使用 [commonEventManager.publish](arkts-basicservices-commoneventmanager-publish-f.md) 发布公共事件时，通过[CommonEventPublishData](arkts-basicservices-commoneventpublishdata-commoneventpublishdata-i.md)中的`data`字段传递的数据一致。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventData-data?: string--><!--Device-CommonEventData-data?: string-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## event

```TypeScript
event: string
```

表示当前接收的公共事件名称。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventData-event: string--><!--Device-CommonEventData-event: string-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## parameters

```TypeScript
parameters?: Record<string, RecordData>
```

表示订阅者接收到的公共事件的附加信息。该字段取值与发布者使用 [commonEventManager.publish](arkts-basicservices-commoneventmanager-publish-f.md) 发布公共事件时，通过[CommonEventPublishData](arkts-basicservices-commoneventpublishdata-commoneventpublishdata-i.md)中的`parameters`字段传递的数据一致。

**类型：** Record&lt;string, [RecordData](arkts-basicservices-recorddata-t.md)&gt;

**起始版本：** 23

<!--Device-CommonEventData-parameters?: Record<string, RecordData>--><!--Device-CommonEventData-parameters?: Record<string, RecordData>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

