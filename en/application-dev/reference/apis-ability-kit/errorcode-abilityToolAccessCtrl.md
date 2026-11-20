# Security Access Fence Service Error Codes

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @gcw_3MIoLA9y-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=004d584c36140b698c591de4648fccdd6ad90c32 translatedAt=2026-11-14T08:07:03.819Z pushedAt=2026-11-14T08:10:37.927Z nl=1 -->

The Security Access Fence Service module provides the capability to obtain authentication tickets for CLI tool execution, applicable to scenarios where credentials for CLI tool execution need to be obtained.

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 24010000 Invalid Parameter

**Error Message**

Invalid Parameter. Error message: messageInfo.

**Description**

The input parameter is incorrect.

**Possible Causes**

1. The CLI command name or subcommand name is empty.
2. ticketExpireTimeMs exceeds 60 seconds (60000 milliseconds).
3. The cliCmdInfos list is empty or its length exceeds 300.

**Solution**

Check the input parameters and correct the parameter values to valid values. For details about valid values, see the parameter description of each API in [@ohos.abilityToolAccessCtrl](js-apis-abilityToolAccessCtrl.md).

## 24010001 System Service Abnormal

**Error Message**

The service is abnormal.

**Description**

This error code is returned when the system service is abnormal.

**Possible Causes**

1. IPC communication fails.
2. The tool management service fails to start properly.

**Solution**

1. Retry later. This exception may be caused by a temporary IPC communication failure, and retrying will resolve the issue.
2. If the problem persists, check the system logs to confirm that the tool management service has started properly.
3. If the service fails to start, restart the device and retry.

## 24010002 Internal Service Error

**Error Message**

Common internal error.

**Description**

This error code is returned when an internal error occurs in the security access fence service, for example, a dependent system service is unavailable or resource access fails. It indicates that the server-side processing failed and the API call was not successfully executed.

**Possible Causes**

1. The system memory is insufficient, causing the internal context object to fail to be created.
2. The API is called during the window period of service switching or restart, and the underlying IPC link or the dependent service is not ready yet.
3. The application has not configured the permission corresponding to the command contained in the request.

**Solution**

1. Ensure that the system memory is sufficient and available. If the memory is insufficient, close unnecessary background processes to release memory and try again.
2. If the error occurs occasionally, check whether the call is made during the window period of service switching or restart. You can retry after an interval of 1 to 2 seconds.
3. The permission is missing in the requestPermissions configuration in the module.json5 file of the application.

## 24010006 Operation Not Allowed While the Device Is Locked

**Error Message**

The requested operation is not allowed to be executed while the device is locked.

**Description**

This error code is returned when an operation that cannot be executed while the device is locked is requested.

**Possible Causes**

An operation that cannot be executed while the device is locked was requested.

**Solution**

Make sure the device is unlocked before initiating the operation request.
