# EnabledNotificationCallbackData (System API)

```TypeScript
export interface EnabledNotificationCallbackData
```

Returns the changes of the application enabling state.

**Since:** 8

<!--Device-unnamed-export interface EnabledNotificationCallbackData--><!--Device-unnamed-export interface EnabledNotificationCallbackData-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## bundle

```TypeScript
readonly bundle: string
```

Bundle name of the application.

**Type:** string

**Since:** 8

<!--Device-EnabledNotificationCallbackData-readonly bundle: string--><!--Device-EnabledNotificationCallbackData-readonly bundle: string-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## enable

```TypeScript
readonly enable: boolean
```

Whether the application notification is enabled.  
- **true**: enabled.  
- **false**: disabled.

**Type:** boolean

**Since:** 8

<!--Device-EnabledNotificationCallbackData-readonly enable: boolean--><!--Device-EnabledNotificationCallbackData-readonly enable: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## uid

```TypeScript
readonly uid: number
```

UID of the application.

**Type:** number

**Since:** 8

<!--Device-EnabledNotificationCallbackData-readonly uid: int--><!--Device-EnabledNotificationCallbackData-readonly uid: int-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
