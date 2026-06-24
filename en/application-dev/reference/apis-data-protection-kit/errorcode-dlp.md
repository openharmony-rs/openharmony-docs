# DLP Service Error Codes

<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=907dbe833940a2647e3ff7ec970329a62449fd1c translatedAt=2026-06-23T11:53:09.209Z pushedAt=2026-06-24T02:59:01.572Z -->

> **NOTE**
> 
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 19100001 Invalid Parameter

**Error Message**

Invalid parameter value.

**Description**

Invalid parameters are specified.

**Possible Causes**

1. The account is empty or exceeds 1024 characters.

2. The account type is incorrect.

3. The **aesKey** or **iv** is invalid.

4. The system time is later than the authorization expiration time.

5. The file descriptor (FD) is less than 0.

6. The value of **tokenId** is **0**.

7. The bundle name is empty.

8. The value of **appIndex** is less than **0**.

9. The value of **userId** is less than **0**.

**Solution**

Check and pass in parameters that meet the requirements, including the account length, type, **aesKey**, IV format, relationship between system time and authorization time, FD, **tokenId**, package name, **appIndex**, and **userId**.

## 19100002 Encryption and Decryption Error

**Error Message**

Credential service busy due to too many tasks or duplicate tasks.

**Description**

The encryption and decryption service is busy.

**Possible Causes**

1. The number of active encryption and decryption tasks is greater than 100.

2. Duplicate encryption/decryption tasks are performed.

**Solution**

Wait for a while and try again. Control the number of concurrent tasks to no more than 100 to prevent such errors.

## 19100003 Encryption/Decryption Timeout

**Error Message**

Credential task time out.

**Description**

The encryption and decryption operation for a Data Loss Prevention (DLP) file is not completed within the specified time, causing the operation to time out and fail.

**Possible Causes**

It takes more than 10 seconds to encrypt or decrypt a DLP file.

**Solution**

Try again later.

## 19100004 Credential Service Error

**Error Message**

Credential service error.

**Description**

An internal error occurs in the DLP credential service, and the credential service cannot be provided normally.

**Possible Causes**

1. The DLP credential service does not exist.

2. The DLP credential service is abnormal.

**Solution**

Wait for a while and try again, or restart the device.

## 19100005 Credential Authentication Server Error

**Error Message**

Credential authentication server error.

**Description**

An error occurs when communicating with the credential authentication server, and the credential authentication process cannot be completed.

**Possible Causes**

1. The credential authentication server cannot be connected.

2. The credential authentication server does not exist.

**Solution**

Check the credential authentication server and try again.

## 19100006 Access Denied for a Non-DLP Sandbox Application

**Error Message**

No permission to call this API, which is available only for DLP sandbox applications.

**Description**

The caller is not a DLP sandbox application.

**Possible Causes**

The caller is not a DLP sandbox application.

**Solution**

Check whether the application is a DLP sandbox application. The API is available only to DLP sandbox applications.

## 19100007 Access Denied for a DLP Sandbox Application

**Error Message**

No permission to call this API, which is available only for non-DLP sandbox applications.

**Description**

The caller cannot be a DLP sandbox application.

**Possible Causes**

The caller is a DLP sandbox application.

**Solution**

Confirm the application is not a DLP sandbox application. The API is not available to DLP sandbox applications.

## 19100008 Non-DLP File

**Error Message**

The file is not a DLP file.

**Description**

The file is not a DLP file.

**Possible Causes**

An operation for DLP files is performed on a non-DLP file.

**Solution**

Use a DLP file.

## 19100009 Failed to Operate the DLP File

**Error Message**

Failed to operate the DLP file.

**Description**

The operation on the DLP file fails.

**Possible Causes**

1. The user is not an authorized user.

2. The sandbox application fails to be installed.

3. The link file is not associated.

4. More than 1000 DLP files are opened simultaneously.

**Solution**

1. Check the access permission.

2. Wait for a while or restart the device and try again. Ensure that the number of DLP files opened simultaneously does not exceed 1000.

<!--Del-->

## 19100010 Read-Only DLP File

**Error Message**

The DLP file is read only.

**Description**

The DLP file is set to read-only mode. Data cannot be written, and permissions cannot be modified.

**Possible Causes**

1. You cannot modify the permission on a DLP file, which is read-only.

2. You cannot write a DLP file, which is read-only.

**Solution**

This DLP file is a read-only file. Do not attempt to modify its permissions or write data to it.
<!--DelEnd-->

## 19100011 System Service Abnormal

**Error Message**

The system ability works abnormally.

**Description**

DLP-related system services cannot run normally, causing related functions to be unavailable.

**Possible Causes**

1. The DLP permission service fails to start.

2. The remote procedure call (RPC) object of the DLP permission service cannot be obtained.

3. The service, on which the DLP permission service depends, fails to start.

4. The inter-process communication (IPC) data fails to be read or written.

5. The service is not initialized.

**Solution**

Try again later or restart the device.

## 19100012 Failed to Apply for Memory

**Error Message**

System memory is insufficient.

**Description**

The system memory is insufficient, and the memory resources required for the DLP operation cannot be requested.

**Possible Causes**

The system memory is insufficient.

**Solution**

The system memory is insufficient. Try again later or restart the device.

## 19100013 User Access Denied

**Error Message**

The user does not have the permission.

**Description**

The currently login user does not have the permission to perform this operation or access this DLP file.

**Possible Causes**

The current login account does not have the permission on the file.

**Solution**

Check whether the currently login account has the access permission for this file.

## 19100014 Account Not Logged In

**Error Message**

Account not logged in.

**Description**

The user needs to log in to the account before performing this operation. The current account is not logged in or the login status has expired.

**Possible Causes**

You have not logged in with the account of the corresponding type.

**Solution**

Log in using your account.

<!--Del-->

## 19100015 Upgrade Required

**Error Message**

The system needs to be upgraded.

**Description**

The current system version does not support this DLP function. The system needs to be upgraded to a version supporting this function.

**Possible Causes**

The current system version needs to be upgraded.

**Solution**

Upgrade the system.
<!--DelEnd-->

## 19100016 URI Missing in Want

**Error Message**

The uri field is missing in the want parameter.

**Description**

The **URI** field is missing in the **Want** parameter when the API is called.

**Possible Causes**

The **URI** field is not included in the **Want** parameter when the API for DLP file operations is called. The **Want** parameter is used to specify the operation target and parameter configuration, and the **URI** field is mandatory.

**Solution**

Set parameters correctly.

## 19100017 displayName Missing in Want

**Error Message**

The displayName field is missing in the want parameter.

**Description**

The **displayName** field is missing in the **Want** parameter when the API is called.

**Possible Causes**

The **displayName** field is not included in the **Want** parameter when the API for DLP file operations is called. The **displayName** field is mandatory in DLP file operations.

**Solution**

Set parameters correctly.

## 19100018 Application Unauthorized

**Error Message**

The application is not authorized.

**Description**

The application is not in the authorized application list for DLP files and has no permission to access or operate on DLP files.

**Possible Causes**

The application is not in the authorized application list.

**Solution**

Request to include the application in the authorized application list.<!--RP1--><!--RP1End-->

<!--Del-->

## 19100019 DLP File Has Expired

**Error Message**

The DLP file has expired.

**Description**

The DLP file has expired. Access to and operations on the file content cannot be continued.

**Possible Causes**

The current time is beyond the authorization period.

**Solution**

Contact the file owner to authorize the file.
<!--DelEnd-->

<!--Del-->

## 19100020 Network Disconnected

**Error Message**

No network connection.

**Description**

The network connection is required to perform this operation. The device is not connected to the network or the network is not authenticated.

**Possible Causes**

The network is disconnected or not authenticated.

**Solution**

Connect the device to Wi-Fi.
<!--DelEnd-->

## 19100021 Failed to Set Enterprise Application Policy

**Error Message**

Failed to set the enterprise policy.

**Description**

Failed to set the policy for an enterprise application.

**Possible Causes**

The input policy format is invalid.

**Solution**

Check the policy format and try again.

## 19110001 Invalid Parameter

**Error Message**

Parameter error.

**Description**

The parameter is invalid.

**Possible Causes**

1. The policy format is incorrect.

2. The parameter range is incorrect.

**Solution**

Check the following parameters:

1. Ensure that the policy format is correct.

2. Ensure that the parameter value is within the valid range.

## 19110002 File Sensitive Content Identification Timed Out

**Error Message**

Sensitive file content identification timed out.

**Description**

Identification of sensitive file content timed out. The identification process cannot be completed within the specified time.

**Possible Causes**

The processing time for sensitive file content identification exceeds the timeout threshold. Possible causes: The file is too large, the file content is highly complex, or the system resource usage is high.

**Solution**

Try again later.

## 19110003 File Not Supported

**Error Message**

The file is not supported.

**Description**

The passed-in file is not supported by the current operation. The path, type, or permission may not meet the requirements.

**Possible Causes**

1. The file path does not exist.

2. The file type is not supported.

3. The file permission is not supported.

**Solution**

Check the following:

1. Ensure that the file path exists and is accessible.

2. Ensure that the file type is supported.

3. Ensure that the file permissions meet the requirements.

## 19110004 System Function Abnormal

**Error Message**

A system error has occurred.

**Description**

The internal function module of the system is running abnormally, causing the operations for file sensitive content identification to fail.

**Possible Causes**

1. The service cannot be started.

2. The service on which the service depends cannot be started properly.

3. IPC data fails to be read or written.

4. The service is not initialized.

**Solution**

Try again later or restart the device when the internal system service is abnormal.