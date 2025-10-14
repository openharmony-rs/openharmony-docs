# HiDebug Trace Error Codes

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @hello_harmony; @yu_haoqiaida-->
<!--Designer: @kutcherzhou1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 11400102 Repeated Trace Collection

**Error Message**

Capture trace already enabled.

**Description**

The trace collection has been enabled for the process.

**Possible Causes**

The trace collection is in progress.

**Solution**

Wait until the trace collection is complete or call hidebug.stopAppTraceCapture to disable the trace collection.

## 11400103 Permission Verification Failed

**Error Message**

No write permission on the file.

**Description**

You do not have the permission to write the trace file in the current directory.

**Possible Causes**

The directory does not exist or is deleted by mistake.

**Solution**

Run the trace collection again to generate a correct trace file in the current directory.

## 11400104 Internal Error

**Error Message**

Abnormal trace status.

> **NOTE**
>
> The error information is subject to the actual content returned by the API.

**Description**

This error code is reported if the current trace encounters an internal error.

**Possible Causes**

The system kernel breaks down or the application process does not respond.

**Solution**

Restart the application or device.

## 11400105 Trace Collection Is Not Enabled

**Error Message**

No capture trace running.

**Description**

This error code is reported if no trace is in progress.

**Possible Causes**

Trace collection is not enabled.

**Solution**

Enable trace collection and then stop it.

## 11400106 The API Call Quota Is Exceeded

**Error Message**

Quota exceeded.

**Description**

The API call quota is exceeded.

**Possible Causes**

1. This API is called by a process more than once per day.

2. This API is called by the system more than five times per week.

**Solution**

Wait for the update of the API call quota.
