# Common Event and Notification Subsystem Changelog

## Behavior of the largeIcon Property in NotificationRequest Is Changed

**Access Level**

Public API

**Change Reason**

The notification fails to be published because the notification icon is too large.

**Change Impact**

This change is a compatible change.

Before change:
When the **largeIcon** property is too large, the notification is intercepted. As a result, the notification fails to be published.

After change:
When the **largeIcon** property is too large, the notification can be published properly. In this case, only the text content is displayed.

**Start API Level**

12

**Change Since**

OpenHarmony 5.0.1.1

**Key API/Component Changes**
The property of **NotificationRequest**: **largeIcon**.

**Adaptation Guide**
This is a compatibility change. No adaptation is required.
