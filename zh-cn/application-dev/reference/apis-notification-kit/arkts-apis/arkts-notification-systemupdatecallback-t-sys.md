# SystemUpdateCallback（系统接口）

```TypeScript
export type SystemUpdateCallback = (data: SubscribeCallbackData) => void
```

type SystemUpdateCallback = (data: SubscribeCallbackData) => void返回携带系统属性值通知信息的回调函数类型。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type SystemUpdateCallback = (data: SubscribeCallbackData) => void--><!--Device-unnamed-export type SystemUpdateCallback = (data: SubscribeCallbackData) => void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [SubscribeCallbackData](arkts-notification-notificationsubscribe-subscribecallbackdata-t-sys.md) | 是 | 返回携带系统属性值的通知信息。  |

