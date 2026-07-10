# Event Error Codes
<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 1500001 Want Action Is Null

**Error Message**

The action field in the want parameter is null.

**Description**

This error code is reported when the **action** attribute in the **want** object is null for the event to send.

**Possible Causes**

The **action** attribute in the **want** object is null for the common event to send.

**Solution**

Make sure the **action** attribute in the **want** object is not null.

## 1500002 Failed to Send Common Events from a Sandbox Application

**Error Message**

A sandbox application cannot send common events.

**Description**

This error code is reported when a sandbox application fails to send a common event.

**Possible Causes**

Common events from a sandbox application are blocked.

**Solution**

Check whether the application that sends the common event is a sandbox application.

## 1500003 Common Event Sending Frequency Is Too High

**Error Message**

The common event sending frequency too high.

**Description**

The frequency at which the application sends common events exceeds the system limit.

**Possible Causes**

The number of events sent by the application within a short period of time exceeds the system limit, triggering frequency control.

**Solution**

Check whether the application sends common events too frequently. If so, reduce the event sending frequency or increase the sending interval and try again.

## 1500004 Failed to Send System Common Events

**Error Message**

A third-party application cannot send system common events.

**Description**

The third-party application fails to send system common events.

**Possible Causes**

The application is not a system application or system service.

**Solution**

Make sure the application to send system common events is a system application or system service.

## 1500005 Subscriber Not Found

**Error Message**

The subscriber is not found.

**Description**

This error code is reported when the subscriber cannot be found.

**Possible Causes**

The subscriber has canceled the subscription and is deleted by the system.

**Solution**

Check whether the subscription has already been canceled. If the subscription has been canceled, the subscriber is deleted.

## 1500006 Invalid User ID

**Error Message**

Invalid userId.

**Description**

This error code is reported when the user ID is invalid.

**Possible Causes**

The user ID is different from the system user ID, or the application is not a system application or system service.

**Solution**

1. Make sure the current user ID is the same as the system user ID.
2. Make sure the application is a system application or system service.

## 1500007 Failed to Send a Request Through IPC

**Error Message**

Failed to send the message to the common event service.

**Description**

This error code is reported when the attempt to send a request through IPC fails.

**Possible Causes**

IPC connections are frequently established within a short period of time, causing system resources to be insufficient. As a result, the connection object fails to be created.

**Solution**

Do not set up connections frequently. Try again later.

## 1500008 Failed to Initialize the Common Event Service

**Error Message**

Failed to initialize the common event service.

**Description**

An error occurs in the initialization process of the common event server.

**Possible Causes**

A service exception occurs when the server initializes data processing.

**Solution**

Try again later.

## 1500009 Failed to Obtain System Parameters

**Error Message**

Failed to obtain system parameters.

**Description**

This error code is reported when an exception occurs in the system during service processing, for example, when the current system time fails to be obtained.

**Possible Causes**

A system fault occurs.

**Solution**

Try again later.

## 1500010 The Number of Subscribers Exceeds the Upper Limit

**Error Message**

The count of subscriber exceed system specification.

**Description**

This error code is reported when the number of subscribers exceeds the upper limit.

**Possible Causes**

The subscriber is not unregistered when it is no longer used. A maximum of 200 subscribers can be subscribed to in each process of the common event. All services in a process share the number of subscribers.

**Solution**

Unregister the subscriber that is no longer used in the application. If the subscriber has been unregistered, try again later.
