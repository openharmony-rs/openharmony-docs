# NotificationSorting (System API)

The **NotificationSorting** module provides APIs for defining the sorting information of active notifications.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.

## Properties

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name     | Type             | Read-Only  | Optional| Description                    |
|-----------| ---------------- | -------|----- |-------------------------|
| slot        | [NotificationSlot](js-apis-inner-notification-notificationSlot.md) | Yes| No| Notification slot type.                 |
| ranking     | number                                                             | Yes| No| Notification level. If this parameter is not set, the default value is used based on the notification slot type.|
| hashCode    | string                                                             | Yes| No| Unique ID of the notification.               |
