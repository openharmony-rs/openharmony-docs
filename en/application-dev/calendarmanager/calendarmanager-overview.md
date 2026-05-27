# About This Kit

<!--Kit: Calendar Kit-->
<!--Subsystem: Applications-->
<!--Owner: @qq_42718467-->
<!--Designer: @windsky6-->
<!--Tester: @z30055209-->
<!--Adviser: @ge-yafang-->

Calendar Kit provides calendar and event management capabilities, typically referring to APIs that can be used to access and manipulate calendar data. These APIs allow you to integrate time-related event services (such as travel, dining, sports, and entertainment) from other applications with the system calendar, enabling features like event management, event creation, and querying.

## Available Capabilities

Calendar Kit includes account management and event management.

- Create a calendar account.

  You can create a calendar account unique to your application. Upon successful account creation, an account ID is returned. The account ID is an auto-increment primary key in the data table and serves as the unique identifier for the account.

- Obtain calendar accounts.

  You can obtain information about a specified calendar account or all calendar accounts created by the current application.

- Delete a calendar account.

  You can delete a specified calendar account. After a calendar account is deleted, all events associated with that calendar account will also be deleted.

- Create an event.

  After obtaining the calendar account information, you can create an event under the obtained calendar account. When creating an event, you can set an event reminder time. A reminder notification will pop up when the reminder time arrives.

  After the event is successfully created, an event ID will be returned. The event ID is an auto-increment primary key in the data table and serves as the unique identifier for the event.

- Delete an event.

  You can specify an event ID to delete an event, and can delete one or multiple events at the same time.

- Update events.

  You can update event information based on the event ID, including the event title, location, start time, end time, reminder time, and other details.

- Query events.

  You can query events by event ID, event title, event start time, and event end time.

## Features

**One-click calendar service**: With the permanent authorization mechanism, after the user allows your application to read and write the system calendar, the corresponding event service can be written into the calendar in the form of deeplink. According to the reminder rules set by yourself, when an event is about to expire or expires, the corresponding service button will be displayed in the calendar application, notification, and widgets. Users can tap the button to redirect to the service landing page in one step.

## Working Principles

Calendar Kit provides a set of APIs for obtaining calendar accounts, and writing calendar events to or reading events from the obtained accounts. If an event has a reminder time set, the system sends a reminder to the user when the set time arrives.

## Constraints

- Currently, the use of Calendar Kit's related capabilities and APIs is only supported under the stage model.

- To use the related capabilities of Calendar Kit, you need to obtain permissions to read or write calendars and events. For details, see [Declaring Permissions](../security/AccessToken/declare-permissions.md).

  - When reading calendars or events, you need to request the **ohos.permission.READ_CALENDAR** or **ohos.permission.READ_WHOLE_CALENDAR** permission.

  - When adding, deleting, or modifying calendars or events, you need to request the **ohos.permission.WRITE_CALENDAR** or **ohos.permission.WRITE_WHOLE_CALENDAR permission**.

  After requesting the corresponding permissions, the supported related operations are shown in the following table.

  | Requested Permissions                     | Supported Calendar Account Operation Scope                       | Supported Event Operation Scope                                           |
  | ------------------------------ | -------------------------------------------- | ------------------------------------------------------------ |
  | ohos.permission.READ_CALENDAR  | - Read the system default calendar account<br>- Read calendar accounts created by the current application | - Read events created by the current application under the system default calendar account<br/>- Read events created by the current application under calendar accounts created by the current application |
  | ohos.permission.WRITE_CALENDAR | - Add, delete, or modify calendar accounts created by the current application               | - Add, delete, or modify events created by the current application under the system default calendar account<br>- Add, delete, or modify events created by the current application under calendar accounts created by the current application |
  | ohos.permission.READ_WHOLE_CALENDAR | - Read all calendar accounts                      | - Read events created by all applications              |
  | ohos.permission.WRITE_WHOLE_CALENDAR | - Add, delete, or modify all calendar accounts                | - Add, delete, or modify events created by all applications          |

<!--RP1-->
<!--RP1End-->