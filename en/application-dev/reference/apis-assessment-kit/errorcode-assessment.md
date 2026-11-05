# Assessment Management Error Codes

<!--Kit: Automatic Scene Configuration Kit-->
<!--Subsystem: Customization-->
<!--Owner: @weredust-->
<!--Designer: @weredust-->
<!--Tester: @weredust-->
<!--Adviser: @weredust-->
<!-- md-trans-meta sourceCommit=3194fdbc42d6357f420eb498f6d963c04a35b419 translatedAt=2026-11-03T13:36:24.998Z pushedAt=2026-11-04T06:59:09.187Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 36700001 Assessment Internal Error

**Error Message**

Assessment internal error. Possible cause: IPC invocation failed internally.

**Description**

When the begin or end interface is called, an internal error occurs in the assessment configuration service, the operation fails, and the system generates this error code.

**Possible Cause**

The internal IPC invocation of the assessment configuration service failed.

**Solution**

Call the interface again to retry. If the operation still fails after multiple retries, check the running status of the assessment configuration service, or contact the device vendor for technical support.

## 36700002 Assessment Configuration Service Is Already Active

**Error Message**

Assessment configuration service is already active. Possible cause: Assessment resource conflict.

**Description**

When the device is already in the assessment state, calling the begin interface again causes an assessment resource conflict, so the assessment cannot be started repeatedly, and the system generates this error code.

**Possible Cause**

1. The current application's previous assessment has not ended, and the begin interface is called again to start a new assessment.

2. Another application has started an assessment and it has not ended yet.

**Solution**

1. Call the isActive interface to query the current assessment status. If it returns true, call the end interface to end the current assessment first, and then start a new assessment.

2. Check whether another application has started an assessment that has not ended yet. If so, the application that started the assessment must call the end interface to end the assessment before a new assessment can be started.

## 36700003 Assessment Configuration Service Is Not Active

**Error Message**

Assessment configuration service is not active. Possible cause: Not in assessment state.

**Description**

The system generates this error code when the end interface is called while the device is not in the assessment state.

**Possible Cause**

The end interface is called when there is no assessment in progress.

**Solution**

Call the isActive interface to confirm the current assessment state, and call the end interface to terminate the assessment only when it returns true.

## 36700004 Invalid Operation

**Error Message**

Invalid operation. Possible cause: Cannot terminate another active assessment.

**Description**

This error code is generated when you call the end interface to terminate an assessment that was not started by the current application.

**Possible Cause**

The current active assessment was started by another application, and the current application does not have permission to terminate it.

**Solution**

Identify the application that started the assessment, and have that application call the end interface to terminate the assessment.
