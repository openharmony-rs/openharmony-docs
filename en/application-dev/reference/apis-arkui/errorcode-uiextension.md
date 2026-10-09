# UIExtension Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e2e8608c64e606248f00eb66f3b2d4805fae44da translatedAt=2026-08-29T09:28:17.651Z pushedAt=2026-08-31T07:52:52.769Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 1011 UIExtension Ability Startup Failure

**Error Message**

Failed to start the UIExtension ability.

**Description**

This error code is reported when the UIExtension ability fails to be started.

**Possible Causes**

1. The configuration of the **Want** parameter is incorrect.
2. There is a type mismatch. For details, see the [API](arkui-ts/ts-container-embedded-component.md#apis) of the **EmbeddedComponent** component.
3. The provider application is not installed.

**Solution**

Verify the configuration of the **Want** parameter and the types, and ensure the application is installed.

## 1012 Failure to Switch the UIExtension Ability to the Background

**Error Message**

Failed to switch the UIExtension ability to the background.

**Description**

This error code is reported when the UIExtension ability fails to be moved to the background.

**Possible Causes**

The UIExtension ability fails to be switched to the background. Possible causes include but are not limited to:

1. The ability lifecycle state is abnormal.

2. The system resources are insufficient. If the cause still cannot be identified, perform analysis based on Ability Manager Service (AMS) logs.

**Solution**

Perform analysis based on Ability Manager Service (AMS) logs.

## 1013 UIExtension Ability Fails to Be Destroyed

**Error Message**

Failed to destroy the UIExtension ability.

**Description**

This error code is reported when the UIExtension ability fails to be destroyed.

**Possible Causes**

The UIExtension ability fails to be destroyed. Possible causes include but are not limited to:

1. The ability lifecycle callback is executed abnormally.

2. An error occurs during resource release. If the cause still cannot be identified, perform analysis based on Ability Manager Service (AMS) logs.

**Solution**

Perform analysis based on Ability Manager Service (AMS) logs.

## 100011 No Synchronous Callback Registered

**Error Message**

No callback has been registered to respond to this request.

**Description**

This error code is reported when the UIExtension ability has not registered a synchronous callback.

**Possible Causes**

The component using the ability calls the **sendSync** API to send data to the launched ability before the ability registers a synchronous callback listener.

**Solution**

1. Register a synchronous callback listener in the UIExtension ability.
2. The component user needs to call the **sendSync** API to send data to the started ability.

## 100012 Data Transfer Failure

**Error Message**

Transferring data failed.

**Description**

This error code is reported when the data transfer fails.

**Possible Causes**

The data transfer fails. Possible causes include but are not limited to:

1. The amount of data sent exceeds the limit.

2. The data serialization fails.

3. The cross-process communication channel is abnormal. If the cause still cannot be identified, perform analysis based on Ability Manager Service (AMS) logs.

**Solution**

Perform analysis based on Ability Manager Service (AMS) logs.

## 100013 Nesting Not Allowed

**Error Message**

Cascading UIExtension components is not allowed.

**Description**

This error code is reported when nesting between UIExtension components may occur unexpectedly in specific page layouts or component reuse scenarios (the nesting is not allowed).

**Possible Causes**

There might be nesting between UIExtension components.

**Solution**

Check the UIExtension component specifications to avoid unexpected nesting in scenarios such as component reuse, conditional rendering, and dynamic loading.

## 100014 Ability Exit Error

**Error Message**

The UIExtension ability exited unexpectedly.

**Description**

This error code is reported when the UIExtension ability exits abnormally.

**Possible Causes**

The UIExtension ability exits abnormally. Possible causes include but are not limited to:

1. An exception occurs when the ability lifecycle callback is executed.

2. An uncaught exception occurs during resource release. If the cause still cannot be identified, perform analysis based on Ability Manager Service (AMS) logs.

**Solution**

Perform analysis based on Ability Manager Service (AMS) logs.

## 100015 Lifecycle Timeout

**Error Message**

The lifecycle of the UIExtension ability has timed out.

**Description**

This error code is reported when the lifecycle of the UIExtension ability times out.

**Possible Causes**

The extended ability lifecycle times out. Possible causes include but are not limited to:

1. A time-consuming operation is performed in the lifecycle callback.

2. The main thread is blocked, preventing the lifecycle callback from being executed in time. If the cause still cannot be identified, perform analysis based on Ability Manager Service (AMS) logs.

**Solution**

Perform analysis based on Ability Manager Service (AMS) logs.

## 100016 Key Event Processing Timeout

**Error Message**

Key event processing by the UIExtension ability has timed out.

**Description**

This error code is reported when the UIExtension ability takes too long to process a key event.

**Possible Causes**

The UIExtension ability takes too long to process a key event. Possible causes include but are not limited to:

1. A time-consuming operation is performed in the Key event processing callback.

2. The main thread is blocked, preventing event handling from being completed in time. If the cause still cannot be identified, perform analysis based on Ability Manager Service (AMS) logs.

**Solution**

Perform analysis based on Ability Manager Service (AMS) logs.

## 100018 UIExtension Ability Startup Failure

**Error Message**

Failed to start the UIExtension ability. Check the Want of the UIExtensionAbility.

**Description**

This error code is reported when the UIExtension ability fails to start in a scenario where the **onTerminated** callback is set.

**Possible Causes**

1. The configuration of the **Want** parameter is incorrect.
2. The type is inconsistent. For details, see the [API](arkui-ts/ts-container-embedded-component.md#apis) of **EmbeddedComponent**.
3. The provider application is not installed.
4. The device type is not supported.

**Solution**

Check the **Want** parameter configuration. Make sure the application is installed, and the current device supports the required features.

## 100019 Failed to Switch the UIExtension Ability to the Background

**Error Message**

background ui extension ability failed, please check AMS log.

**Description**

This error code is reported when the UIExtension ability fails to be switched to the background in a scenario where the **onTerminated** callback is set.

**Possible Causes**

The UIExtension ability fails to be switched to the background. Analyze the issue based on the Ability Manager Service (AMS) logs.

**Solution**

Analyze the issue based on the Ability Manager Service (AMS) logs.

## 100020 Failed to Destroy the UIExtension Ability (with the onTerminated Callback)

**Error Message**

terminate ui extension ability failed, please check AMS log.

**Description**

This error code is reported when the UIExtension ability fails to be destroyed in a scenario where the **onTerminated** callback is set.

**Possible Causes**

The UIExtension ability fails to be destroyed. Analyze the issue based on the Ability Manager Service (AMS) logs.

**Solution**

Analyze the issue based on the Ability Manager Service (AMS) logs.

## 100021 Transparent Node Detected

**Error Message**

Transparent node is detected in the UIExtension ability.

**Description**

This error code is reported when a transparent node is detected in the UIExtension ability.

**Possible Causes**

A transparent node is detected in the UIExtension Ability, which may block event distribution.

**Solution**

Remove the transparent node or adjust the component transparency setting to avoid blocking events.