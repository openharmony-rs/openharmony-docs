# Onscreen Awareness Error Codes
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 34000001 Service Exception

**Error Message**

Service exception.

**Description**

This error code is reported if a service exception occurs when the **getPageContent** or **sendControlEvent** API of the **onScreen** module is called.

**Possible Causes**

The service status is abnormal.

**Solution**

1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.
2. If the operation fails for three consecutive times, stop the retry. You can obtain device logs for further analysis.

## 34000002 Unsupported Application or Page

**Error Message**

The application or page is not supported.

**Description**

This error code is reported if the application or page fails to call the **getPageContent** API of the **onScreen** module.

**Possible Causes**

The application or page does not support the API.

**Solution**

Switch to a supported application or page and try again.

## 34000003 Invalid Window ID

**Error Message**

The window id is invalid.

**Description**

This error code is reported if no window ID is found when the **getPageContent** API of the **onScreen** module is called.

**Possible Causes**

1. No window ID is passed in the split-screen scenario.
2. The window corresponding to the input window ID is not displayed on the screen or is in the floating state.

**Solution**

1. In the split-screen scenario, pass in the correct window ID.
2. Ensure that the window corresponding to the input window ID is displayed on the screen or is not in the floating state.

## 34000004 Page Not Ready

**Error Message**

The page is not ready.

**Description**

This error code is reported if the page is not ready when the **getPageContent **API of the **onScreen** module is called.

**Possible Causes**

The page is not ready.

**Solution**

Call the API after the page is ready.

## 34000005 Target Not Found

**Error Message**

The target is not found.

**Description**

This error code is reported if no target is found when the **sendControlEvent** API of the onScreen module is called.

**Possible Causes**

The input window ID, session ID, or hook ID is incorrect.

**Solution**

Pass in the correct window ID, session ID, or hook ID.

## 34000006 Request Timeout

**Error Message**

The request timed out.

**Description**

This error code is reported when the **getPageContent** API of the **onScreen** module times out.

**Possible Causes**

The API call times out.

**Solution**

1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.
2. If the operation fails for three consecutive times, stop the retry. You can obtain device logs for further analysis.
