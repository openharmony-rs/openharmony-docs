# OH_CommonEvent
<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

## Overview

This module provides APIs of the Common Event Service, which are implemented in C. It provides cross-process event communication capabilities for apps based on the publication-subscription model. After a publisher publishes a common event, the system delivers the event to all subscribers who have subscribed to the event based on the event name. In this way, decoupled communication between apps and between apps and the system is implemented.

This module provides the following capabilities:

- **Event subscription and unsubscription**: creates subscription information, creates subscribers, subscribes to or unsubscribes from specified common events, and uses a callback to receive event data when the event is triggered.
- **Event publishing**: publishes common events. You can set the publishing attributes, such as ordered/disordered events, the permission, app package name, code, data, and additional information.
- **Event data access**: obtains the event name, result code, result data, publisher app package name, and additional information (parameters and key-value (KV) pairs, supporting reading and writing of data of the int/long/bool/char/double types and their array types) from the callback data.
- **Control of ordered common events**: terminates an ordered common event, clears the termination status, obtains/sets the result code and result data, and completes the event.
- **System common event constants**: provide system-defined common event name constants (such as battery level change, screen on/off, Wi-Fi status, and USB status) to facilitate subscription to system status changes.
- **Error codes**: enumerates the error codes that may be returned during operations.

**Use scenarios:** When an app needs to detect system status changes (such as the battery level, screen status, network connection, Wi-Fi status, USB status, and package installation) or broadcast service messages between multiple apps, APIs provided by this module can be used to subscribe to or publish common events.

**System capability:** SystemCapability.Notification.CommonEvent

**Since:** 12

## Files

| Name| Description|
| -- | -- |
| [oh_commonevent.h](capi-oh-commonevent-h.md) | Provides operation functions for subscription, unsubscription, publishing, event data access, additional information read/write, and ordered event control, enumerates the error codes, and defines the core data types.|
| [oh_commonevent_support.h](capi-oh-commonevent-support-h.md) | Provides system-defined common event name constants (such as **COMMON_EVENT_BATTERY_CHANGED** and **COMMON_EVENT_SCREEN_ON**) for reference during subscription. This file does not provide functions.|
