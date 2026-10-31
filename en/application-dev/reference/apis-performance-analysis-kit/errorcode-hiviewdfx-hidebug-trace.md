# HiDebug Trace Error Codes

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=f723d457b4c69fd7c9854a237d35cae9f2a87b83 translatedAt=2026-09-16T11:05:32.375Z pushedAt=2026-09-20T09:01:52.267Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 11400102 Repeated Trace Capture

**Error Message**

Capture trace already enabled.

**Description**

The trace capture has been enabled for the process.

**Possible Causes**

The trace capture is in progress.

**Solution**

Wait for the trace capture to finish, or call the **hidebug.stopAppTraceCapture** API to stop the running trace capture, to resolve the duplicate capture issue.

## 11400103 Permission Verification Failed

**Error Message**

No write permission on the file.

**Description**

You do not have the permission to write the trace file in the current directory.

**Possible Causes**

The directory does not exist or is deleted by mistake.

**Solution**

Run the capture API again to regenerate the correct directory file, to resolve the permission verification failure issue.

## 11400104 Internal Error

**Error Message**

Abnormal trace status.

> **NOTE**
>
> The error message may vary depending on the API.

**Description**

The current trace capture encounters an internal error.

**Possible Causes**

The system kernel crashes or the application process does not respond.

**Solution**

Restart the application or device to resolve the issue of an abnormal internal state of trace capture.

## 11400105 Trace Capture Disabled

**Error Message**

No capture trace running.

**Description**

No trace capture is in progress.

**Possible Causes**

Trace capture is not enabled.

**Solution**

Ensure that trace capture has been successfully started before calling the API to stop trace capture.

## 11400106 API Call Quota Exceeded

**Error Message**

Quota exceeded.

**Description**

The API call quota is exceeded.

**Possible Causes**

1. The API is called by a process more than the quota (once per day).

2. The API is called by the device more than the quota (five times per week).

**Solution**

Wait for the call quota of the process or device to be refreshed, to resolve the issue that the API call quota has been exceeded.

## 11400120 Trace File Storage Limit Reached

**Error Message**

Trace storage limit reached.

**Description**

The number of .sys files returned by the trace capture in the directory exceeds the upper limit.

**Possible Causes**

The number of .sys files returned by the trace capture in the directory is greater than or equal to 3.

**Solution**

Clean up the files in the trace directory to resolve the issue that the trace file storage limit has been reached.

## 11400302 Trace Collection Exceeds the Resource Quota

**Error Message**

Resource unavailable.

**Description**

The number of times the application calls trace capture exceeds the system resource quota.

> **NOTE**
>
> In developer mode, the [applications of the debug version](../../dfx/performance-analysis-kit-terminology.md#applications-of-the-debug-version) is not controlled.

**Possible Causes**

The number of times the application calls trace capture exceeds the daily quota of system resources.

**Solution**

Wait for the system resource quota to be refreshed on the next day, to resolve the issue that trace capture exceeds the resource quota.
