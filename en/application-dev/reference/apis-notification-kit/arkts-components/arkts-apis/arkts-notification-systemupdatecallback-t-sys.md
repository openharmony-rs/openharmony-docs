# SystemUpdateCallback (System API)

```TypeScript
export type SystemUpdateCallback = (data: SubscribeCallbackData) => void
```

Returns the notification information carrying system property values. type SystemUpdateCallback = (data: SubscribeCallbackData) =&gt; void

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md) | Yes | Notification information that carries the system property value. |
