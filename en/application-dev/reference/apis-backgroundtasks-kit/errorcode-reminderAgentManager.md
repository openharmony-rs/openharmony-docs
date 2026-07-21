# reminderAgentManager Error Codes

<!--Kit: Background Tasks Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 1700001 Notification Disabled

**Error Message**

Notification is not enabled.

**Description**

The application is not allowed to send notifications when **publishReminder()** is called.

**Possible Causes**

1. The application has not requested the notification to be enabled.
2. The notification feature is not enabled for the application.

**Solution**

1. Use [notificationManager.requestEnableNotification](../apis-notification-kit/js-apis-notificationManager.md#notificationmanagerrequestenablenotification10) to request the notification to be enabled.
2. Enable notification for the application in the notification settings.

## 1700002 Too Many Reminders

**Error Message**

The number of reminders exceeds the limit.

**Description**

The number of reminders exceeds the limit when **publishReminder()** is called.

**Possible Causes**
<!--RP1-->
1. The maximum number of reminders for applications varies depending on the API version and application type:
    - For API version 26.0.0 or later: A maximum of 64 reminders can be set for a common application, and 10,000 can be set for a system application.
    - For API versions 10 to 25: A maximum of 30 reminders can be set for a common application, and 10,000 can be set for a system application.
    - For API version 9 and earlier versions: A maximum of 30 reminders can be set for a single application.
2. Since API version 10, the total number of reminders for all applications cannot exceed 12,000. For API version 9 and earlier versions, the total number of reminders cannot exceed 2,000.

**Solution**

Delete unnecessary reminders.
<!--RP1End-->
## 1700003 Nonexistent Reminder

**Error Message**

The reminder does not exist.

**Description**

The reminder passed in **cancelReminder()** does not exist.

**Possible Causes**

1. The reminder has expired.
2. The reminder has been deleted.

**Solution**

1. Check whether the reminder is valid.
2. Check whether the reminder has been deleted.

## 1700004 Nonexistent Bundle Name

**Error Message**

The bundle name does not exist.

**Description**

The bundle name passed is not found.

**Possible Causes**

1. The bundle name is incorrect.
2. The application is not installed.

**Solution**

Check whether the bundle name exists.

## 1700007 Invalid Parameter

**Error Message**

If the input parameter is not valid parameter.

**Description**

The input parameter is invalid.

**Possible Causes**

The parameter does not comply with the rules.

**Solution**

Make sure all the mandatory parameters are passed in and the parameter types are valid. If parameter verification fails, read the parameter specifications and locate the fault based on the possible causes.
