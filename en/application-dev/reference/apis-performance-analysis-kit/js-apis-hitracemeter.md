# @ohos.hiTraceMeter (Performance Tracing)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @qq_437963121-->
<!--Designer: @kutcherzhou1; @MontSaintMichel-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

The **HiTraceMeter** module provides the functions of tracing service processes and monitoring the system performance. It provides the data needed for HiTraceMeter to carry out performance analysis.

For details about the development process, see [Using HiTraceMeter](../../dfx/hitracemeter-guidelines-arkts.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> You are advised to use the performance tracing APIs of API version 19. The [startTrace()](#hitracemeterstarttrace), [finishTrace()](#hitracemeterfinishtrace), and [traceByValue()](#hitracemetertracebyvalue) APIs will be deprecated.
>
> The trace output level cannot be specified in the [startTrace()](#hitracemeterstarttrace), [finishTrace()](#hitracemeterfinishtrace) and [traceByValue()](#hitracemetertracebyvalue) APIs. By default, the trace output level is **COMMERCIAL**.
>
> The vertical bar (|) is used as the separator in [user-mode trace format](../../dfx/hitracemeter-view.md#user-mode-trace-format). Therefore, the string parameters passed by the performance tracing APIs must exclude this character to avoid trace parsing exceptions.
>
> The maximum length of a [user-mode trace](../../dfx/hitracemeter-view.md#user-mode-trace-format) is 512 characters. Excess characters will be truncated.

## Modules to Import

```js
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';
```

## hiTraceMeter.startTrace

startTrace(name: string, taskId: number): void

Starts an asynchronous trace.

If multiple trace tasks with the same name need to be performed at the same time or a trace needs to be performed multiple times concurrently, different task IDs must be specified in **startTrace**.

If the trace tasks with the same name are not performed at the same time, the same taskId can be used. For a specific example, see [finishTrace()](#hitracemeterfinishtrace).

Since API version 19, you are advised to use [startAsyncTrace()](#hitracemeterstartasynctrace19), which must be used together with [finishAsyncTrace()](#hitracemeterfinishasynctrace19). In this way, you can specify the trace output level and category.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| name   | string | Yes  | Name of the trace to start.|
| taskId | number | Yes  | Task ID.          |

**Example**

```js
hiTraceMeter.startTrace("myTestFunc", 1);
```

## hiTraceMeter.finishTrace

finishTrace(name: string, taskId: number): void

Stops an asynchronous trace.

To stop a trace, the values of name and task ID in **finishTrace** must be the same as those in [startTrace()](#hitracemeterstarttrace).

Since API version 19, you are advised to use [finishAsyncTrace()](#hitracemeterfinishasynctrace19), which must be used together with [startAsyncTrace()](#hitracemeterstartasynctrace19).

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| name   | string | Yes  | Name of the trace to start.|
| taskId | number | Yes  | Task ID.          |

**Example**

```js
hiTraceMeter.finishTrace("myTestFunc", 1);
```

```js
// Start trace tasks with the same name concurrently.
hiTraceMeter.startTrace("myTestFunc", 1);
// Service flow...
hiTraceMeter.startTrace("myTestFunc", 2);  // Start the second trace with the same name while the first task is still running. The tasks are running concurrently and therefore their taskId must be different.
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

Traces the value changes of an integer variable.

Since API version 19, you are advised to use the [traceByValue<sup>19+</sup>()](#hitracemetertracebyvalue19) API to specify the trace output level

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type  | Mandatory| Description                  |
| ------ | ------ | ---- | ---------------------- |
| name   | string | Yes  | Name of the integer variable to trace.|
| count  | number | Yes  | Value of an integer variable.        |

**Example**

```js
let traceCount = 3;
hiTraceMeter.traceByValue("myTestCount", traceCount);
traceCount = 4;
hiTraceMeter.traceByValue("myTestCount", traceCount);
// Service flow...
```

## HiTraceOutputLevel<sup>19+</sup>

Enumerates trace output levels.

The trace output level lower than the threshold does not take effect. The log version threshold is **INFO**, and the nolog version threshold is **COMMERCIAL**.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

| Level      | Value  | Description                                   |
| ---------- | ---- | --------------------------------------- |
| DEBUG      | 0    | Level used only for debugging, which has the lowest priority.     |
| INFO       | 1    | Level for the log version.                |
| CRITICAL   | 2    | Level for the log version, which has a higher priority than **INFO**.|
| COMMERCIAL | 3    | Level for the nolog version, which has the highest priority.  |
| MAX        | 3    | Maximum trace output level: **COMMERCIAL**.   |

## hiTraceMeter.startAsyncTrace<sup>19+</sup>

startAsyncTrace(level: HiTraceOutputLevel, name: string, taskId: number, customCategory: string, customArgs?: string): void

Starts an asynchronous trace with the trace output level specified.

If multiple trace tasks with the same name need to be performed at the same time or a trace needs to be performed multiple times concurrently, different task IDs must be specified in **startAsyncTrace**.

If the trace tasks with the same name are not performed at the same time, the same taskId can be used. For details, see [finishAsyncTrace()](#hitracemeterfinishasynctrace19).

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name        | Type                                       | Mandatory| Description                                                        |
| -------------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| level          | [HiTraceOutputLevel](#hitraceoutputlevel19) | Yes  | Trace output level.                                              |
| name           | string                                      | Yes  | Name of the trace to start.                                          |
| taskId         | number                                      | Yes  | Task ID.                                                    |
| customCategory | string                                      | Yes  | Custom category name, which is used to collect asynchronous trace data of the same type.                |
| customArgs     | string                                      | No  | Custom key-value pair. The format is **key=value**. Use commas (,) to separate multiple key-value pairs.<br>If this parameter is not passed in, an empty string is passed in.|

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

Stops an asynchronous trace with the trace output level specified.

The **level**, **name**, and **taskId** used in **finishAsyncTrace()** must be the same as those of [startAsyncTrace()](#hitracemeterstartasynctrace19).

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type                                       | Mandatory| Description              |
| ------ | ------------------------------------------- | ---- | ------------------ |
| level  | [HiTraceOutputLevel](#hitraceoutputlevel19) | Yes  | Trace output level.    |
| name   | string                                      | Yes  | Name of the trace to start.|
| taskId | number                                      | Yes  | Task ID.          |

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

Starts a synchronous trace with the trace output level specified. For details, see [finishSyncTrace()](#hitracemeterfinishsynctrace19).

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name    | Type                                       | Mandatory| Description                                                        |
| ---------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| level      | [HiTraceOutputLevel](#hitraceoutputlevel19) | Yes  | Trace output level.                                              |
| name       | string                                      | Yes  | Name of the trace to start.                                          |
| customArgs | string                                      | No  | Custom key-value pair. The format is **key=value**. Use commas (,) to separate multiple key-value pairs.<br>If this parameter is not passed in, an empty string is passed in.|

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

Stops a synchronous trace with the trace output level specified.

The **level** used in **finishSyncTrace** must be the same as that of [startSyncTrace()](#hitracemeterstartsynctrace19).

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

Traces an integer with the trace output level specified. **name** and **count** are used to identify the name and value of an integer variable to be traced.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type                                       | Mandatory| Description                  |
| ------ | ------------------------------------------- | ---- | ---------------------- |
| level  | [HiTraceOutputLevel](#hitraceoutputlevel19) | Yes  | Trace output level.        |
| name   | string                                      | Yes  | Name of the integer variable to trace.|
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

Registers a callback to notify whether the application trace capture is enabled. This API uses a synchronous callback to return the result.

After the registration is successful, the callback is executed immediately. Subsequent callbacks are executed when the application trace capture status changes.

Callbacks are stored in the application process. A maximum of 10 callbacks can be registered in a process.

> **NOTE**
>
> If the callback contains time-consuming operations, the registration or deregistration will be blocked (waiting for the callback execution to complete) when the callback is executed.
>
> Therefore, you are advised not to register or deregister callbacks containing time-consuming operations in the main thread of the application to avoid application freeze.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name  | Type                                       | Mandatory| Description            |
| -------- | ------------------------------------------- | ---- | ---------------- |
| callback | [TraceEventListener](#traceeventlistener22) | Yes  | Registered callback.|

**Returns**

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| number | Callback registration status.<br>>= 0: The registration is successful. The callback index for deregistration is returned. The index ranges from 0 to 9.<br> **-1**: The maximum number of callbacks has been reached.<br> **-2**: Invalid parameter. The parameter is not of the **TraceEventListener** type.|

**Example**

```js
// Define the registered callback.
let callback: hiTraceMeter.TraceEventListener = (traceStatus: boolean) => {
    if (traceStatus) {
        // Trace capture is enabled for the current application. The service process is as follows:
    } else {
        // Trace capture is disabled for the current application. The service process is as follows:
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

Deregisters the callback used to notify whether the application trace capture is enabled.

Deregisters the callback associated with the callback index returned by [registerTraceListener()](#hitracemeterregistertracelistener22).

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| index  | number | Yes  | Index of the registered callback.|

**Returns**

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| number | Callback deregistration status.<br>**0**: Deregistration succeeded.<br>**-1**: The callback corresponding to the index is not registered.<br>**-2**: Invalid index. The index value is not within the range of 0 to 9.|

**Example**

```js
// Deregister the callback used to notify whether the application trace capture is enabled. index is the callback index returned by hiTraceMeter.registerTraceListener.
let ret = hiTraceMeter.unregisterTraceListener(index);
if (ret < 0) {
    // Handle exceptions.
}
```
