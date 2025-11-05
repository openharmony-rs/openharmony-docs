# Device Usage Statistics Overview (for System Applications Only)
<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @cheng-shichang-->
<!--Designer: @zhouben25-->
<!--Tester: @fenglili18-->
<!--Adviser: @Brilliantry_Rui-->

Device usage statistics include the usage of applications, notifications, and the system. In application usage statistics, you can query the application usage, event logs, and bundle groups. The application records (usage history statistics and event records) cached by components are flushed to the database for persistent storage within 30 minutes after an event is reported.

## Introduction

Currently, you can use device usage statistics APIs to access only statistics on the application usage.

- The application usage statistics are flushed:
  1. Every 30 minutes.
  2. Upon system time changes.
  3. Upon start of a new day.

- You can use **query()** (including **isIdleState**) to obtain:
  1. Events of all applications based on the specified start time and end time.
  2. Application usage duration based on the specified start time and end time.
  3. Events of the caller application based on the specified start time and end time.
  4. Application usage duration in the specified time frame at the specified interval (daily, weekly, monthly, or annually).
  5. Priority group of the caller application.
  6. Whether an application is in the idle state.
  7. Obtain the number of FA usage records. **maxNum** specifies the maximum number of FA usage records returned. If **maxNum** is not specified, the default value **1000** will be used.
  8. Number of notifications from applications based on the specified start time and end time.
  9. System events (hibernation, wakeup, lock, and unlock) that occur between the specified start time and end time.
  10. Priority group of the caller application or a given application.

- You can use **set()** to:

  Set the group for the application specified by **bundleName**.

- You can use **register()** to:

  Register a callback for application group changes. When an application group of the user changes, the change is notified to all applications that have registered the callback.

- You can use **unregister()** to:

  Unregister the callback for application group changes.

## Required Permissions
- Only system applications can call the device usage statistics APIs. They must request the **ohos.permission.BUNDLE_ACTIVE_INFO** permission to call these APIs.
