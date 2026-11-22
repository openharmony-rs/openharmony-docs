# Cross-Device Notification Overview
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=75c0f0cf34944e262b28608d43f8d720a6e6e07e translatedAt=2026-11-03T09:17:02.335Z pushedAt=2026-11-03T09:17:02.335Z nl=1 -->

[Cross-device collaboration](notification-glossary.md#cross-device-collaboration) notifications aim to use the phone as the center to implement collaborative interaction of notification messages with other devices such as watches. Typical scenarios are as follows:

<!--Del-->
  - [Cross-Device Notification Management (for System Applications Only)](./notification-distributed-notdistributed-sys.md): Configure cross-device notifications for system applications and enable this feature as required.
<!--DelEnd-->
  - [Clearing Repeated Notifications Across Devices](./notification-distributed-messageid.md): Clear repeated notifications published across devices and by the local device to prevent multiple notifications from disturbing users.

## Constraints
  - Devices supported for [cross-device collaboration](notification-glossary.md#cross-device-collaboration): Starting from API version 18, notification message collaboration between phones and wearables is supported. Starting from API version 20, notification message collaboration between phones and tablets/PCs/2-in-1 devices is supported.
  - [Notification slot types](../../application-dev/reference/apis-notification-kit/js-apis-notificationManager.md#slottype) supported for cross-device notification:
    - Wearable: social communication notifications with quick reply (SOCIAL_COMMUNICATION) and LIVE_VIEW.
    - Tablet: **SOCIAL_COMMUNICATION**, **SERVICE_INFORMATION**, **LIVE_VIEW**, and **CUSTOMER_SERVICE**.
    - PC/2-in-1 device: **SOCIAL_COMMUNICATION**, **SERVICE_INFORMATION**, and **CUSTOMER_SERVICE**.

## Working Principles

![distributed_overview](figures/distributed_overview.png)
