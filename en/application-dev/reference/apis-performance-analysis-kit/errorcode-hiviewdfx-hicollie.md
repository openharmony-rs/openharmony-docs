# HiCollie Error Codes

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @rr_cn-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

> **Note:**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 29800001 Failed to Obtain the System Service

**Error Message**

Wrong thread context.The function can not be called from main thread.

**Description**

The API fails to be called from the thread.

**Possible Causes**

The API cannot be called from the main thread.

**Solution**

Call the API from a non-main thread.

## 29800002 Failed to Call the Remote API

**Error Message**

Remote call failed.

**Description**

The API fails to be called for the remote service.

**Possible Causes**

The service is not started or crashes.

**Solution**

Call the API again.

## 29800003 Invalid Timer Name

**Error Message**

Invalid timer name.

**Description**

The timer name is invalid.

**Possible Causes**

The **name** is **nullptr** or points to an empty string.

**Solution**

Check the **name** parameter and ensure that it is neither a **nullptr** nor a pointer to an empty string.

## 29800004 Invalid Timeout Value

**Error Message**

Invalid timeout value.

**Description**

The **timeout** value is invalid.

**Possible Causes**

The **timeout** value is **0**.

**Solution**

Check the **timeout** value and ensure that it is greater than 0.

## 29800005 Incorrect Process Context

**Error Message**

Wrong process context.

**Description**

The process context is incorrect.

**Possible Causes**

The **appspawn** or **nativespawn** process is used to access the timer.

**Solution**

Do not access HiCollie in the **appspawn** and **nativespawn** processes.

## 29800006 Incorrect Timer ID

**Error Message**

Wrong timer id output param.

**Description**

The timer task ID is incorrect.

**Possible Causes**

- The integer pointer ID is **nullptr**.
- The number of concurrent tasks in the process that accesses the HiCollie timer reaches the maximum value 128.

**Solution**

- Check the ID and ensure that it is a non-null integer pointer.
- Retry the operation or reduce the number of HiCollie timer tasks in the process.
