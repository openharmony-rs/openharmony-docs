# NotificationSortingMap (System API)

```TypeScript
export interface NotificationSortingMap
```

The **NotificationSortingMap** module provides APIs for defining the sorting information of active notifications in all subscribed notifications.

**Since:** 7

<!--Device-unnamed-export interface NotificationSortingMap--><!--Device-unnamed-export interface NotificationSortingMap-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## sortedHashCode

```TypeScript
readonly sortedHashCode: Array<string>
```

Hash codes for notification sorting.

**Type:** Array&lt;string&gt;

**Since:** 7

<!--Device-NotificationSortingMap-readonly sortedHashCode: Array<string>--><!--Device-NotificationSortingMap-readonly sortedHashCode: Array<string>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## sortings

```TypeScript
readonly sortings: Record<string, NotificationSorting>
```

Array of notification sorting information.

**Type:** Record&lt;string, [NotificationSorting](arkts-notification-notificationsorting-i-sys.md)&gt;

**Since:** 7

<!--Device-NotificationSortingMap-readonly sortings: Record<string, NotificationSorting>--><!--Device-NotificationSortingMap-readonly sortings: Record<string, NotificationSorting>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
