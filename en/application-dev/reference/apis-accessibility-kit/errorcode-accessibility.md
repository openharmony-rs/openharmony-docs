# Accessibility Error Codes

<!--Kit: Accessibility Kit-->
<!--Subsystem: BarrierFree-->
<!--Owner: @qiiiiiiian-->
<!--Designer: @z7o-->
<!--Tester: @A_qqq-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=9d26bd1999a89e67cfecfa777535add71144c96b translatedAt=2026-08-03T09:34:23.253Z pushedAt=2026-08-03T12:18:09.104Z -->

> **NOTE**
>
> The following describes only the error codes specific to this module. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 9300000 Accessibility System Service Abnormal

**Error Message**

System abnormality.

**Error Description**

The method returns this error code when the accessibility system service is abnormal.

**Possible Causes**

This error code indicates an abnormal accessibility system service. Possible causes are as follows:

1. Internal operation failed.

2. Failed to obtain the required service or client object (null pointer).

3. IPC communication failed.

4. Failed to obtain the accessibility service proxy.

5. Timed out while waiting for the result of an asynchronous operation.

6. The listener or observer has already been registered.

7. The listener or observer is not registered.

8. The client is not connected.

9. The target application failed to connect to the accessibility service.

10. The element information received from ACE is invalid.

11. Failed to perform an action in ACE.

12. Failed to inject a gesture event.

**Processing Steps**

1. Wait for a while and call the method again.

2. If this error code is still reported after a retry, restart the accessibility extension app.

3. If the error persists, restart the device.

<!--Del-->

## 9300001 Invalid Bundle Name or Ability Name

**Error Message**

Invalid bundle name or ability name.

**Error Description**

This error code is returned when the input bundle name or ability name is invalid.

**Possible Causes**

This error code indicates an invalid bundle name or ability name. The possible causes are as follows:

1. The bundle name does not exist.

2. The bundle does not contain the corresponding ability.

**Processing Steps**

1. Check whether the bundle name is correct.

2. Check whether the Ability corresponding to the package name is correct.

## 9300002 Target Ability Already Enabled

**Error Message**

Target ability already enabled.

**Error Description**

The method returns this error code when the target ability is already enabled.

**Possible Causes**

This error code indicates that the target Ability is already enabled and cannot be enabled again.

**Processing Steps**

1. Stop the target Ability.

2. Enable the target Ability again.

<!--DelEnd-->

## 9300003 No Accessibility Permission to Perform the Operation

**Error Message**

No accessibility permission to perform the operation.

**Error Description**

This error code is returned when an app performs an unauthorized accessibility operation, that is, an operation not enabled by the user when enabling the accessibility extension app.

**Possible Causes**

This error code indicates that the app does not have the accessibility permission for this operation. The possible cause is that the app performed an accessibility feature operation that the user did not enable when enabling the accessibility extension app.

**Processing Steps**

1. Try to prompt the user about the necessity of performing the accessibility feature operation and obtain user authorization. After authorization is complete, the app will have the permission to perform this accessibility feature operation.

2. Re-enable the accessibility extension app and enable the required accessibility feature operation. After completion, the accessibility feature operation can be performed normally without reporting this error code again.

## 9300004 Attribute Does Not Exist

**Error Message**

This property does not exist.

**Error Description**

This error code is returned when an attribute that does not exist in the accessibility node element is input.

**Possible Causes**

This error code indicates that an invalid attribute of an accessibility node element is input, meaning the attribute does not exist in the accessibility node element.

**Processing Steps**

1. Check whether the attribute exists in the accessibility node element.

2. If not, use an attribute that already exists in the node element.

## 9300005 Operation Not Supported

**Error Message**

This action is not supported.

**Error Description**

When an app performs an operation that is not supported by the accessibility node element, the method returns this error code.

**Possible Causes**

This error code indicates that an operation not supported by the accessibility node element is performed.

**Processing Steps**

1. Check whether the operation is included in the list of operations supported by the accessibility node element.

2. If not, use an operation supported by the node element.

<!--Del-->

## 9300006 Failed to Connect the Target App and Accessibility Service

**Error Message**

The connection between the target application and accessibility services failed.

**Error Description**

This error code is returned when the connection handle between the target app and accessibility service does not exist.

**Possible Causes**

The target app has not completed registration connection with the accessibility service.

**Processing Steps**

The target app has not completed registration connection. Try calling this method later.

## 9300007 Magnification Trigger Failed

**Error Message**

Trigger magnification failed.

**Error Description**

This error code is returned when the magnification function fails to trigger.

**Possible Causes**

1. The magnification gesture function is not enabled.

2. The magnification mode is not configured.

**Processing Steps**

1. Enable the magnification gesture function.

2. Configure the magnification mode. After the configuration is complete, trigger the magnification function again to execute it successfully.

<!--DelEnd-->

## 9300008 App Clone Index Invalid

**Error Message**

The appIndex is invalid. Possible causes: 1. The appIndex is out of the valid range. 2. The application corresponding to the appIndex does not exist.

**Error Description**

This error code is returned when the input app clone index (that is, the index of multiple running instances of the same app) is invalid.

**Possible Causes**

This error code indicates that the app clone index is invalid. Possible causes are as follows:

1. The app clone index is out of the valid range. It must be an integer greater than or equal to 0.

2. The app corresponding to this index does not exist.

**Processing Steps**

Check whether the app clone index value is valid.