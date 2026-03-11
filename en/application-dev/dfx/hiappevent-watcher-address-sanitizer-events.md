# Address Sanitizer Event Overview
<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @mlkgeek-->
<!--Designer: @StevenLai1994-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Overview

An address sanitizer error refers to an invalid memory access that causes application exceptions or crashes.

You can subscribe to address sanitizer events using the ArkTS and C/C++ APIs provided by HiAppEvent. For details, see the following documents:

- [Subscribing to Address Sanitizer Events (ArkTS)](hiappevent-watcher-address-sanitizer-events-arkts.md)

- [Subscribing to Address Sanitizer Events (C/C++)](hiappevent-watcher-address-sanitizer-events-ndk.md)

> **NOTE**
>
> Address sanitizer events can be subscribed to using HiAppEvent in [application clones](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/app-clone). Since API version 22, this feature is also supported for [input method applications](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/inputmethod-application-guide). This feature is not supported for atomic services.

## Detection Principles

For details, see [Address Sanitizer Detection](address-sanitizer-guidelines.md).

## Event Fields

### params

 

| Name| Type| Description|
| -------- | -------- | -------- |
| time | number | Event triggering time, in ms.|
| bundle_version | string | Application version.|
| bundle_name | string | Application name.|
| pid | number | Process ID of the application.|
| uid | number | User ID of the application.|
| type | string | Type of the address sanitizer error. For details, see the description of **type**.|
| external_log | string[] | Path of the error log file. If the directory files exceed the threshold (for details, see **log_over_limit**), new log files may fail to be written. Therefore, delete the log files immediately after they are processed.|
| log_over_limit | boolean | Whether the size of generated fault log files and existing log files exceeds the upper limit (5 MB). The value **true** indicates that the upper limit is exceeded and logs fail to be written. The value **false** indicates that the upper limit is not exceeded.|

### type

 

| Value| Description|
| -------- | -------- |
| GWP-ASAN | Error triggered by GWP-ASan.|
| UBSAN | Error triggered by UBSan.|
| TSAN | Error triggered by TSan.|
| FDSAN | Error triggered by [fdsan](../napi/fdsan.md). This type is supported since API version 20.|
| stack tag-mismatch | Stack tag mismatch detected by HWASan, possibly due to stack use-after-return, out-of-scope access, or out-of-bounds access.|
| alloc-dealloc-mismatch | The memory allocation and release modes do not match.|
| allocation-size-too-big | The heap memory is too large.|
| calloc-overflow | **calloc()** fails to allocate memory.|
| container-overflow | The container overflows.|
| double-free | The memory is repeatedly released.|
| dynamic-stack-buffer-overflow | The buffer access exceeds the boundary of a stack-allocated object.|
| global-buffer-overflow | The global buffer overflows.|
| heap-buffer-overflow | The heap buffer overflows.|
| heap-use-after-free | The released heap memory is used.|
| invalid-allocation-alignment | The alignment mode specified in memory allocation is invalid.|
| memcpy-param-overlap | **memcpy()** does not support overlapping memory regions.|
| new-delete-type-mismatch | The released memory size does not match the allocated memory size.|
| stack-buffer-overflow | The stack buffer overflows.|
| stack-buffer-underflow | The stack buffer underflow occurs.|
| stack-use-after-return | The stack memory is used after the function has returned.|
| stack-use-after-scope | The stack memory is out of range.|
| strcat-param-overlap | The source and destination buffers used for string concatenation overlap.|
| use-after-poison | The memory address is used after being poisoned.|
