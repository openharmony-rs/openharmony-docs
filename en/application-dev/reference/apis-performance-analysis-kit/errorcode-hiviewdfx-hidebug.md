# HiDebug Error Codes

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @hello_harmony; @yu_haoqiaida-->
<!--Designer: @kutcherzhou1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 11400101 Failed to Obtain the System Service

**Error Message**

ServiceId invalid. The system ability does not exist.

**Description**

The system service cannot be obtained based on the specified service ID.

**Possible Causes**

The specified service ID is incorrect or the corresponding service is not started.

**Solution**

Specify a correct system service ID.

## 11400104 Remote Service Exception

**Error Message**

The interface call failed due to a remote exception.

> **NOTE**
>
> The error message may vary depending on the API.

**Description**

The remote service is abnormal.

**Possible Causes**

The remote service process crashes.

**Solution**

Restart the device and try again. If the fault persists, [export logs](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-setup-hilog#section2114542680)<!--RP1--> and send feedback to the official website.<!--RP1End-->

## 11400107 Failed to Fork the Child Dump Process

**Error Message**

Fork operation failed.

**Description**

Failed to fork the child dump process.

**Possible Causes**

The system resources are insufficient. You are advised to check the system load.

**Solution**

Fork the child dump process again. If the fault persists, filter error logs to locate the fault by referring to [Log Analysis](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-setup-hilog). If the problem persists, <!--RP1-->contact us.<!--RP1End-->

## 11400108 Failed to Wait for the Child Dump Process to Finish

**Error Message**

Failed to wait for the child process to finish.

**Description**

Failed to wait for the child dump process to finish.

**Possible Causes**

The system resources are insufficient. You are advised to check the system load.

**Solution**

Fork the child dump process again. If the fault persists, filter error logs to locate the fault by referring to [Log Analysis](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-setup-hilog). If the problem persists, <!--RP1-->contact us.<!--RP1End-->

## 11400109 Waiting for the Child Dump Process Times Out

**Error Message**

Timeout while waiting for the child process to finish.

**Description**

The child dump process times out.

**Possible Causes**

The dump process takes a long time. You are advised to check the system load.

**Solution**

Fork the child dump process again. If the fault persists, filter error logs to locate the fault by referring to [Log Analysis](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-setup-hilog). If the problem persists, <!--RP1-->contact us.<!--RP1End-->

## 11400110 Insufficient Disk Space

**Error Message**

Failed to create dump file.

**Description**

The disk space is insufficient.

**Possible Causes**

The available disk space is less than 30 GB.

**Solution**

Release the disk space to ensure that the available space is greater than 30 GB.

## 11400111 Failed to Call the Node-API

**Error Message**

Napi interface call exception.

**Description**

An exception occurs when the Node-API is called.

**Possible Causes**

The VM is abnormal.

**Solution**

Fork the child dump process again. If the fault persists, filter error logs to locate the fault by referring to [Log Analysis](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-setup-hilog). If the problem persists, <!--RP1-->contact us.<!--RP1End-->

## 11400112 Repeated Data Dump

**Error Message**

Repeated data dump.

**Description**

Dump data is collected repeatedly.

**Possible Causes**

This API has been called and is called repeatedly before the calling is complete.

**Solution**

Optimize the code logic to ensure that the next dump task starts after the previous dump task is complete.

## 11400113 Failed to Create a Dump File

**Error Message**

Failed to create dump file.

**Description**

Failed to create the dump file.

**Possible Causes**

1. A file with the same name exists in the process directory.

2. System resources are insufficient.

**Solution**

Fork the child dump process again. If the fault persists, filter error logs to locate the fault by referring to [Log Analysis](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-setup-hilog). If the problem persists, <!--RP1-->contact us.<!--RP1End-->

## 11400114 Failed to Enable GWP-ASan

**Error Message**

The number of GWP-ASAN applications of this device overflowed after last boot.

**Description**

After the device is restarted, the number of applications for which GWP-ASan is enabled exceeds the system limit.

**Possible Causes**

During the device running, the quota of applications enabled with GWP-ASan is used up.

**Solution**

Restart the system to update the device quota.
