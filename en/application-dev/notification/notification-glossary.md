# Glossary

<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=b0e965054b682272b6c9e3890a6020b1129a6551 translatedAt=2026-08-22T02:19:35.324Z pushedAt=2026-08-22T07:08:35.833Z -->

## C

### Content Type

Content layout type of a notification, which determines how the notification is displayed in the notification center. When publishing a notification, select the appropriate content type (such as plain text, long text, multi-line text, image, or Live View) based on display requirements, and use it together with the corresponding notification content object.

### Cross-device Collaboration

A mechanism that synchronizes and forwards notification messages across multiple device forms such as phones, wearables, tablets, and PCs, enabling notification sharing among multiple devices.

### Customized Ringtone

A non-default audio prompt resource specified when an app publishes a notification. It can come from a preset resource file of the app or an audio file in the sandbox.

## D

### Distributed Notification

A notification message that is synchronized across multiple devices through distributed communication capabilities, allowing the same notification to be displayed on different devices. Once enabled, notifications can flow among multiple networked devices, so that you can view and handle the same notification on any collaborative device.

### Do Not Disturb Mode

A mode that suppresses reminder behaviors such as notification ringtones and vibrations within a specified period. It can be configured to take effect once, daily, or on specified dates. It prevents notifications from disturbing users during specific periods without losing notification content.

## G

### Geofence

A virtual geographic area defined by latitude, longitude, and radius, used as a condition-based trigger for notifications. When a device enters or exits the geofence, a preconfigured notification is triggered. It applies to location-based scenarios such as arrival reminders and location check-ins.

### Group Notification

A notification that aggregates multiple notifications with the same group name into a single grouped display. In the collapsed state, it is presented as a summary; when expanded, the details of each notification can be viewed. It is used to categorize and organize notifications of the same type and reduce redundancy in the notification list.

## L

### Live View Notification

A notification form that supports real-time content updates and continuously displays dynamically changing information in the notification center. It applies to scenarios that require real-time status synchronization, such as navigation, ride-hailing, and food delivery. It is used to display the progress of long-running tasks such as audio recording, screen recording, audio/video playback, calls, and timers in real time. It is not persistently stored, and its lifecycle is consistent with that of the publisher.

### Local Notification

A notification that is directly published and displayed locally on the client by an application through Notification Kit. After publication, it produces the corresponding ringtone, vibration, banner, lock screen, status bar icon, and notification center display based on the notification type and scenario. Its lifecycle is consistent with that of the local publisher, distinguishing it from distributed notifications that are synchronized across devices.

## N

### Normal Live View

A type of live view notification that is created and updated directly by system applications. It supports multiple update modes such as incremental and full updates, as well as extended content such as attached images and buttons, and is used by system applications to display real-time status.

### Notification Action Button

An interactive action button displayed in a notification. It allows users to trigger a `WantAgent` action by tapping the button. A notification can contain up to two buttons, which are suitable for quick actions such as "Reply" and "Mark as read".

### Notification Authorization

A user permission that an app must obtain before publishing notifications. The system displays a dialog box for the user to decide whether to allow the app to send notifications.

### Notification Badge

A notification count indicator displayed as a number in the upper right corner of an application icon. It informs users of the number of unread notifications and dynamically increases or decreases as notifications are added or viewed.

### Notification Button

An interactive button displayed in a Live View, as part of the Live View notification content. You can configure a button name list and an icon list, with a maximum of three buttons. Unlike a notification action button, it is dedicated to Live View scenarios.

### Notification Capsule

A component that displays information in a capsule shape in a Live View. It can carry a title, an icon, and a background color, and is used to prominently display key status or summary information within the limited area of a live notification.

### Notification Card

A card displayed on the device after notification publication. It appears in the notification center, status bar, and other locations for users to view and interact with.

### Notification Center

A system UI on the device that centrally displays and manages notifications. After a notification is published, it is displayed in the notification center, where users can view, manage, and delete notifications. An application can query the number and details of its existing notifications in the notification center.

### Notification Check

A mechanism by which a system application authenticates the content and channel of a notification before it is published. A notification is displayed only after passing the check; otherwise, it is blocked. This mechanism enables unified control and filtering before notifications are displayed.

### Notification Content

The content structure of a notification, including the notification title and body, which provides content description APIs for multiple notification types. An application selects the corresponding content type API to construct notification content based on display requirements (such as plain text, long text, multi-line text, images, and Live View). Plain-text notification content serves as the base structure for other notification types.

### Notification Flags

A setting item used to reduce notification reminder methods (such as sound, vibration, banner, and lock screen) as needed. You can use it to disable certain reminder behaviors of a specific notification, achieving finer-grained reminder control than notification channels.

### Notification Kit

A Kit that provides a local notification publication channel for developers. It pushes notifications generated by an application to users locally on the client, and produces display effects such as ringtone, vibration, banner, lock screen, status bar icon, and notification center based on the notification type and publication scenario.

### Notification Progress

A description field used to display progress bar information in a Live View. It is a component of Live View notification content.

### Notification Proxy

A notification published by one application on behalf of another. When published, it carries the identity information of the proxied application so that the notification is displayed under the identity of the proxied application. It applies to scenarios where a system application sends notifications on behalf of third-party applications in a unified manner.

### Notification Request

A data carrier that describes all information of a notification, including notification content, identifiers, display styles, and interaction behaviors. When publishing a notification, you use it to specify the attributes of the notification. It serves as the basis for notification publication and update.

### Notification Reminder Mode

The specific methods used to remind users when a notification arrives, including ringtone, lock screen, banner, screen wake-up, vibration, and the status bar notification icon. It is used to configure specific reminder behaviors for a given application or notification channel, so that different notifications remind users in different ways.

### Notification Setting

The setting states of notification reminder method switches, including the switch states of lock screen notifications, banner notifications, home screen badges, vibration, ringtone, and the application notification enablement state. It is used to query or configure the notification reminder methods of an application, and can open the notification settings screen for users to modify manually.

### Notification Slot

A classification mechanism for managing notification reminder methods (sound, vibration, lock screen display, and so on). Notifications in the same slot share consistent reminder behavior. By creating and configuring slots, you can uniformly manage the reminder behavior, such as ringtone, vibration, and banner, of different categories of notifications from the same application.

### Notification Smart Aggregation

A mechanism that automatically merges multiple related notifications into one aggregation group based on aggregation scenarios and rules. You can set the title and summary of an aggregation group to intelligently aggregate a large number of similar notifications and improve the readability of the notification list.

### Notification Snooze

A mechanism that sets an existing notification to remind again after a specified time interval. Each setting triggers only one reminder, and the reminder method is the same as that of the original notification. After the setting takes effect, the original notification is deleted. This mechanism applies to scenarios where a user wants to postpone handling a notification and receive a reminder again later.

### Notification Sorting

Provides sorting information about activity notifications, including the notification channel, notification level, and unique notification identifier. The system sorts and displays activity notifications among the subscribed notifications based on the sorting information. You can obtain the sorting information of all activity notifications in batches through the notification sorting map.

### Notification Subscription

A mechanism by which an application registers a subscriber with the notification subsystem to receive notification changes. It supports subscribing to notifications published by all apps or by specified apps.

### Notification Update

An update mechanism in which a newly published notification replaces an existing notification when both have the same ID and tag. If no notification with the same ID exists, a new notification is created. You can set the `updateOnly` field to control whether only updates are allowed without creating a new notification.

## P

### Priority Notification

A feature that marks specific types of notifications as priority notifications through priority policies. It supports methods such as intelligent recognition, user keyword matching, and app rule matching, and covers management capabilities including the priority master switch, app-level switch, intelligent service enablement status, and priority policies. It ensures that important notifications (such as payment and repayment, account transaction reminders, logistics progress, and missed calls) receive priority processing and display, and is distinct from the notification priority of a notification channel.

## S

### Silent Reminder

A notification reminder method at the application level. After it is enabled for an application, notifications published by the application do not trigger reminder behaviors such as ringtones and vibration upon delivery, and are only displayed silently. It applies to notification scenarios that do not require immediate interruption of the user, and is independent of the system-level Do Not Disturb mode.

### System Live View

A Live View notification created by the system agent. Third-party applications cannot create it directly, but can update specified content in it by publishing a notification with the same ID, so that third-party applications can reuse the system Live View capability under controlled conditions.