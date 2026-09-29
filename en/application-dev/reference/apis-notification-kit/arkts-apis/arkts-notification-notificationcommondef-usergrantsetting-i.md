# UserGrantSetting

```TypeScript
export interface UserGrantSetting
```

Describes the user authorization settings.

**Since:** 26.0.0

<!--Device-unnamed-export interface UserGrantSetting--><!--Device-unnamed-export interface UserGrantSetting-End-->

**System capability:** SystemCapability.Notification.Notification

## grantedBundleInfos

```TypeScript
readonly grantedBundleInfos?: Array<GrantedBundleInfo>
```

List of apps for which the **Allow access to notifications on this device** switch is toggled on.

**Type:** Array&lt;[GrantedBundleInfo](arkts-notification-notificationcommondef-grantedbundleinfo-i.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserGrantSetting-readonly grantedBundleInfos?: Array<GrantedBundleInfo>--><!--Device-UserGrantSetting-readonly grantedBundleInfos?: Array<GrantedBundleInfo>-End-->

**System capability:** SystemCapability.Notification.Notification

## userGrantEnabled

```TypeScript
readonly userGrantEnabled: boolean
```

Whether the **Allow access to notifications on this device** switch is toggled on. true: **yes**; false: **no**.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserGrantSetting-readonly userGrantEnabled: boolean--><!--Device-UserGrantSetting-readonly userGrantEnabled: boolean-End-->

**System capability:** SystemCapability.Notification.Notification
