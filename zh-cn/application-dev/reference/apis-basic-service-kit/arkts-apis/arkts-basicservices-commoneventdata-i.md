# CommonEventData

表示公共事件的数据。

**起始版本：** 7

**系统能力：** SystemCapability.Notification.CommonEvent

## bundleName

```TypeScript
bundleName?: string
```

表示包名称，默认为空字符串。

**类型：** string

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Notification.CommonEvent

## code

```TypeScript
code?: number
```

表示订阅者接收到的公共事件数据（number类型）。该字段取值与发布者使用
[commonEventManager.publish](arkts-basicservices-publish-f.md#publish-2)
发布公共事件时，通过[CommonEventPublishData](arkts-basicservices-commoneventpublishdata-i.md)中的`code`字段传递的数据一致。默认值为0。

**类型：** number

**默认值：** 0

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Notification.CommonEvent

## data

```TypeScript
data?: string
```

表示订阅者接收到的公共事件数据（string类型）。该字段取值与发布者使用
[commonEventManager.publish](arkts-basicservices-publish-f.md#publish-2)
发布公共事件时，通过[CommonEventPublishData](arkts-basicservices-commoneventpublishdata-i.md)中的`data`字段传递的数据一致。

**类型：** string

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Notification.CommonEvent

## event

```TypeScript
event: string
```

表示当前接收的公共事件名称。

**类型：** string

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Notification.CommonEvent

## parameters

```TypeScript
parameters?: { [key: string]: any }
```

表示订阅者接收到的公共事件的附加信息。该字段取值与发布者使用
[commonEventManager.publish](arkts-basicservices-publish-f.md#publish-2)
发布公共事件时，通过[CommonEventPublishData](arkts-basicservices-commoneventpublishdata-i.md)中的`parameters`字段传递的数据一致。

**类型：** { [key: string]: any }

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Notification.CommonEvent

