# HiDebug Trace Error Codes

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @hello_harmony; @leiguangyu-->
<!--Designer: @kutcherzhou1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

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

Wait until the trace capture is complete or call **hidebug.stopAppTraceCapture** to stop the trace capture.

## 11400103 Permission Verification Failed

**Error Message**

No write permission on the file.

**Description**

You do not have the permission to write the trace file in the current directory.

**Possible Causes**

The directory does not exist or is deleted by mistake.

**Solution**

Run the trace capture again to generate a correct trace file in the current directory.

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

Restart the application or device.

## 11400105 Trace Capture Disabled

**Error Message**

No capture trace running.

**Description**

No trace capture is in progress.

**Possible Causes**

Trace capture is not enabled.

**Solution**

Enable trace capture and then stop it.

## 11400106 API Call Quota Exceeded

**Error Message**

Quota exceeded.

**Description**

The API call quota is exceeded.

**Possible Causes**

1. This API is called by a process more than once per day.

2. This API is called by the system more than five times per week.

**Solution**

Wait for the update of the API call quota.

## 11400120 Trace File Storage Limit Reached

**Error Message**

Trace storage limit reached.

**Description**

The number of .sys files returned by the trace collection in the directory exceeds the upper limit.

**Possible Causes**

The number of .sys files returned by the trace collection in the directory is greater than or equal to 3.

**Solution**

Delete files from the trace directory.

## 11400302 Trace Collection Exceeds the Resource Quota

**Error Message**

Resource unavailable.

**Description**

The number of times the application calls trace collection exceeds the system resource quota.

> **NOTE**
>
> In developer mode, the [applications of the debug version](../../dfx/performance-analysis-kit-terminology.md#applications-of-the-debug-version) is not controlled.

**Possible Causes**

The number of times the application calls trace collection exceeds the daily quota of system resources.

**Solution**

If the quota is used up on the current day, wait until the system resource quota is updated on the next day.
