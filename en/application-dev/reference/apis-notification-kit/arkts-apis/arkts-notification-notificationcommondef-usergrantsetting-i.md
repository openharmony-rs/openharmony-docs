# UserGrantSetting

Describes the user authorization settings.

**Since:** 26.0.0

**System capability:** SystemCapability.Notification.Notification

## grantedBundleInfos

```TypeScript
readonly grantedBundleInfos?: Array<GrantedBundleInfo>
```

List of apps for which the **Allow access to notifications on this device** switch is toggled on.

**Type:** Array&lt;[GrantedBundleInfo](arkts-notification-notificationcommondef-grantedbundleinfo-i.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

## userGrantEnabled

```TypeScript
readonly userGrantEnabled: boolean
```

Whether the **Allow access to notifications on this device** switch is toggled on. true: **yes**; false: **no**.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification
