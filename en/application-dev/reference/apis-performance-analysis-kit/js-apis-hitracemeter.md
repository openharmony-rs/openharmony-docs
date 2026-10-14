# @ohos.hiTraceMeter (HiTraceMeter)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @yu_haoqiaida-->
<!--Designer: @MontSaintMichel-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=0e8943e8b8dd159f54837747c5c7d06207b95bd2 translatedAt=2026-09-09T06:17:23.124Z pushedAt=2026-09-09T10:17:22.443Z -->

This module provides the tracing capability for tracking process traces and measuring program execution performance, supporting multiple performance analysis scenarios such as asynchronous time-consuming task tracing, synchronous time-consuming task tracing, and integer variable tracing. The trace data of this module is used by the HiTraceMeter tool for analysis, helping developers quickly locate performance bottlenecks and optimize application performance.

For details about the development process, see [Using HiTraceMeter (ArkTS)](../../dfx/hitracemeter-guidelines-arkts.md).

> **NOTE**
>
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - You are advised to use the performance tracing APIs of API version 19. The performance tracing APIs [startTrace()](#hitracemeterstarttrace), [finishTrace()](#hitracemeterfinishtrace), and [traceByValue()](#hitracemetertracebyvalue) will be deprecated gradually.
>
> - The performance tracing APIs [startTrace()](#hitracemeterstarttrace), [finishTrace()](#hitracemeterfinishtrace), and [traceByValue()](#hitracemetertracebyvalue) always use the COMMERCIAL level.
>
> - The [user-mode trace format](../../dfx/hitracemeter-view.md#user-mode-trace-format) uses the vertical bar `|` as the delimiter. Therefore, string parameters passed through the performance tracing APIs should avoid containing this character to prevent trace parsing exceptions.
>
> - The total length of a [user-mode trace](../../dfx/hitracemeter-view.md#user-mode-trace-format) is limited to 512 characters, and the excess part will be truncated.

## Modules to Import

```js
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';
```

## hiTraceMeter.startTrace

startTrace(name: string, taskId: number): void

Marks the start of an asynchronous time-consuming task to trace. After the call succeeds, an asynchronous trace record is created.
> **NOTE**
>
> - This API must be used together with **finishTrace()**.
> - When **finishTrace()** is called, the **name** and **taskId** parameters must be exactly the same as those in **startTrace()**.
> - For multiple tasks with the same name, if they are executed in parallel, different task IDs must be used to distinguish them.

If multiple trace tasks with the same name need to be performed at the same time or a trace needs to be performed multiple times concurrently, different task IDs must be specified in **startTrace**.

If the trace tasks with the same name are not performed at the same time, the same taskId can be used. For a specific example, see [finishTrace()](#hitracemeterfinishtrace).

Since API version 19, you are advised to use [startAsyncTrace()](#hitracemeterstartasynctrace19), which must be used together with [finishAsyncTrace()](#hitracemeterfinishasynctrace19). In this way, you can specify the trace output level and category.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type  | Mandatory| Description                                                               |
| ------ | ------ | ---- |-------------------------------------------------------------------|
| name   | string | Yes   | Name of the task to trace.<br>Since the total length of a single trace record is limited to 512 bytes, the excess part will be truncated. It is recommended that the length of this parameter not exceed 420 bytes. |
| taskId | number | Yes   | Task ID.<br>Used to distinguish multiple tasks with the same name. Ensure that the task IDs of concurrently executed tasks with the same name are unique.            |

**Example**

```js
hiTraceMeter.startTrace("myTestFunc", 1);  // Start the asynchronous tracing task.
```

## hiTraceMeter.finishTrace

finishTrace(name: string, taskId: number): void

Marks the end of an asynchronous time-consuming task to trace. After the call succeeds, the tracing of the task is completed.
> **NOTE**
>
> - The **name** and **taskId** in **finishTrace** must be the same as the corresponding parameter values in [startTrace()](#hitracemeterstarttrace) at the start of the process.
> - Since API version 19, you are advised to use [finishAsyncTrace()](#hitracemeterfinishasynctrace19) (which must be used together with [startAsyncTrace()](#hitracemeterstartasynctrace19)).

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| name | string | Yes | Task name to trace, which must be consistent with the corresponding parameter value of [startTrace()](#hitracemeterstarttrace) at the start of the process. |
| taskId | number | Yes | Task ID, which must be consistent with the corresponding parameter value of [startTrace()](#hitracemeterstarttrace) at the start of the process. |

**Example**

```js
// Start trace tasks with the same name concurrently.
hiTraceMeter.startTrace("myTestFunc", 1);
// Service flow...
hiTraceMeter.startTrace("myTestFunc", 2);  // The second tracing task starts while the first task with the same name has not finished, resulting in parallel execution. Different taskIds are required to distinguish the tasks.
// Service flow...
hiTraceMeter.finishTrace("myTestFunc", 1);
// Service flow...
hiTraceMeter.finishTrace("myTestFunc", 2);
```

```js
// Start trace tasks with the same name in serial mode.
hiTraceMeter.startTrace("myTestFunc", 1);
// Service flow...
hiTraceMeter.finishTrace("myTestFunc", 1);  // End the first trace task.
// Service flow...
hiTraceMeter.startTrace("myTestFunc", 1);   // Start the second trace task with the same name in serial mode.
// Service flow...
hiTraceMeter.finishTrace("myTestFunc", 1);
```

## hiTraceMeter.traceByValue

traceByValue(name: string, count: number): void

Marks an integer variable to trace, whose value keeps changing. It is applicable to scenarios where real-time monitoring of value changes is required, such as the number of network requests, cache hit rate, and memory usage, helping developers quickly detect abnormal fluctuations and analyze data trends.
> **NOTE**
>
> Since API version 19, you are advised to use [traceByValue<sup>19+</sup>()](#hitracemetertracebyvalue19) to implement level-based control of trace output.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type  | Mandatory| Description                  |
| ------ | ------ | ---- | ---------------------- |
| name   | string | Yes   | Name of the integer variable to trace.<br>Since the total length of a single trace record is limited to 512 bytes, the excess part will be truncated. It is recommended that the length of this parameter not exceed 420 bytes. |
| count  | number | Yes  | Value of an integer variable.        |

**Example**

```js
let traceCount = 3;  // Define the initial value of the integer variable to be traced.
hiTraceMeter.traceByValue("myTestCount", traceCount);
traceCount = 4;
hiTraceMeter.traceByValue("myTestCount", traceCount);  // When myTestCount changes, the new value is recorded.
// Service flow...
```

## HiTraceOutputLevel<sup>19+</sup>

Enumerates the trace output levels.
> **NOTE**
> 
> Trace points below the system trace output level threshold will not take effect. The threshold of the log version is **INFO**, and that of the nolog version is **COMMERCIAL**.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

| Level      | Value  | Description                                   |
| ---------- | ---- | --------------------------------------- |
| DEBUG      | 0    | Output level used only for debugging, with the lowest priority. Trace points below the system trace output level threshold will not take effect.      |
| INFO       | 1    | Output level used for the log version. The log version threshold is **INFO**.                 |
| CRITICAL   | 2    | Output level used for the log version, with a higher priority than **INFO**, for trace events that require special attention. |
| COMMERCIAL | 3    | Output level used for the nolog version, with the highest priority. The nolog version threshold is **COMMERCIAL**.   |
| MAX        | COMMERCIAL    | Maximum trace output level: **COMMERCIAL**.   |

## hiTraceMeter.startAsyncTrace<sup>19+</sup>

startAsyncTrace(level: HiTraceOutputLevel, name: string, taskId: number, customCategory: string, customArgs?: string): void

Marks the start of an asynchronous time-consuming task to trace, with level-based control of trace output.
> **NOTE**
>
> If multiple tasks with the same **name** need to be traced, or the same task needs to be traced multiple times, and the tasks are executed at the same time, the **taskId** passed in each call to **startAsyncTrace** must be different. If tasks with the same **name** are executed in serial mode, the **taskId** can be the same. For a specific example, see the example in [finishAsyncTrace()](#hitracemeterfinishasynctrace19).

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name        | Type                                       | Mandatory| Description                                                                                                                               |
| -------------- | ------------------------------------------- | ---- |-----------------------------------------------------------------------------------------------------------------------------------|
| level          | [HiTraceOutputLevel](#hitraceoutputlevel19) | Yes  | Trace output level.                                                                                                                          |
| name           | string                                      | Yes   | Name of the task to trace.<br>Since the total length of a single trace record is limited to 512 bytes, the excess part will be truncated. It is recommended that the total length of **name**, **customCategory**, and **customArgs** not exceed 420 bytes.                            |
| taskId         | number                                      | Yes   | Task ID.<br>Used to distinguish multiple tasks with the same name. Ensure that the task IDs of concurrently executed tasks with the same name are unique.                                                                        |
| customCategory | string                                      | Yes   | Custom category name, used to aggregate asynchronous tracing points of the same category.<br>Since the total length of a single trace record is limited to 512 bytes, the excess part will be truncated. It is recommended that the total length of **name**, **customCategory**, and **customArgs** not exceed 420 bytes.               |
| customArgs     | string                                      | No   | Custom key-value pairs in the format key=value, with multiple key-value pairs separated by commas, used to record additional business information or debugging information (such as user ID and operation type). Pass this parameter when additional custom data is needed for trace analysis; otherwise, do not pass it. The default value is an empty string. Since the total length of a single trace record is limited to 512 bytes, the excess part will be truncated. It is recommended that the total length of **name**, **customCategory**, and **customArgs** not exceed 420 bytes. |

**Example**

```js
// If the customCategory parameter is not required, pass in an empty string.
// If the customArgs parameter is not required, do not pass in this parameter or pass in an empty string.
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
hiTraceMeter.startAsyncTrace(COMMERCIAL, "myTestFunc", 1, "", "");
hiTraceMeter.startAsyncTrace(COMMERCIAL, "myTestFunc", 2, "");
// Use commas (,) to separate multiple key-value pairs.
hiTraceMeter.startAsyncTrace(COMMERCIAL, "myTestFunc", 3, "categoryTest", "key1=value");
hiTraceMeter.startAsyncTrace(COMMERCIAL, "myTestFunc", 4, "categoryTest", "key1=value1,key2=value2");
```

## hiTraceMeter.finishAsyncTrace<sup>19+</sup>

finishAsyncTrace(level: HiTraceOutputLevel, name: string, taskId: number): void

Marks the end of an asynchronous time-consuming task to trace, with level-based control of trace output.
> **NOTE**
> 
> The **level**, **name**, and **taskId** in **finishAsyncTrace** must be the same as the corresponding parameter values in [startAsyncTrace()](#hitracemeterstartasynctrace19) at the start of the process.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type                                       | Mandatory| Description              |
| ------ | ------------------------------------------- | ---- | ------------------ |
| level  | [HiTraceOutputLevel](#hitraceoutputlevel19) | Yes   | Trace output level, which must be consistent with the **level** parameter value of [startAsyncTrace()](#hitracemeterstartasynctrace19) at the start of the process.     |
| name   | string                                      | Yes   | Name of the task to trace, which must be consistent with the **name** parameter value of [startAsyncTrace()](#hitracemeterstartasynctrace19) at the start of the process. |
| taskId | number                                      | Yes   | Task ID, which must be consistent with the **taskId** parameter value of [startAsyncTrace()](#hitracemeterstartasynctrace19) at the start of the process.           |

**Example**

```js
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
hiTraceMeter.finishAsyncTrace(COMMERCIAL, "myTestFunc", 1);
```

```js
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
// Start trace tasks with the same name concurrently.
// Start the first trace.
hiTraceMeter.startAsyncTrace(COMMERCIAL, "myTestFunc", 1, "categoryTest", "key=value");
// Service flow...
// Start the second trace with the same name while the first trace is still running. The tasks are running concurrently and therefore their taskId must be different.
hiTraceMeter.startAsyncTrace(COMMERCIAL, "myTestFunc", 2, "categoryTest", "key=value");
// Service flow...
// Stop the first trace.
hiTraceMeter.finishAsyncTrace(COMMERCIAL, "myTestFunc", 1);
// Service flow...
// Stop the second trace.
hiTraceMeter.finishAsyncTrace(COMMERCIAL, "myTestFunc", 2);
```

```js
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
// Start trace tasks with the same name in serial mode.
// Start the first trace.
hiTraceMeter.startAsyncTrace(COMMERCIAL, "myTestFunc", 1, "categoryTest", "key=value");
// Service flow...
// Stop the first trace.
hiTraceMeter.finishAsyncTrace(COMMERCIAL, "myTestFunc", 1);
// Service flow...
// Start the second trace with the same name. The traces with the same name are executed in serial mode.
hiTraceMeter.startAsyncTrace(COMMERCIAL, "myTestFunc", 1, "categoryTest", "key=value");
// Service flow...
// Stop the second trace with the same name.
hiTraceMeter.finishAsyncTrace(COMMERCIAL, "myTestFunc", 1);
```

## hiTraceMeter.startSyncTrace<sup>19+</sup>

startSyncTrace(level: HiTraceOutputLevel, name: string, customArgs?: string): void

Marks the start of a synchronous time-consuming task to trace, with level-based control of trace output.
> **NOTE**
>
> It is applicable to scenarios where the execution time of a synchronous code block needs to be traced, helping developers locate time-consuming issues in synchronous operations and optimize application response speed. For a specific example, see the example in [finishSyncTrace()](#hitracemeterfinishsynctrace19).

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name    | Type                                       | Mandatory| Description                                                                                    |
| ---------- | ------------------------------------------- | ---- |----------------------------------------------------------------------------------------|
| level      | [HiTraceOutputLevel](#hitraceoutputlevel19) | Yes  | Trace output level.                                                                               |
| name       | string                                      | Yes  | Name of the task to trace.<br>Since the total length of a single trace record is limited to 512 bytes, the excess part will be truncated. It is recommended that the total length of **name** and **customArgs** not exceed 420 bytes. |
| customArgs | string                                      | No   | Key-value pairs in the format of key=value, with multiple key-value pairs separated by commas, used to record additional service information or debugging information (such as function parameters and return values). Pass this parameter when custom data needs to be attached for trace analysis of synchronous tracing; omit it when no additional data is needed. The default value is an empty string. Since the total length of a single trace record is limited to 512 bytes, the excess part will be truncated. It is recommended that the total length of **name** and **customArgs** not exceed 420 bytes.                               |

**Example**

```js
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
// If the customArgs parameter is not required, do not pass in this parameter or pass in an empty string.
hiTraceMeter.startSyncTrace(COMMERCIAL, "myTestFunc");
hiTraceMeter.startSyncTrace(COMMERCIAL, "myTestFunc", "");
// Use commas (,) to separate multiple key-value pairs.
hiTraceMeter.startSyncTrace(COMMERCIAL, "myTestFunc", "key=value");
hiTraceMeter.startSyncTrace(COMMERCIAL, "myTestFunc", "key1=value1,key2=value2");
```

## hiTraceMeter.finishSyncTrace<sup>19+</sup>

finishSyncTrace(level: HiTraceOutputLevel): void

Marks the end of a synchronous time-consuming task to trace, with level-based control of trace output.
> **NOTE**
> 
> The **level** in **finishSyncTrace** must be the same as the corresponding parameter value in [startSyncTrace()](#hitracemeterstartsynctrace19) at the start of the process.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type                                       | Mandatory| Description          |
| ------ | ------------------------------------------- | ---- | -------------- |
| level  | [HiTraceOutputLevel](#hitraceoutputlevel19) | Yes  | Trace output level.|

**Example**

```js
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
hiTraceMeter.finishSyncTrace(COMMERCIAL);
```

```js
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
// The startSyncTrace and finishSyncTrace APIs can be nested and they matched each other based on proximity.
// Start the first trace.
hiTraceMeter.startSyncTrace(COMMERCIAL, "myTestFunc1", "key=value");
// Service flow...
// Start the second trace.
hiTraceMeter.startSyncTrace(COMMERCIAL, "myTestFunc2", "key=value");
// Service flow...
// Stop the second trace.
hiTraceMeter.finishSyncTrace(COMMERCIAL);
// Service flow...
// Stop the first trace.
hiTraceMeter.finishSyncTrace(COMMERCIAL);
```

## hiTraceMeter.traceByValue<sup>19+</sup>

traceByValue(level: HiTraceOutputLevel, name: string, count: number): void

Traces an integer with the trace output level specified. It is used to mark the name and value of a predefined integer variable to be traced.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type                                       | Mandatory| Description                  |
| ------ | ------------------------------------------- | ---- | ---------------------- |
| level  | [HiTraceOutputLevel](#hitraceoutputlevel19) | Yes  | Trace output level.        |
| name   | string                                      | Yes   | Name of the integer variable to trace.<br>Since the total length of a single trace record is limited to 512 bytes, the excess part will be truncated. It is recommended that the length of this parameter not exceed 420 bytes. |
| count  | number                                      | Yes  | Value of an integer variable.        |

**Example**

```js
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
let traceCount = 3;
hiTraceMeter.traceByValue(COMMERCIAL, "myTestCount", traceCount);
traceCount = 4;
hiTraceMeter.traceByValue(COMMERCIAL, "myTestCount", traceCount);
// Service flow...
```

## hiTraceMeter.isTraceEnabled<sup>19+</sup>

isTraceEnabled(): boolean

Checks whether application trace capture is enabled.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Returns**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | **true** is returned when the trace capture is enabled using [hitrace](../../dfx/hitrace.md). **false** is returned when it is disabled or stopped. In this case, calling the HiTraceMeter API does not take effect.|

**Example**

```js
if (hiTraceMeter.isTraceEnabled()) {
  // Service flow...
} else {
  // Service flow...
}
```

## TraceEventListener<sup>22+</sup>

type TraceEventListener = (traceStatus: boolean) => void

Defines a callback to listen for whether the trace capture is enabled.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name     | Type   | Mandatory| Description                                                    |
| ----------- | ------- | ---- | -------------------------------------------------------- |
| traceStatus | boolean | Yes  | Whether the trace capture is enabled for the current application.<br>The value **true** indicates that the trace capture is enabled, and **false** indicates the opposite.|

## hiTraceMeter.registerTraceListener<sup>22+</sup>

registerTraceListener(callback: TraceEventListener): number

Registers a callback to notify whether the application trace capture is enabled. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> - After registration succeeds, the callback is executed once immediately. Subsequent callbacks are triggered by state changes of the application trace capture switch.
> - Callbacks are stored in the application process. A process can register up to 10 callbacks.
> - If a registered callback contains time-consuming operations, the registration or unregistration behavior is blocked (waiting for the callback to complete) when the callback is executed. Therefore, you are advised not to register or unregister callbacks containing time-consuming operations in the main thread of the application to avoid screen freezing.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name  | Type                                       | Mandatory| Description            |
| -------- | ------------------------------------------- | ---- | ---------------- |
| callback | [TraceEventListener](#traceeventlistener22) | Yes | Callback invoked when the trace capture switch state of the application changes. When the trace capture switch state changes (from on to off or from off to on), this callback is triggered and the current trace state is passed in. After registration success, the callback is executed once immediately, and it is triggered each time the trace capture switch state changes. |

**Returns**

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| number | Callback registration status.<br>>= 0: registration success, returns the callback index used for unregistration, with the index ranging from [0, 9];<br> **-1**: the maximum number of registered callback functions has been reached;<br> **-2**: invalid parameter, the parameter is not of the TraceEventListener type. |

**Example**

```js
// Define the registered callback.
let callback: hiTraceMeter.TraceEventListener = (traceStatus: boolean) => {
  if (traceStatus) {
    // Trace capture is enabled for the current application.
    // ...
  } else {
    // Trace capture is disabled for the current application.
    // ...
  }
};

// Register a callback to notify whether the application trace capture is enabled.
let index = hiTraceMeter.registerTraceListener(callback);
if (index < 0) {
  // Handle exceptions.
}
```

## hiTraceMeter.unregisterTraceListener<sup>22+</sup>

unregisterTraceListener(index: number): number

Unregisters the callback function used to notify whether the trace capture is enabled, which is registered using **registerTraceListener()**.


**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| index  | number | Yes   | Index of the registered callback function. The value ranges from 0 to 9, which is the return value when [registerTraceListener()](#hitracemeterregistertracelistener22) is called successfully. |

**Returns**

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| number | Callback unregistration status.<br>**0**: unregistration success;<br>**-1**: the callback at the target index is not registered;<br>**-2**: invalid index. The value of the index parameter is not within [0, 9]. |

**Example**

```js
// Deregister the callback used to notify whether the application trace capture is enabled. index is the callback index returned by hiTraceMeter.registerTraceListener.
let ret = hiTraceMeter.unregisterTraceListener(index);
if (ret < 0) {
  // Handle exceptions.
}
```
