# HUKS Error Codes

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=23577c979bcb519c1999250f5076db4008505504 translatedAt=2026-10-12T08:40:52.022Z pushedAt=2026-10-13T06:55:17.707Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 12000001 Feature Not Supported

**Error Message**

The feature or capability is not supported.

**Description**

The currently called feature (capability) is not supported. The specific feature (capability) can be obtained from the printed errorMessage.

**Possible Causes**

1. The sub-feature is not supported.
2. The algorithm parameter is not supported.

**Solution**

1. Check **errorMessage** to identify the unsupported sub-feature, and avoid calling this feature in the current device environment. If it is necessary for your business, submit feedback on the official developer community.
2. Refer to the specific sections on capability introduction and algorithm specifications in [HUKS Development Guide](../../security/UniversalKeystoreKit/huks-overview.md), confirm the API specification to be called, adjust the API parameters, and use the supported algorithm parameters.

## 12000002 Missing Key Algorithm Parameter

**Error Message**

The algorithm param is missing.

**Description**

The algorithm parameter required for the key operation is missing.

**Possible Causes**

The parameters required for the current key operation, such as the key algorithm, key length, or padding algorithm, are not added.

**Solution**

1. Check **errorMessage** to identify the missing key parameter.
2. Refer to the specific sections on capability introduction and algorithm specifications in [HUKS Development Guide](../../security/UniversalKeystoreKit/huks-overview.md), confirm the API specification to be called, adjust the API parameters, and add the corresponding key parameters.

## 12000003 Invalid Key Algorithm Parameter

**Error Message**

The algorithm argument is invalid.

**Description**

Invalid key algorithm parameter.

**Possible Causes**

The related parameters are invalid when a key is used, for example, the algorithm does not match the padding algorithm, or the algorithm does not match the key operation.

**Solution**

1. Determine the invalid parameter from the error message.
2. Refer to the specific sections on capability introduction and algorithm specifications in [HUKS Development Guide](../../security/UniversalKeystoreKit/huks-overview.md), confirm the API specification to be called, adjust the API parameters, and change the corresponding key parameters to valid values.

## 12000004 File Error

**Error Message**

The file operation failed.

**Description**

Failed to operate the file.

**Possible Causes**

1. The disk is full.
2. Failed to obtain the file size.
3. The file cannot be operated. For details, see the returned errorMessage.

**Solution**

1. If the disk space is full, clear the disk space first.
2. Check the operation permission of the corresponding file. For details, see [File Directory Description](../../file-management/app-sandbox-directory.md#application-file-directory-and-application-file-path).
3. If there are other exceptions in the file system, submit feedback in the official developer community.

## 12000005 IPC Error

**Error Message**

IPC communication failed.

**Description**

IPC communication failed.

**Possible Causes**

1. Failed to obtain messages from the IPC.
2. An IPC error occurred. For details, see the returned errorMessage.

**Solution**

Locate and rectify the IPC failure.

## 12000006 Algorithm Library Operation Failed

**Error Message**

Crypto engine error or UKey driver error.

**Description**

The algorithm library operation or UKey driver operation fails.

**Possible Causes**

The possible causes are as follows:

1. The encryption and decryption on the algorithm library failed due to incorrect ciphertext data.
2. Incorrect key parameters exist.

**Solution**

1. Check and correct the ciphertext data.
2. Check and correct the key parameters.

## 12000007 Key Access Failure - Key Invalidated

**Error Message**

This credential is invalidated permanently.

**Description**

The current credential has expired permanently.

**Possible Causes**

The possible causes include the following:

1. The key is configured with the user access control attribute and becomes invalid after the password is cleared.
2. The key is configured with the user access control attribute and becomes invalid after a new biometric feature is enrolled.

**Solution**

1. Confirm the authentication failure mode recorded in the log.
2. If the authentication fails due to the configuration of the access control attribute, the key cannot be used any longer.

## 12000008 Key Access Failure - Key Authentication Failure

**Error Message**

The authentication token verification failed.

**Description**

The user token cannot pass the authentication.

**Possible Causes**

The challenge value is incorrect.

**Solution**

1. Check whether the challenge for user IAM authentication is correctly assembled.
2. If the challenge value is incorrect, modify the assembly mode, use the bytes generated by HUKS to assembly the challenge value, and pass it to user IAM for authentication.

## 12000009 Key Access Failure - Key Access Timeout

**Error Message**

This authentication token timed out.

**Description**

The token of the current user has timed out.

**Possible Causes**

The user authentication access control attribute is set for the key, and the authentication timeout interval (**timeout**) is specified. However, the user authentication is not completed within the **timeout** period after the key **init** operation. As a result, the authentication token expires, and the current key session becomes invalid.

**Solution**

Initialize the key and perform the authentication again. Ensure that the difference between the current time and the authentication token generation time is less than the timeout interval.

## 12000010 Key Operation Sessions Reaches the Limit

**Error Message**

The number of key operation sessions has reached the limit.

**Description**

The number of key operation sessions has reached the limit.

**Possible Causes**

The number of HUKS key operation sessions has reached the upper limit (15), and no more call requests from the same application or across applications can be processed.

**Solution**

1. Check whether there are multiple key session operations (**init** operations) for the same application. If yes, modify the code to avoid concurrent invoking.
2. If the key operation sessions are set up for different applications, wait until the sessions are released.

## 12000011 The Entity Does Not Exist

**Error Message**

Queried entity does not exist.

**Description**

The target object does not exist.

**Possible Causes**

The key corresponding to the key alias does not exist.

**Solution**

1. Check whether the key alias is correctly spelled.
2. Check whether the key corresponding to the key alias is successfully generated.

## 12000012 External Error

**Error Message**

Device environment or input parameter abnormal.

**Description**

The device environment or input parameters are abnormal.

**Possible Causes**

<!--RP1-->
The external hardware, file, or input parameter is abnormal.
 <!--RP1End-->

**Solution**

<!--RP2-->
1. Check whether the input parameters are valid and whether the parameter types and value ranges meet the requirements.
2. Check whether the device environment is normal and whether the hardware and system status are normal.
3. If no error is found, submit the error code and logs to the community for help.
<!--RP2End-->

## 12000013 The Credential Does Not Exist

**Error Message**

The credential does not exist.

**Description**

The current credential does not exist.

**Possible Causes**

The credential, such as the PIN, fingerprint, or face image, is not enrolled.

**Solution**

Enroll the credential or change the authentication type bound to the key.

## 12000014 Insufficient Memory

**Error Message**

A file error can be any of the following:

- Insufficient memory.
- Malloc failed.

**Description**

A file error can be any of the following:

- The memory is insufficient.
- Failed to allocate memory.

**Possible Causes**

The system memory is insufficient, or the buffer allocated for the output parameter is too small.

**Solution**

1. Release memory or restart the device.
2. Check whether the buffer allocated for the output parameter is too small.

## 12000015 Failed to Invoke Other System Services

**Error Message**

Failed to obtain the information via UserIAM.

**Description**

Failed to obtain authentication-related information via UserIAM.

**Possible Causes**

The called system service has not started.

**Solution**

Wait for the system service to start and call the API again.

## 12000016 Device Password Not Set

**Error Message**

A device password is required but not set.

**Description**

The device password is not set.

**Possible Causes**

The key is configured with the user access authentication attribute that depends on the device password, but the device password is not configured, so the key cannot be operated.

**Solution**

Set the device password first, and then perform the key operation.

## 12000017 Duplicate Key Alias

**Error Message**

The key with the same alias already exists.

**Description**

A key with the same name already exists.

**Possible Causes**

The same key alias already exists and cannot be overwritten.

**Solution**

Check whether the same key alias needs to be overwritten as needed.

## 12000018 Invalid Input Parameter

**Error Message**

The input parameter is invalid.

**Description**

The input parameter is invalid.

**Possible Causes**

1. A mandatory parameter is not passed.

2. A parameter type is incorrect (Type Error).

3. A null parameter is incorrect (Null Argument Error).

4. A value range is incorrect (Value Range Error).

**Solution**

Make sure all the mandatory parameters are passed in and the types of the passed-in parameter are valid. If parameter verification fails, read the parameter specifications and locate the fault based on the possible causes.

## 12000019 Provider Name Already Registered

**Error Message**

The provider is already registered.

**Description**

The provider to be registered already exists.

**Possible Causes**

The provider with the same name is registered repeatedly, or the previously registered provider is not unregistered.

**Solution**

Check whether the provider to be registered is correct. If the provider is correct, unregister the provider and register it again.

## 12000020 Dependent Module Error

**Error Message**

The provider operation failed.

**Description**

The downstream dependent module reports an error.

**Possible Causes**

The downstream dependent module reports an error.

**Solution**

Check the cause of the error reported by the downstream module based on the error code or error message returned.

## 12000021 UKey PIN Locked

**Error Message**

The UKey PIN is locked.

**Description**

The UKey PIN is locked.

**Possible Causes**

The PIN is locked due to too many incorrect PIN attempts.

**Solution**

Contact the bank to unlock the UKey.

## 12000022 Incorrect UKey PIN

**Error Message**

The UKey PIN is incorrect.

**Description**

The UKey PIN is incorrect.

**Possible Causes**

The PIN is incorrect.

**Solution**

Enter the correct PIN.

## 12000023 Unauthenticated UKey PIN

**Error Message**

The UKey PIN is not authenticated.

**Description**

The UKey PIN is not authenticated.

**Possible Causes**

PIN authentication is required for the operation, but the PIN has not been authenticated.

**Solution**

Authenticate the UKey PIN and then perform the operation that requires authentication.

## 12000024 Device or Resource Busy

**Error Message**

The provider or UKey is busy.

**Description**

The device or resource is busy.

**Possible Causes**

The device or resource is busy.

**Solution**

Try again, or remove and insert the UKey and try again.

## 12000025 Resource Limit Exceeded

**Error Message**

The resource exceeds the limit.

**Description**

The resource limit is exceeded.

**Possible Causes**

The resource limit is exceeded.

**Solution**

Check whether there are unreleased resources. If yes, release the resources and try again.

## 12000026 Secure Element Fault

**Error Message**

the secure element is not available.

**Description**

The secure element is faulty.

**Possible Causes**

The secure element is faulty.

**Solution**

1. Try again later or restart the device and try again.
2. If the fault persists, submit the error code and logs to the community.

## 12000027 Network Unavailable

**Error Message**

The Internet is unavailable.

**Description**

The network is unavailable.

**Possible Causes**

The device network connection is unavailable.

**Solution**

1. Check whether the device network connection is normal.
2. Retry after the network connection is restored.

<!--RP3--><!--RP3End-->