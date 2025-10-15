# Resource Leak Event Overview

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @xuxinao-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Overview

Resource leaks occur when resources, such as handles, threads, or memory, are not properly released during application running. As a result, the resources are occupied for a long time and cannot be used by other applications. If a certain type of resource is exhausted, the system may crash or restart.

This section describes the fields of resource leak events. For details about how to use the HiAppEvent API to subscribe to system resource leak events, refer to the following documents. Currently, ArkTS and C/C++ APIs are provided.

- - [Subscribing to Resource Leak Events (ArkTS)](hiappevent-watcher-resourceleak-events-arkts.md)

- - [Subscribing to Resource Leak Events (C/C++)](hiappevent-watcher-resourceleak-events-ndk.md)

## Detection Principles

For details about the detection principles, see [Resource Leak Detection](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/resource-leak-guidelines).

## Custom Specifications

### Available APIs

| Name| Description|
| -------- | -------- |
| setEventConfig(name: string, config: Record<string, ParamType>): Promise&lt;void> | Sets the specifications of resource leak logs. name must be the resource leak event name constant hiappevent.event.RESOURCE_OVERLIMIT. **Only JS memory leak is supported.**<br>Note: This API is supported since API version 20.|

### Parameter Settings

You can use the APIs provided by HiAppEvent to set the specifications of RESOURCE_OVERLIMIT logs and callback events in Record&lt;string, ParamType>. The specific parameter descriptions are as follows.

| Name         | Type  | Mandatory| Description                                                        |
| --------------- | ------ | ---- | ------------------------------------------------------------ |
| js_heap_logtype | string | No  | event: No heap snapshot is transferred when an OOM occurs.<br>event_rawheap: The system generates and transfers a heap snapshot when an OOM occurs.<br>**Note**: Only the preceding two values are supported. If other values are passed, the method fails to be called and no effect is generated.|

> **NOTE**
>
> Even if js_heap_logtype is set to event_rawheap, the heap snapshot file may not be generated. This is because the app may exit in advance due to screen freezing caused by performance problems when the heap snapshot is generated.

Parameter configuration example:

```ts
let configParams: Record<string, hiAppEvent.ParamType> = {
    "js_heap_logtype": "event", // Obtain only events.
    // "js_heap_logtype": "event_rawheap", // Obtain heap snapshots.
};

hiAppEvent.setEventConfig(hiappEvent.event.RESOURCE_OVERLIMIT, configParams);
```

> **NOTE**
>
> When the setEventConfig API is called, the content called each time takes effect only within the current app lifecycle. After the app is restarted, you need to call the setEventConfig API again.
>
> The setEventConfig API can be called for multiple times within the same app lifecycle. The value of the last successful call is used.
>
> During debugging and self-testing, if the number of OOMs triggered in a day is too large, you may fail to receive the JS memory leak event returned by the HiAppEvent. You can change the system time to one day later to avoid this problem.

## params

The **params** parameter in the event information is described as follows.

| Name| Type| Description|
| -------- | -------- | -------- |
| time | number | Event triggering time, in ms.|
| bundle_version | string | Application version.|
| bundle_name | string | Application name.|
| pid | number | Process ID of an application.|
| uid | number | User ID of an application.|
| resource_type | string | Resource type. For details, see **resource_type**.|
| memory | object | Memory information (only available for **pss_memory** and **js_heap**). For details, see **memory**.|
| fd | object | File descriptor information (only available for **fd**). For details, see **fd**.|
| thread | object | Thread information (only available for **thread**). For details, see **thread**.|
| external_log | string[] | Path of the error log file. If the directory files exceed the threshold (for details, see **log_over_limit**), new log files may fail to be written. Therefore, delete the log files immediately after they are processed.|
| log_over_limit | boolean | Whether the size of generated fault log files and existing log files exceeds the upper limit (2 GB). The value **true** indicates that the upper limit is exceeded and logs fail to be written. The value **false** indicates that the upper limit is not exceeded.|

### resource_type

| Value| Description|
| -------- | -------- |
| pss_memory | PSS memory leak.|
| ion_memory | ION memory leak.<br>**Note**: This field is supported since API version 20.|
| gpu_memory | GPU memory leak.<br>**Note**: This field is supported since API version 20.|
| js_heap | JS memory leak.|
| fd | Handle leak.|
| thread | Thread leak.|

### memory

| Name| Type| Description|
| -------- | -------- | -------- |
| rss | number | Size of the memory allocated for a process (only available for **pss_memory**, **ion_memory**, and **gpu_memory**), in KB.|
| vss | number | Size of the virtual memory applied by a process from the system (only available for **pss_memory**, **ion_memory**, and **gpu_memory**), in KB.|
| pss | number | Size of the physical memory actually used by a process (only available for **pss_memory**, **ion_memory**, and **gpu_memory**), in KB.|
| ion | number | Size of the ION memory actually used by a process (only available for **pss_memory**, **ion_memory**, and **gpu_memory**), in KB.<br>**Note**: This field is supported since API version 20.|
| gpu | number | Size of the GPU memory actually used by a process (only available for **pss_memory**, **ion_memory**, and **gpu_memory**), in KB.<br>**Note**: This field is supported since API version 20.|
| sys_free_mem | number | Size of the free memory (only available for **pss_memory**, **ion_memory**, and **gpu_memory**), in KB.|
| sys_avail_mem | number | Size of the available memory (only available for **pss_memory**, **ion_memory**, and **gpu_memory**), in KB.|
| sys_total_mem | number | Size of the total memory (only available for **pss_memory**, **ion_memory**, and **gpu_memory**), in KB.|
| limit_size | number | Limit of memory size (only available for **js_heap**), in KB.|
| live_object_size | number | Size of the used memory (only available for **js_heap**), in KB.|

### fd field description

| Name| Type| Description|
| -------- | -------- | -------- |
| num | number | Total number of FDs.|
| top_fd_type | string | FD type that is most frequently used.|
| top_fd_num | number | Number of FDs that are most frequently used.|

### thread

| Name| Type| Description|
| -------- | -------- | -------- |
| num | number | Total number of threads.|

## Parameters for Customizing Events

Currently, the resource leak event reports the JS memory leak event information, which may not meet your personal requirements. Therefore, the **setEventParam** method is provided to customize event reporting information.

### Available APIs

| Name| Description|
| -------- | -------- |
| setEventParam(params: Record&lt;string, ParamType>, domain: string, name?: string): Promise&lt;void> | Sets custom event parameters.<br>Note: This API is supported since API version 20.|
