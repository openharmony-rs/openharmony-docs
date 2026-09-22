# @ohos.hiTraceChain (HiTraceChain)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @yu_haoqiaida-->
<!--Designer: @MontSaintMichel-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=0c0db3e174588398ce45072b7ae0a095cb0a05c5 translatedAt=2026-09-21T02:54:39.540Z pushedAt=2026-09-22T01:29:30.417Z -->

The **hiTraceChain** module implements call chain trace throughout a service process. It provides functions such as starting and stopping call chain trace and configuring trace points.

When to use:
- Distributed cross-device business call chain tracing and analysis.
- Locating performance issues and analyzing bottlenecks.
- Debugging business processes and troubleshooting faults.
- Monitoring asynchronous call chains.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { hiTraceChain } from '@kit.PerformanceAnalysisKit';
```

## HiTraceFlag

Enumerates the combinations of trace flags. It is used to control the behavior mode of distributed tracing. For example, use the **INCLUDE_ASYNC** flag in business processes that require tracing asynchronous calls, use the **DONOT_CREATE_SPAN** flag in simple business processes that do not require detailed span information, and use the **TP_INFO** flag in scenarios that require debugging tracepoint information.

**System capability**: SystemCapability.HiviewDFX.HiTrace

| Name| Value| Description|
| -------- | -------- | -------- |
| DEFAULT           | 0      | Default flag.       |
| INCLUDE_ASYNC     | 1      | Asynchronous call flag.<br>When this flag is set, both synchronous and asynchronous calls are traced. By default, only synchronous calls are traced. |
| DONOT_CREATE_SPAN | 1 << 1 | No-span flag.<br>When this flag is set, no span information is created. By default, span information is created. |
| TP_INFO           | 1 << 2 | Tracepoint flag.<br>When this flag is set, calling [tracepoint()](#hitracechaintracepoint) prints tracepoint information to the hilog. By default, tracepoint information is not printed to the hilog. |
| NO_BE_INFO        | 1 << 3 | No begin/end information flag.<br>In debugging scenarios, when this flag is set, calling the begin trace API [begin()](#hitracechainbegin) and the end trace API [end()](#hitracechainend) prints begin and end trace information to the hilog respectively. By default, begin and end trace information is not printed to the hilog. |
| DISABLE_LOG       | 1 << 4 | Log correlation flag.<br>When this flag is set, **HiTraceId** information is not appended to the hilog. By default, **HiTraceId** information is appended to the hilog. |
| FAILURE_TRIGGER   | 1 << 5 | Failure trigger flag. This is a reserved flag.|
| D2D_TP_INFO       | 1 << 6 | Device-to-device tracepoint flag, a subset of **TP_INFO**, used in debugging scenarios.<br>When **TP_INFO** is already set, **D2D_TP_INFO** does not take effect.<br>When **TP_INFO** is not set, **D2D_TP_INFO** takes effect, and calling the information tracing point API [tracepoint()](#hitracechaintracepoint) prints tracepoint information to the hilog only when the mode parameter is **DEVICE**. |

## HiTraceTracepointType

Enumerates the tracepoint types. It is used to identify key nodes in a business process. For example, **CS** and **CR** mark the sending and receiving of a client request, **SS** and **SR** mark the receiving and sending of a server request, and **GENERAL** marks other key nodes that cannot be classified into the preceding four scenarios.

**System capability**: SystemCapability.HiviewDFX.HiTrace

| Name| Value| Description|
| -------- | -------- | -------- |
| CS       | 0 | Client Send.       |
| CR       | 1 | Client Receive.       |
| SS       | 2 | Server Send.       |
| SR       | 3 | Server Receive.       |
| GENERAL  | 4 | General type, which identifies the trace points except the CS, CR, SS, and SR trace points.|

## HiTraceCommunicationMode

Enumerates the trace communication modes. It is used to identify the level at which communication occurs. For example, **THREAD** marks inter-thread communication within the same application, **PROCESS** marks inter-process communication within the same device, and **DEVICE** marks cross-device distributed communication.

**System capability**: SystemCapability.HiviewDFX.HiTrace

| Name| Value| Description|
| -------- | -------- | -------- |
| DEFAULT  | 0 | Default communication.   |
| THREAD   | 1 | Inter-thread communication. |
| PROCESS  | 2 | Inter-process communication. |
| DEVICE   | 3 | Inter-device communication. |

## HiTraceId

This API is the **HiTraceId** object API. It is used to identify a unique node in a distributed trace chain. It is used in scenarios that require tracing business processes across threads, processes, and devices, such as e-commerce order placement, payment, and distributed service call chains.

**System capability**: SystemCapability.HiviewDFX.HiTrace

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| chainId      | bigint | No| No| Call chain ID.|
| spanId      | number | No| Yes| Span ID. The default value is **0**.|
| parentSpanId | number | No| Yes| Parent span ID. The default value is **0**.|
| flags        | number | No| Yes| Trace flag. The default value is **0**.|

## hiTraceChain.begin

begin(name: string, flags?: number): HiTraceId

Starts tracing. This is a synchronous API. It is used to start distributed tracing at the starting node of a business process, for example, when a user taps a button to initiate a request, when a server receives a request and starts processing, or when a background task is started.

> **NOTE**
>
> - If no valid **HiTraceId** exists in the TLS (Thread Local Storage) of the current thread, a valid **HiTraceId** is generated, set to the TLS of the current thread, and returned.
> - If a valid **HiTraceId** already exists in the TLS of the current thread, no new trace is started, and an invalid **HiTraceId** whose attribute values are all 0 is returned.
> - **begin()** must be used in pair with **end()**. After **begin()** is called, **end()** must be called to end the trace after the business logic is complete. Failure to call **end()** may prevent the trace chain from ending properly and affect the integrity of the trace data.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type| Mandatory| Description                                            |
| -------- | -------- | -------- |------------------------------------------------|
| name  | string | Yes | Trace business name.<br>The length of this parameter does not exceed 63 bytes; the excess part is truncated.    |
| flags | number | No | Trace flag combination. For details, see [HiTraceFlag](#hitraceflag). Set **INCLUDE_ASYNC** to trace asynchronous calls, set **DONOT_CREATE_SPAN** to not create span information, and set **TP_INFO** in debugging scenarios to print tracepoint information. The default value is **0**, which means tracing only synchronous calls, creating span information, and not printing logs. |

**Return value**

| Type| Description|
| -------- | -------- |
| [HiTraceId](#hitraceid) | **HiTraceId** instance in the TLS of the current thread. |

**Example**

```ts
// Start tracing. The trace flag is the union of INCLUDE_ASYNC and DONOT_CREATE_SPAN.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.INCLUDE_ASYNC | hiTraceChain.HiTraceFlag.DONOT_CREATE_SPAN);
// End the call chain trace after the service logic is executed for several times.
hiTraceChain.end(traceId);
```

## hiTraceChain.end

end(id: HiTraceId): void

Ends a trace. This is a synchronous API. It is used to terminate Distributed Tracing at the end node of a Business Process, for example, when request processing is complete and a result is returned, when a user operation flow ends, or when a background task is finished.
> **NOTE**
>
> - If the given **HiTraceId** is valid and equals the **HiTraceId** in the TLS of the current thread, the trace is ended and the **HiTraceId** in the TLS of the current thread is set to invalid. If the given **HiTraceId** is invalid or does not equal the **HiTraceId** in the TLS of the current thread, ending the trace fails and a hilog log indicating the failure to end the trace is printed.
> - **end()** must be used in pair with **begin()**, and the **HiTraceId** returned by **begin()** must be passed in to end the trace chain started by **begin()** and release related resources.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id | [HiTraceId](#hitraceid) | Yes| **HiTraceId** instance.|

**Example**

```ts
// Start tracing. The tracing flag is DEFAULT.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.DEFAULT);
// End the call chain trace after the service logic is executed for several times.
hiTraceChain.end(traceId);
```

## hiTraceChain.getId

getId(): HiTraceId

Obtains the trace identifier. This is a synchronous API. It is used in scenarios where the current trace identifier needs to be passed, for example, passing the trace identifier to a child thread, passing it to another process, or recording the current trace identifier in a log.
> **NOTE**
>
> - Obtains the **HiTraceId** in the TLS of the current thread. If no valid **HiTraceId** exists in the TLS of the current thread, an invalid **HiTraceId** whose attribute values are all 0 is returned.
> - This method should be used after **begin()** is called, to obtain the trace identifier between business logic operations in the same thread and then pass it.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Return value**

| Type| Description|
| -------- | -------- |
| [HiTraceId](#hitraceid) | **HiTraceId** instance in the TLS of the current thread. |

**Example**

```ts
// Start tracing. The tracing flag is DEFAULT.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.DEFAULT);
// After the service logic is executed for several times, obtain the current trace ID.
let curTraceId = hiTraceChain.getId();
// The call chain IDs in the trace IDs obtained from the same call chain trace must be the same.
if (curTraceId.chainId != traceId.chainId) {
// Processing logic for exceptions.
}
// End the call chain trace after the service logic is executed for several times.
hiTraceChain.end(traceId);
```

## hiTraceChain.setId

setId(id: HiTraceId): void

Sets a trace identifier. This is a synchronous API. It is used in scenarios where an external trace identifier needs to be set to the current thread, for example, inheriting a trace identifier from a parent thread, receiving a trace identifier from another process, or obtaining a trace identifier from inter-device communication.

> **NOTE**
>
> Set the given **HiTraceId** to the TLS of the current thread. If the given **HiTraceId** is invalid, no operation is performed.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id | [HiTraceId](#hitraceid) | Yes| **HiTraceId** instance.|

**Example**

```ts
// Obtain the trace ID of the current call chain.
let traceId = hiTraceChain.getId();
// Set traceId to the obtained trace ID.
hiTraceChain.setId(traceId);
```

## hiTraceChain.clearId

clearId(): void

Clears the trace identifier. This is a synchronous API. It is used in scenarios where the current trace chain needs to be cut off, for example, when a business logic branch no longer needs tracing, when the trace identifier is cleaned up after a task is complete, or when an old trace identifier is cleaned up before starting a new trace.

> **NOTE**
>
> Set the **HiTraceId** in the TLS of the current thread to invalid.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Example**

```ts
// Before the service starts, try to clear the trace ID.
hiTraceChain.clearId();
// Start tracing. The tracing flag is DEFAULT.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.DEFAULT);
// End the call chain trace after the service logic is executed for several times.
hiTraceChain.end(traceId);
```

## hiTraceChain.createSpan

createSpan(): HiTraceId

Creates a trace span. This is a synchronous API. It is used to mark important sub-processes in a business process, for example, key steps during request processing, various stages in a server-side processing chain, or business branches that require special attention.


> **NOTE**
>
> - Creates a **HiTraceId**, uses the **chainId** and **spanId** in the TLS of the current thread to initialize the **chainId** and **parentSpanId** of the **HiTraceId**, generates a new **spanId** for the **HiTraceId**, and returns the **HiTraceId**.
> - A valid **HiTraceId** must exist in the TLS of the current thread (that is, **begin()** has been called and **clearId()** has not been called). If no valid **HiTraceId** exists in the TLS of the current thread, an invalid **HiTraceId** whose attribute values are all 0 is returned.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Return value**

| Type| Description|
| -------- | -------- |
| [HiTraceId](#hitraceid) | **HiTraceId** instance.|

**Example**

```ts
// Start tracing. The tracing flag is DEFAULT.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.DEFAULT);
// Create a trace span after the service logic is executed for several times.
let spanTraceId = hiTraceChain.createSpan();
// The call chain IDs in the trace IDs obtained from the same call chain trace must be the same.
if (spanTraceId.chainId != traceId.chainId) {
// Processing logic for exceptions.
}
// Stop tracing after the service is complete.
hiTraceChain.end(traceId);
```

## hiTraceChain.tracepoint

tracepoint(mode: HiTraceCommunicationMode, type: HiTraceTracepointType, id: HiTraceId, msg?: string): void

Adds a trace point for the [@ohos.hiTraceMeter (Performance Tracing)](./js-apis-hitracemeter.md) logging, which is synchronous.

> **NOTE**
>
> This API works with the HiTraceMeter module. HiTraceChain manages the trace chain, while HiTraceMeter collects and counts performance data. When type is set to **CS** on the client side and **SR** is received on the server side, synchronous HiTraceMeter tracing starts. When type is set to **SS** on the server side and **CR** is received on the client side, synchronous HiTraceMeter tracing ends. The Information Tracing Points of **CS** and **CR**, as well as **SR** and **SS**, must be used in pairs. Otherwise, the start and end tracing points of HiTraceMeter cannot be matched properly. When type is set to the general type **GENERAL**, no HiTraceMeter tracing is performed.


**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| mode | [HiTraceCommunicationMode](#hitracecommunicationmode) | Yes | Communication mode of the trace that the information tracing point needs to specify, used to identify the communication scope where the tracing point occurs: **THREAD** indicates inter-thread communication, **PROCESS** indicates inter-process communication, and **DEVICE** indicates inter-device communication. |
| type | [HiTraceTracepointType](#hitracetracepointtype)| Yes| Trace point type.|
| id   | [HiTraceId](#hitraceid) | Yes| **HiTraceId** instance for trace point triggering.|
| msg  | string | No | Trace description information passed in the HiTraceMeter tracing operation, used to identify the tracing point location during performance analysis. Pass a meaningful description (such as a function name or operation step) when different tracing point locations need to be distinguished in the HiTraceMeter report. If not passed, an empty string is used, which does not affect the basic tracing function. The length of this parameter does not exceed 63 bytes, and the excess part is truncated. |

**Example**

```ts
// Start tracing. The trace flag is the union of INCLUDE_ASYNC and DONOT_CREATE_SPAN.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.INCLUDE_ASYNC | hiTraceChain.HiTraceFlag.DONOT_CREATE_SPAN);
// Trigger the trace point after the service logic is executed for several times.
hiTraceChain.tracepoint(hiTraceChain.HiTraceCommunicationMode.THREAD, hiTraceChain.HiTraceTracepointType.SS, traceId, "Just an example");
// Stop tracing after the service is complete.
hiTraceChain.end(traceId);
```

## hiTraceChain.isValid

isValid(id: HiTraceId): boolean

Checks whether a **HiTraceId** instance is valid. This API returns the result synchronously.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id  | [HiTraceId](#hitraceid) | Yes| **HiTraceId** instance.|

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | The value **true** indicates that **HiTraceId** is valid, and **false** indicates the opposite.|

**Example**

```ts
// Start tracing. The tracing flag is DEFAULT.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.DEFAULT);
// Set the value of traceIdIsvalid to true.
let traceIdIsvalid = hiTraceChain.isValid(traceId);
if (traceIdIsvalid) {
// Processing logic for the scenario where the validity check on the trace ID is successful.
}
// Stop tracing after the service is complete.
hiTraceChain.end(traceId);
```

## hiTraceChain.isFlagEnabled

isFlagEnabled(id: HiTraceId, flag: HiTraceFlag): boolean

Determines whether the **HiTraceId** has the specified trace flag enabled. This is a synchronous API. It is used to perform different processing in business logic based on the trace flag, for example, checking whether the **INCLUDE_ASYNC** flag is enabled to decide whether to wait for asynchronous operations to complete, or checking whether the **TP_INFO** flag is enabled to decide whether to print debug information.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id  | [HiTraceId](#hitraceid) | Yes| **HiTraceId** instance to be checked.|
| flag | [HiTraceFlag](#hitraceflag) | Yes| Specified trace flag.|

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | The value **true** indicates that the flag for **HiTraceId** is enabled, and **false** indicates the opposite.|

**Example**

```ts
// Start tracing. The tracing flag is INCLUDE_ASYNC.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.INCLUDE_ASYNC);
// Set the value of enabledIncludeAsyncFlag to true.
let enabledIncludeAsyncFlag = hiTraceChain.isFlagEnabled(traceId, hiTraceChain.HiTraceFlag.INCLUDE_ASYNC);
if (enabledIncludeAsyncFlag) {
// Processing logic for the scenario where the INCLUDE_ASYNC trace flag has been set.
}
// Stop tracing after the service is complete.
hiTraceChain.end(traceId);
```

## hiTraceChain.enableFlag

enableFlag(id: HiTraceId, flag: HiTraceFlag): void

Enables the specified trace flag in the **HiTraceId**. This is a synchronous API. It is used to dynamically adjust tracing behavior in a **Business Process**, for example, enabling the **TP_INFO** flag to print tracing point information during debugging, enabling the **INCLUDE_ASYNC** flag when asynchronous calls need to be traced, or enabling the **DISABLE_LOG** flag when log correlation needs to be disabled.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id  | [HiTraceId](#hitraceid) | Yes| **HiTraceId** instance for which the trace flag is enabled.|
| flag | [HiTraceFlag](#hitraceflag) | Yes| Specified trace flag.|

**Example**

```ts
// Start tracing. The tracing flag is INCLUDE_ASYNC.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.INCLUDE_ASYNC);
// Set the value of enabledDoNotCreateSpanFlag to false.
let enabledDoNotCreateSpanFlag = hiTraceChain.isFlagEnabled(traceId, hiTraceChain.HiTraceFlag.DONOT_CREATE_SPAN);
// Set the DONOT_CREATE_SPAN trace flag.
hiTraceChain.enableFlag(traceId, hiTraceChain.HiTraceFlag.DONOT_CREATE_SPAN);
// Set the value of enabledDoNotCreateSpanFlag to true.
enabledDoNotCreateSpanFlag = hiTraceChain.isFlagEnabled(traceId, hiTraceChain.HiTraceFlag.DONOT_CREATE_SPAN);
if (enabledDoNotCreateSpanFlag) {
// Processing logic for the scenario where the DONOT_CREATE_SPAN trace flag has been set.
}
// Stop tracing after the service is complete.
hiTraceChain.end(traceId);
```
