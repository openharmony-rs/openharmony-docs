# GroupInfo (System API)

Defines the group notification information.

**Since:** 26.0.0

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## groupTitle

```TypeScript
groupTitle?: string
```

Group title displayed after notifications are grouped. This parameter is valid only when the notification is the latest one in the notification group. This parameter is left empty by default.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## isGroupIcon

```TypeScript
isGroupIcon?: boolean
```

Whether to use the **smallIcon** field in NotificationRequest as the group icon displayed after notifications are grouped. Whether to use the **smallIcon** field as the group icon when the notification is the latest one in the notification group and the **smallIcon** field is passed. The default value is **false**.  
- **true**: yes.  
- **false**: no.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
