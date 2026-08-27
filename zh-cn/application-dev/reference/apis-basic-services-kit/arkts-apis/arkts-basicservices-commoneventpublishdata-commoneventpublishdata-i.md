# CommonEventPublishData

用于封装公共事件发布时携带的数据和属性，包括事件数据（code/data）、 订阅者权限、订阅者包名、是否有序/粘性事件及附加参数等，支持发布方对 公共事件接收方范围、事件投递顺序及粘性特性进行精细化控制，适用于 需要限定接收方、传递自定义事件数据或实现有序/粘性公共事件等场景。

> **说明：**
> 
> 如果不加限制，任何应用都可以订阅公共事件并读取公共事件携带的信息，应避免在公共事件中携带敏感信息。通过本模块的subscriberPermissions和bundleName参数，可以限制公共事件接收方的范围。

**起始版本：** 7

**系统能力：** SystemCapability.Notification.CommonEvent

## bundleName

```TypeScript
bundleName?: string
```

表示订阅者包名，用于限定将公共事件发布给指定包名的订阅者。默认为空。 当该参数为空时，表示不限制订阅者包名，所有订阅者都可以接收该公共事件。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.CommonEvent

## code

```TypeScript
code?: number
```

表示发布方传递的公共事件数据。默认值为0。

**类型：** number

**默认值：** 0

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.CommonEvent

## data

```TypeScript
data?: string
```

表示发布方传递的公共事件数据。数据大小不超过64KB， 超出限制时，事件发布失败。默认为空。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.CommonEvent

## isOrdered

```TypeScript
isOrdered?: boolean
```

表示是否是有序公共事件。默认为false。  
- true：有序公共事件，根据订阅者设置的优先级等级，优先将公共事件发送给优先级较高的订阅者，等待其成功接收该公共事件之后再将事件发送给优先级较低的订阅者。如果有多个订阅者具有相同的优先级，则他们将随机接收到公共事件。  
- false：无序公共事件，不考虑订阅者是否接收到该事件，也不保证订阅者接收到该事件的顺序与其订阅顺序一致。

**类型：** boolean

**默认值：** false

**起始版本：** 7

**系统能力：** SystemCapability.Notification.CommonEvent

## isSticky

```TypeScript
isSticky?: boolean
```

表示是否是粘性公共事件。默认为false。  
- true：粘性公共事件，能够让订阅者收到在订阅前已经发送的公共事件。  
- false：普通公共事件，只能让订阅者收到在订阅后才发送的公共事件。  
仅系统应用或系统服务允许发送粘性事件。  
[ohos.permission.COMMONEVENT_STICKY](../../../security/AccessToken/permissions-for-all.md#ohospermissioncommonevent_sticky)

**类型：** boolean

**默认值：** false

**起始版本：** 7

**需要权限：** ohos.permission.COMMONEVENT_STICKY

**系统能力：** SystemCapability.Notification.CommonEvent

## parameters

```TypeScript
parameters?: { [key: string]: any }
```

表示发布方传递的公共事件的附加信息，以键值对形式携带自定义参数。 默认为空。

**类型：** { [key: string]: any }

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.CommonEvent

## subscriberPermissions

```TypeScript
subscriberPermissions?: Array<string>
```

表示订阅者的权限，只有具备该权限的订阅者才能收到该公共事件。默认为空。 当该参数为空时，表示不限制订阅者的权限，所有订阅者都可以接收该公共事件。

**类型：** Array&lt;string&gt;

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.CommonEvent
