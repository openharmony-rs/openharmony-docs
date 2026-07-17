# CommonEventPublishData

包含公共事件内容和属性。

> **说明：**  
>  
> 如果不加限制，任何应用都可以订阅公共事件并读取相关信息，应避免在公共事件中携带敏感信息。通过本模块的subscriberPermissions和bundleName参数，可以限制公共事件接收方的范围。

**起始版本：** 7

<!--Device-unnamed-export interface CommonEventPublishData--><!--Device-unnamed-export interface CommonEventPublishData-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## bundleName

```TypeScript
bundleName?: string
```

表示订阅者包名称，只有包名为bundleName的订阅者才能收到该公共事件。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventPublishData-bundleName?: string--><!--Device-CommonEventPublishData-bundleName?: string-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## code

```TypeScript
code?: number
```

表示发布方传递的公共事件数据（number类型）。默认值为0。

**类型：** number

**默认值：** 0

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventPublishData-code?: int--><!--Device-CommonEventPublishData-code?: int-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## data

```TypeScript
data?: string
```

表示发布方传递的公共事件数据（string类型）。数据大小不超过64KB。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventPublishData-data?: string--><!--Device-CommonEventPublishData-data?: string-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## isOrdered

```TypeScript
isOrdered?: boolean
```

表示是否是有序事件。默认为false。

- true：有序公共事件，根据订阅者设置的优先级等级，优先将公共事件发送给优先级较高的订阅者，等待其成功接收该公共事件之后再将事件发送给优先级较低的订阅者。如果有多个订阅者具有相同的优先级，则他们将随机接收到公共事件。  
- false：无序公共事件，不考虑订阅者是否接收到该事件，也不保证订阅者接收到该事件的顺序与其订阅顺序一致。

**类型：** boolean

**默认值：** false

**起始版本：** 7

<!--Device-CommonEventPublishData-isOrdered?: boolean--><!--Device-CommonEventPublishData-isOrdered?: boolean-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## isSticky

```TypeScript
isSticky?: boolean
```

表示是否是粘性事件。默认为false。

- true：粘性公共事件，能够让订阅者收到在订阅前已经发送的公共事件。  
- false：普通公共事件，只能让订阅者收到在订阅后才发送的公共事件。

仅系统应用或系统服务允许发送粘性事件。

[ohos.permission.COMMONEVENT_STICKY](../../../../security/AccessToken/permissions-for-all.md#ohospermissioncommonevent_sticky)

**类型：** boolean

**默认值：** false

**起始版本：** 7

**需要权限：** ohos.permission.COMMONEVENT_STICKY

<!--Device-CommonEventPublishData-isSticky?: boolean--><!--Device-CommonEventPublishData-isSticky?: boolean-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## parameters

```TypeScript
parameters?: { [key: string]: any }
```

表示发布方传递的公共事件的附加信息。

**类型：** { [key: string]: any }

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventPublishData-parameters?: { [key: string]: any }--><!--Device-CommonEventPublishData-parameters?: { [key: string]: any }-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## subscriberPermissions

```TypeScript
subscriberPermissions?: Array<string>
```

表示订阅者的权限。

**类型：** Array<string>

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventPublishData-subscriberPermissions?: Array<string>--><!--Device-CommonEventPublishData-subscriberPermissions?: Array<string>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

