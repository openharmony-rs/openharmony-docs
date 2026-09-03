# Input Method Framework Error Codes

<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c9f68a28229d3fb5da602baa0bfb8e542d407a50 translatedAt=2026-09-02T02:26:48.528Z pushedAt=2026-09-02T11:29:20.109Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 12800001 Bundle Manager Service Exception

**Error Message**

Bundle manager error.

**Description**

This error code is reported when the system fails to obtain information such as the input method application bundle name and version number by calling bundle management APIs.

**Possible Causes**

This error code is thrown when APIs such as **getInputMethods** and **listCurrentInputMethodSubtype** are called to obtain input methods and their subtypes, and an error occurs within the bundle manager service.

**Solution**

Check the bundle manager service status and ensure that the service is running properly.

## 12800002 Input Method Engine Error

**Error Message**

Input method engine error. Possible causes:

1. input method panel not created.

2. input method application does not subscribe to input method panel lifecycle events.

**Description**

This error code is reported when operations such as showing or hiding the keyboard fail because the input method panel is not created or the input method application does not subscribe to related events.

**Possible Causes**

1. The input method panel is not created.

2. The input method application does not subscribe to related events.

**Solution**

Check whether the input method application process is running normally. Tap the application dialog box to trigger the keyboard display. If the keyboard is displayed normally, the process is running normally.

## 12800003 Input Method Client Error

**Error Message**

Input method client error. Possible causes: 

1. the edit box is not focused.

2. no edit box is bound to current input method application.

3. ipc failed due to data transferred exceeding 1MB or invalid data format.

**Description**

This error code is reported when edit controls such as dialog boxes within applications (WeChat, Settings, Contacts, etc.) fail to show or hide the soft keyboard.

**Possible Causes**

1. The application is not focused.

2. The application client service is abnormal, causing the input method application to disconnect from the application client.

3. IPC fails because the data volume to transmit exceeds 1 MB or the data format is incorrect.

**Solution**

1. Attach the input method app to the app again: terminate the background process of the application, restart the application, and trigger the display of the input method keyboard. The issue is resolved if the keyboard is shown normally. To hide the keyboard, call the **hideTextInput** API which shall be used in pairs with **showTextInput**.

2. Switch the application to the foreground, ensure that it is not covered by other apps or windows, and trigger the keyboard to pop up.

3. According to the IPC constraints, adjust the volume of data to be transmitted to a smaller size before initiating the request. The total volume of data transmitted at the IPC layer in a single API call equals the volume of data sent by the application side plus the necessary data required for system-layer processing. Therefore, the maximum volume of data that an application can actually send when calling an API (about 1 MB) is smaller than the maximum volume of data limited by IPC itself (about 1.2 MB). Note: **showTextInput** and **hideTextInput** must be called in pairs to avoid resource leaks.

## 12800004 Not an Input Method

**Error Message**

Not an input method application.

**Description**

This error code is reported when an API exclusive to input methods is called by an application of another type.

**Possible Causes**

A non-input-method application called an API that is supported only by input method applications.

**Solution**

Call the API only in an input method.

## 12800005 Configuration Persistence Failure

**Error Message**

Configuration persistence error.

**Description**

This error code is reported when configuration persistence fails.

**Possible Causes**

When the API for switching input methods is called, input method configuration parameters are saved. An error is thrown if an exception occurs in the system parameter configuration module and causes the parameters to fail to be saved.

**Solution**

Run the command `hdc shell param get persist.sys.default_ime` to check the default input method parameter. If the parameter is displayed normally, the system parameter configuration module is working properly. It is recommended that you restart the device and retry the configuration persistence operation.

## 12800006 Input Method Controller Error

**Error Message**

Input method controller error. Possible cause: create InputMethodController object failed.

**Description**

This error code is reported when the input method controller fails to be obtained.

**Possible Causes**

This error code is thrown if an application encounters an exception when calling the **getController** API to obtain the **InputMethodController**.

**Solution**

None

## 12800007 Input Method Setter Error

**Error Message**

Input method setter error. Possible cause: create InputMethodSetting object failed.

**Description**

This error code is reported when the system fails to obtain the input method setter.

**Possible Causes**

This error code is thrown if an application encounters an exception when calling the **getSetting** API to obtain the **InputMethodSetting**.

**Solution**

None

## 12800008 Input Method Manager Service Error

**Error Message**

Input method manager service error. Possible cause: a system error, such as null pointer, IPC exception.

**Description**

This error code is reported when an API in the input method framework is called and an exception occurs in obtaining the service because it depends on the input method manager service.

**Possible Causes**

This error code is thrown when an application calls any API of the [input method framework](js-apis-inputmethod.md) and the required input method manager service cannot be found.

**Solution**

Run the command `ps -A | grep inputmethod` to check the process ID of the input method service. If the process exists, the service is running normally.

## 12800009 Input Method Client Detached

**Error Message**

Input method client detached.

**Description**

This error code is reported when the current application is not attached to an input method.

**Possible Causes**

This error code is thrown when the current app is not attached to an input method and operations such as **showTextInput** and **hideTextInput** are performed.

**Solution**

First call the [attach](js-apis-inputmethod.md#attach10) API to establish attachment, and then call APIs such as **showTextInput** to perform keyboard operations. The complete call process is: **attach** → **showTextInput** (shows the keyboard) → **hideTextInput** (hides the keyboard). **hideTextInput** and **showTextInput** must be used in pairs to release resources.

## 12800010 Not Preconfigured Default Input Method

**Error Message**

Not the preconfigured default input method.

**Description**

This error code is reported when the invoking application is not the preconfigured default input method.

**Possible Causes**

The API is called by an application other than the preconfigured default input method.

**Solution**

Use [getDefaultInputMethod](js-apis-inputmethod.md#inputmethodgetdefaultinputmethod11) to query the default input method of the system and determine whether the application uses the default input method. If the application does not use the default input method, this API cannot be called.

## 12800011 Text Preview Not Supported

**Error Message**

Text preview not supported.

**Description**

The current edit box does not support the text preview feature.

**Possible Causes**

Text preview of the edit box is not supported.

**Solution**

Use [getEditorAttributeSync](js-apis-inputmethodengine.md#geteditorattributesync10) to obtain the value of **isTextPreviewSupported** of [EditorAttribute](js-apis-inputmethodengine.md#editorattribute). If **isTextPreviewSupported** is **false**, this API cannot be called.

## 12800012 Soft Keyboard Panel Not Created

**Error Message**

The input method panel does not exist.

**Description**

The input method panel of the soft keyboard type is not created.

**Possible Causes**

The input method application has not created a soft keyboard panel.

**Solution**

Create the panel through the [createPanel](js-apis-inputmethodengine.md#createpanel10) API.

## 12800013 Window Manager Service Error

**Error Message**

Window manager service error.

**Description**

The window manager service is not running properly.

**Possible Causes**

After the API is called, the system uses the capabilities of the window manager service module. This error is thrown due to an error of the window manager service.

**Solution**

Restart the device and try again.

## 12800014 Non-Full Access Mode of the Input Method Application

**Error Message**

The input method is in basic mode.

**Description**

The input method application is in non-full access mode.

**Possible Causes**

This error code is thrown when an API that requires full access mode is called but the current input method is not in full access mode.

**Solution**

Enable the full access mode of the input method in **Settings**.

## 12800015 Message Receiver Unable to Receive Custom Communication Data

**Error Message**

The other side does not accept the request.

**Description**

The message receiver cannot receive custom communication data.

**Possible Causes**

This error is thrown if the message receiver does not register [MessageHandler](js-apis-inputmethodengine.md#messagehandler15) to receive data when you call the API for sending custom communication data.

**Solution**

The message receiver must first register a **MessageHandler** to receive custom communication data before calling **recvMessage** to receive messages. Calling sequence: first register a **MessageHandler** (to listen for data), and then call **recvMessage** (to receive data). The input method application side calls [recvMessage](js-apis-inputmethodengine.md#recvmessage15), and the input method client side calls [recvMessage](js-apis-inputmethod.md#recvmessage15). Calling **recvMessage** without registering **MessageHandler** will result in failure to receive data.

## 12800016 Input Method Client Not in Edit Mode

**Error Message**

Input method client is not editable.

**Description**

The input method client is not in edit mode.

**Possible Causes**

The input method client exits edit mode after being attached. For example, [hideTextInput](js-apis-inputmethod.md#hidetextinput10) is called after the self-drawn component is attached to the input method through `Attach`.

**Solution**

After the input method client is attached and exits edit mode, it needs to re-enter edit mode. The complete call process is: **attach** (to establish attachment) → **showTextInput** (to enter the edit mode) → **hideTextInput** (to exit the edit mode). For example, a self-drawn component needs to call [showTextInput](js-apis-inputmethod.md#showtextinput10) to re-enter the edit mode. Note: After **hideTextInput** is called, other editing operations cannot be called directly; **showTextInput** must be called first to re-enter the edit mode.

## 12800017 Invalid Panel Type or Panel Flag

**Error Message**

Invalid panel type or panel flag. Valid values are defined in PanelType and PanelFlag enums.

**Description**

Invalid panel type or panel flag.

**Possible Causes**

This error code is thrown when the input method panel type or panel flag is not supported for invocation, or when the invoked API does not accept the currently passed panel type or panel flag.

**Solution**

Read the API usage description and adjust the input method panel type or panel flag as required.

<!--Del-->

## 12800018 Input Method Not Found

**Error Message**

The input method is not found.

**Description**

The input method is not found in the list of input methods installed on the system.

**Possible Causes**

The input method is not installed.

**Solution**

Call the [getAllInputMethods](js-apis-inputmethod.md#getallinputmethods11) to query all installed input methods.

## 12800019 Unsupported Operation by Default Input Method

**Error Message**

Current operation cannot be applied to the preconfigured default input method.

**Description**

The preconfigured default input method does not support this operation.

**Possible Causes**

[enableInputMethod](js-apis-inputmethod-sys.md#enableinputmethod20) or [EnabledState](js-apis-inputmethod.md#enabledstate15) is called to set the enabled state of the preconfigured default input method in the system.

**Solution**

Call the [getDefaultInputMethod](js-apis-inputmethod.md#inputmethodgetdefaultinputmethod11) API to query the preconfigured default input method in the system, and check whether the input method in use is the default input method. If yes, no processing is performed.

<!--DelEnd-->

## 12800020 Immersive Effect Parameter Configuration Error

**Error Message**

Invalid immersive effect.

1. The gradient mode and the fluid light mode can only be used when the immersive mode is enabled.

2. The fluid light mode can only be used when the gradient mode is enabled.

3. When the gradient mode is not enabled, the gradient height can only be 0.

**Description**

1. Gradient mode and fluid light mode can be used only when the immersive mode is enabled.

2. The fluid light mode can be used only when the gradient mode is enabled.

3. If the gradient mode is disabled, the gradient height can only be 0 px.

**Possible Causes**

The input parameters do not meet the preceding requirements when the [setImmersiveEffect](js-apis-inputmethodengine.md#setimmersiveeffect20) API is called to set the [ImmersiveEffect](js-apis-inputmethodengine.md#immersiveeffect20).

**Solution**

1. First set the **immersiveEnabled** property of **ImmersiveEffect** to **true** to enable the immersive mode, and then set **gradientMode** to enable the gradient mode and **fluidLightMode** to enable the fluid light mode.

2. First set the **gradientMode** property to enable the gradient mode, and then set the **fluidLightMode** property to enable the fluid light mode.

3. When the gradient mode is not enabled (**gradientMode** is **false**), set the **gradientHeight** property to 0 px.

## 12800021 Incorrect Call Sequence

**Error Message**

This operation is allowed only after adjustPanelRect or resize is called.

**Description**

The **setImmersiveEffect** API can be called only after any of the following APIs is called:

  - [adjustPanelRect](js-apis-inputmethodengine.md#adjustpanelrect12) (available since API version 12)

  - [adjustPanelRect](js-apis-inputmethodengine.md#adjustpanelrect15) (available since API version 15)

  - [resize](js-apis-inputmethodengine.md#resize10) (available since API version 10)

**Possible Causes**

The [setImmersiveEffect](js-apis-inputmethodengine.md#setimmersiveeffect20) API can be called only after any of the following APIs is called:

  - [adjustPanelRect](js-apis-inputmethodengine.md#adjustpanelrect12) (available since API version 12)

  - [adjustPanelRect](js-apis-inputmethodengine.md#adjustpanelrect15) (available since API version 15)

  - [resize](js-apis-inputmethodengine.md#resize10) (available since API version 10)

**Solution**

The **setImmersiveEffect** API can be called only after any of the following APIs is called:

  - **adjustPanelRect** (available since API version 12 or 15)

  - **resize** (available since API version 10)

## 12800022 Invalid displayId

**Error Message**

Invalid displayId.

**Description**

**displayId** is invalid or does not exist.

**Possible Causes**

This error code is thrown when the **displayId** passed to the [getSystemPanelCurrentInsets](js-apis-inputmethodengine.md#getsystempanelcurrentinsets21) API is invalid and the API call fails.

**Solution**

Call the [getDisplayId](js-apis-inputmethodengine.md#getdisplayid15) API to obtain the ID of the current window.

<!--Del-->

## 12800023 Specified User Not Exist

**Error Message**

The specified user does not exist.

**Description**

The specified user does not exist.

**Possible Causes**

This error code is thrown when an API with the **userId** parameter is called but the user corresponding to the passed **userId** does not exist.

**Solution**

Verify the validity of the user ID through system user management APIs such as **getOsAccountLocalIdFromNumber**, or check whether the passed **userId** parameter is correct.

## 12800024 Specified User Not in the Foreground

**Error Message**

The specified user is not in the foreground.

**Description**

The specified user is not in the foreground.

**Possible Causes**

This error code is thrown when an API with the **userId** parameter is called but the user corresponding to the passed **userId** is not in the foreground.

**Solution**

Ensure that the target user is in the foreground before calling the related API.

## 12800025 Cross-User Operation Denied

**Error Message**

Cross-user operation denied. Only user 0 applications are authorized for this operation.

**Description**

Cross‑user operation denied. Only applications belonging to user 0 are granted permission to perform this operation.

**Possible Causes**

An application of a user other than user 0 attempts to access or operate on data or features of another user.

**Solution**

Ensure that only applications for user 0 call the APIs for such cross‑user operations.


## 12800026 Input Method System Panel Error

**Error Message**

Input method system panel error. Possible causes: 

1. system panel not connected.

2. ipc failed due to data transferred exceeding 1MB or invalid data format.

3. the caller is not system panel.

**Description**

An input method system panel operation failed. For example, an application may encounter an exception while invoking a system panel API.

**Possible Causes**

1. The system panel is not connected.

2. The IPC failed because the amount of data transferred exceeds 1 MB or the data format is incorrect.

3. The caller is not the system panel.

**Solution**

1. Ensure that the [connectSystemChannel](js-apis-inputmethod-system-panel-manager-sys.md#inputmethodsystempanelmanagerconnectsystemchannel) API has been called to connect the system channel.

2. Refer to [IPC constraints](../../ipc/ipc-rpc-overview.md#constraints). Reduce the amount of data to be transferred before initiating the request. Note that the total amount of data transferred at the IPC layer in a single API call consists of data sent by the application plus data required for system-layer processing. Therefore, the maximum amount of data that an application can actually send when calling an API is smaller than the IPC‑enforced maximum data limit.

3. Ensure that the caller is the system panel.

<!--DelEnd-->

