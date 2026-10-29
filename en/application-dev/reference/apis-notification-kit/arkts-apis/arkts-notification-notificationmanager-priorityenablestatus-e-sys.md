# PriorityEnableStatus (System API)

```TypeScript
export enum PriorityEnableStatus
```

Describes the enabling status of the priority notification for an application.

**Since:** 23

<!--Device-notificationManager-export enum PriorityEnableStatus--><!--Device-notificationManager-export enum PriorityEnableStatus-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## DISABLE

```TypeScript
DISABLE = 0
```

The priority notification is disabled.

**Since:** 23

<!--Device-PriorityEnableStatus-DISABLE = 0--><!--Device-PriorityEnableStatus-DISABLE = 0-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## ENABLE

```TypeScript
ENABLE = 2
```

All application notifications are set as priority notifications.

**Since:** 23

<!--Device-PriorityEnableStatus-ENABLE = 2--><!--Device-PriorityEnableStatus-ENABLE = 2-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## ENABLE_BY_INTELLIGENT

```TypeScript
ENABLE_BY_INTELLIGENT = 1
```

The priority switch of the application notification is in the intelligent recognition state. It can be set to [priority notification](../../../notification/notification-glossary.md#priority-notification) through intelligent recognition, user keyword matching, application rule matching, and other methods.

**Since:** 23

<!--Device-PriorityEnableStatus-ENABLE_BY_INTELLIGENT = 1--><!--Device-PriorityEnableStatus-ENABLE_BY_INTELLIGENT = 1-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
