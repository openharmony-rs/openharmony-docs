# Widget Error Codes
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=465fb4d57a1447327363d6485241bf8b06b62dc9 translatedAt=2026-11-04T04:24:40.272Z pushedAt=2026-11-04T10:12:50.110Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 16500050 IPC Failure

**Error Message**

IPC connection error.

**Description**

An error occurs when the system initiates inter-process communications (IPC) to complete the request.

**Possible Causes**

The parameter value passed in the API is too large, causing IPC data verification failure.

**Solution**

Pass appropriate parameter values.

## 16500060 Service Connection Failure

**Error Message**

Service connection error.

**Description**

An error occurs when the system attempts to connect to a service to complete the request.

**Possible Causes**

1. The widget is in the initialization state.
2. The system is busy.

**Solution**

1. Reconnect to the service.
2. Restart the device.

## 16500100 Failed to Obtain Widget Configuration Information

**Error Message**

Failed to obtain configuration information.

**Description**

An error occurs when the system attempts to obtain widget configuration information to complete the request.

**Possible Causes**

The widget configuration information field is missing or invalid.

**Solution**

Use the correct configuration information.

## 16501000 Internal Function Error

**Error Message**

An internal functional error occurred.

**Description**

An internal error occurs when the system executes the request.

**Possible Causes**

An internal service execution exception occurs.

**Solution**

Try again after the system is restarted.

## 16501001 Widget ID Not Exist

**Error Message**

The ID of the form to be operated does not exist.

**Description**

The specified widget in the request is not found.

**Possible Causes**

The widget ID passed in the API does not exist or is invalid.

**Solution**

Use a valid widget ID.

## 16501002 Too Many Widgets

**Error Message**

The number of forms exceeds the maximum allowed.

**Description**

The application attempts to add more widgets when the number of widgets has reached the upper limit.

**Possible Causes**

The number of widgets has reached the upper limit.

**Solution**

Delete unnecessary widgets and then add the required widgets.

## 16501003 Widget Not Operatable

**Error Message**

The form cannot be operated by the current application.

**Description**

The application cannot perform operations on a widget.

**Possible Causes**

The widget does not belong to the application.

**Solution**

<!--Del-->
1. Upgrade the application permission to **SystemApp**.
2. <!--DelEnd-->Check whether the widget ID belongs to the application.

## 16501006 Failed to Connect to the Widget Rendering Service

**Error Message**

FormRenderService is stopped. Connect to the service again.

**Description**

This error code is reported when the widget rendering service fails to be connected.

**Possible Causes**

The service is busy.

**Solution**

Try again later.

## 16501007 Untrusted Widget

**Error Message**

Form is not trust.

**Description**

The widget is not trusted.

**Possible Causes**

The widget code has problems such as infinite loop and memory leakage, causing system exceptions.

**Solution**

Check whether the widget code has an infinite loop or memory leakage.

<!--Del-->
## 16501008 Adding a Widget to the Home Screen Times Out

**Error Message**

Waiting for the form addition to the desktop timed out.

**Description**

A request for adding a widget to the home screen is sent, but the widget is not added within the specified duration.

**Possible Causes**

The service is busy.

**Solution**

Try again later.
<!--DelEnd-->

## 16501010 Failed to Set the Background Image of the Interactive Widget

**Error Message**

Failed to set the live form background image.

**Description**

This error code is reported when the background image resource is invalid.

**Possible Causes**

The background image resource is invalid.

**Solution**

Check whether the background image resource is valid.

## 16501011 API Not Supported

**Error Message**

The form can not support this operation.

**Description**

This error code is reported when the widget does not support the current API.

**Possible Causes**

The interactive widget animation is requested by a common widget, or the current interactive widget is incorrectly configured.

**Solution**

Ensure that the configured [sceneAnimationParams](../../form/arkts-ui-widget-configuration.md#sceneanimationparams-field) of the current widget is correct.

## 16501012 Incorrect Widget Dimension

**Error Message**

The form host uses an incorrect dimension.

**Description**

This error code is reported when the widget dimension is incorrect.

**Possible Causes**

The specified widget dimension is not configured, or the transferred widget dimension is invalid.

**Solution**

Check whether the input widget dimension is in the [FormDimension](js-apis-app-form-formInfo.md#formdimension) and [supportDimensions](../../form/arkts-ui-widget-configuration.md#fields-in-configuration-file) configuration list.

## 16501013 Operation Not Supported

**Error Message**

The system does not support the current operation.

**Description**

The system does not support the current operation.

**Possible Causes**

Failed to register the callback for listening for template widget information.

**Solution**

Restart the device to allow the system to re-register the callback for listening for template widget information.

## 16501014 Semi-modal Widget Editing Page Not in Foreground

**Error Message**

The form edit page is not in the foreground. The current operation is not supported.

**Description**

The semi-modal widget editing page is not in the foreground. The current operation is not supported.

**Possible Causes**

The semi-modal widget editing page is not opened.

**Solution**

Ensure that the [semi-modal widget editing page](../../form/arkts-ui-widget-event-formeditextensionability.md#semi-modal-widget-editing) is opened.

## 16501015 Failed to Close Semi-Modal Widget Editing Page of Another Application

**Error Message**

Cannot close the widget editing page opened by other apps.

**Description**

The semi-modal widget editing page of another application cannot be closed.

**Possible Causes**

The opened semi-modal widget editing page does not belong to the application that requests to close the page.

**Solution**

Ensure that the opened semi-modal widget editing page belongs to the application that requests to close the page.

## 16501016 Invalid Widget Location Information

**Error Message**

The location of the widget is invalid.

**Description**

The widget location information is invalid.

**Possible Causes**

The specified widget location information is out of the system-defined range.

**Solution**

Ensure that the input widget location is in the [FormLocation](js-apis-app-form-formInfo.md#formlocation20) list.

## 16501017 No Space to Publish the Card

**Error Message**

There is no space to publish the form.

**Description**

When publishing a card, the desktop has no space to accommodate the new card.

**Possible Causes**

1. The current page and the next page of the desktop have insufficient space, and the total number of desktop pages has reached the limit.
2. The number of cards on the desktop has reached the upper limit, and no more cards can be added.

**Solution**

Delete unnecessary cards and retry publishing.

## 16501018 Card Does Not Support Publishing

**Error Message**

This form does not support publishing.

**Description**

When publishing a card, the desktop does not allow the card to be published.

**Possible Causes**

The card does not support publishing on the desktop.

**Solution**

Check whether the card configuration meets the current scenario. For details, see the renderingMode field description in [Configuration File](../../form/arkts-ui-widget-configuration.md#fields-in-configuration-file) and the [relationship between supportdimensions fields and devices](../../form/arkts-ui-widget-configuration.md#supportdimensions-field-and-device-support-relationship-table).

## 16501019 Unable to Unregister a Form Service Not Registered by the Current Application
 
**Error Message**
 
A form service not owned by you cannot be unregistered.
 
**Description**
 
When unregistering a form consumer service, the form service being operated is not registered by the current application.
 
**Possible Causes**
 
The current application attempts to unregister a form consumer service that it did not register.
 
**Solution**
 
Unregister only the form consumer service registered by the current application.
 
## 16501020 Remote Card Service Unavailable
 
**Error Message**
 
Remote form service is unavailable.
 
**Description**
 
The remote form service is unavailable when distributing a card across devices.
 
**Possible Causes**
 
The remote device has not started the form service, or the form service is abnormal.
 
**Solution**
 
Check the form service status on the remote device. After confirming that the remote form service is available, re-initiate the cross-device card distribution request.
 
## 16501021 Remote Card Application Not Installed or Version Too Old
 
**Error Message**
 
The peer form application is not installed or the version is too old.
 
**Description**
 
When distributing a card across devices, the target card application on the remote device is not installed or its version is too old.
 
**Possible Causes**
 
1. The target card application is not installed on the remote device.
2. The version of the target card application on the remote device is too old and does not support cross-device card distribution.
 
**Solution**
 
Confirm that the target card application is installed on the remote device and that the application version supports cross-device distribution, and then initiate the cross-device card distribution request again.

## 2293761 Internal Service Error

**Error Message**

Some internal server error occurs.

**Description**

An internal error occurs when the system executes the current request.

**Possible Causes**

1. The system is busy.
2. The internal data of the system is abnormal currently.

**Solution**

1. Restart the system and try again.
2. If the restart still fails, submit an [online ticket](https://developer.huawei.com/consumer/en/support/feedback/#) to obtain help.

## 2293766 Requested Bundle Name Not Exist

**Error Message**

The requested bundle name does not exist.

**Description**

The requested bundle name does not exist. This is an internal error.

**Possible Causes**

An error occurs when the bundle management module obtains the bundle name of the requester. This is an internal service execution exception.

**Solution**

1. Restart the system and try again.
2. If the restart still fails, submit an [online ticket](https://developer.huawei.com/consumer/en/support/feedback/#) to obtain help.

## 2293767 Invalid Parameter

**Error Message**

Invalid params received on operating form.

**Description**

Invalid input parameters are passed when the API is called.

**Possible Causes**

1. Mandatory parameters are not transferred.
2. The parameter type is incorrect.
3. The number of parameters is incorrect.
4. The parameter value is empty. For example, an empty string ('') is passed.
5. Incorrect parameter format.
6. Invalid parameter value. The input parameters must be the same as those in [app.json5](../../quick-start/app-configuration-file.md) and [Configuring ArkTS Widget Configuration Files](../../form/arkts-ui-widget-configuration.md).

**Solution**

Check the possible causes to determine whether mandatory parameters are transferred and whether the transferred parameter types are correct.

## 2293795 Failed to Obtain the Bundle Manager Service

**Error Message**

Get bms rpc failed.

**Description**

Failed to obtain the Bundle Manager service.

**Possible Causes**

An internal service execution exception occurs.

**Solution**

1. Restart the system and try again.
2. If the restart still fails, submit an [online ticket](https://developer.huawei.com/consumer/en/support/feedback/#) to obtain help.

## 2293798 Failed to Obtain the Widget Manager Service

**Error Message**

Get fms rpc failed.

**Description**

Failed to obtain the Widget Manager service.

**Possible Causes**

An internal service execution exception occurs.

**Solution**

1. Restart the system and try again.
2. If the restart still fails, submit an [online ticket](https://developer.huawei.com/consumer/en/support/feedback/#) to obtain help.

## 2293802 Failed to Obtain the System Manager Service

**Error Message**

Get system manager service failed.

**Description**

Failed to obtain the System Manager service.

**Possible Causes**

An internal service execution exception occurs.

**Solution**

1. Restart the system and try again.
2. If the restart still fails, submit an [online ticket](https://developer.huawei.com/consumer/en/support/feedback/#) to obtain help.
