# @ohos.hiTraceChain (Distributed Tracing)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @qq_437963121-->
<!--Designer: @kutcherzhou1; @MontSaintMichel-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

The **hiTraceChain** module implements call chain trace throughout a service process. It provides functions such as starting and stopping call chain trace and configuring trace points.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { hiTraceChain } from '@kit.PerformanceAnalysisKit';
```

## HiTraceFlag

Enumerates trace flag types.

**System capability**: SystemCapability.HiviewDFX.HiTrace

| Name| Value| Description|
| -------- | -------- | -------- |
| DEFAULT           | 0      | Default flag.      |
| INCLUDE_ASYNC     | 1      | Asynchronous call flag.<br>When this flag is set, both synchronous and asynchronous calls are traced. By default, only synchronous calls are traced.|
| DONOT_CREATE_SPAN | 1 << 1 | No span flag.<br>When this flag is set, no span information is created. By default, span information is created.|
| TP_INFO           | 1 << 2 | Trace point flag.<br>When this flag is set in the debugging scenario, the HiLog logs of the trace point are printed upon calling the **[tracepoint()](#hitracechaintracepoint)** API. By default, the HiLog logs are not printed.|
| NO_BE_INFO        | 1 << 3 | No begin and end flag.<br>When this flag is set in the debugging scenario, the HiLog logs about the begin and end of tracing are printed when the [begin()](#hitracechainbegin) and [end()](#hitracechainend) APIs are called. By default, the HiLog logs about the begin and end of tracing are not printed.|
| DISABLE_LOG       | 1 << 4 | Log association flag.<br>When this flag is set, the **HiTraceId** information is not added to the HiLog logs. By default, the **HiTraceId** information is added to the HiLog logs.|
| FAILURE_TRIGGER   | 1 << 5 | Failure trigger flag. This is a reserved flag.|
| D2D_TP_INFO       | 1 << 6 | Device-to-device trace point flag. It is a subset of **TP_INFO** and is used in debugging scenarios.<br>When the **TP_INFO** flag is set, the **D2D_TP_INFO** flag does not take effect.<br>When **TP_INFO** is not set and **D2D_TP_INFO** is set, the HiLog logs of the trace point are printed only when the mode parameter is set to **DEVICE** upon calling [tracepoint()](#hitracechaintracepoint).|

## HiTraceTracepointType

Enumerates trace point types.

**System capability**: SystemCapability.HiviewDFX.HiTrace

| Name| Value| Description|
| -------- | -------- | -------- |
| CS       | 0 | CS trace point.      |
| CR       | 1 | CR trace point.      |
| SS       | 2 | SS trace point.      |
| SR       | 3 | SR trace point.      |
| GENERAL  | 4 | General type, which identifies the trace points except the CS, CR, SS, and SR trace points.|

## HiTraceCommunicationMode

Enumerates communication modes.

**System capability**: SystemCapability.HiviewDFX.HiTrace

| Name| Value| Description|
| -------- | -------- | -------- |
| DEFAULT  | 0 | Default communication.   |
| THREAD   | 1 | Inter-thread communication. |
| PROCESS  | 2 | Inter-process communication. |
| DEVICE   | 3 | Inter-device communication. |

## HiTraceId

Defines a **HiTraceId** object.

**System capability**: SystemCapability.HiviewDFX.HiTrace

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| chainId      | bigint | No| No| Call chain ID.|
| spanId      | number | No| Yes| Span ID. The default value is **0**.|
| parentSpanId | number | No| Yes| Parent span ID. The default value is **0**.|
| flags        | number | No| Yes| Trace flag. The default value is **0**.|

## hiTraceChain.begin

begin(name: string, flags?: number): HiTraceId

Starts call chain trace. This API returns the result synchronously.

If the current thread's TLS does not contain a valid HiTrace ID, this function generates one, stores it in TLS, and returns it.

If the current thread's TLS already contains a valid HiTrace ID, this function does not start tracing and returns an invalid HiTrace ID with all property values being 0.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name  | string | Yes| Traced service name.|
| flags | number | No| Trace flag combination. For details, see [HiTraceFlag](#hitraceflag). The default value is **0**.|

**Return value**

| Type| Description|
| -------- | -------- |
| [HiTraceId](#hitraceid) | **HiTraceId** instance.|

**Example**

```ts
// Start tracing. The trace flag is the union of INCLUDE_ASYNC and DONOT_CREATE_SPAN.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.INCLUDE_ASYNC | hiTraceChain.HiTraceFlag.DONOT_CREATE_SPAN);
// End the call chain trace after the service logic is executed for several times.
hiTraceChain.end(traceId);
```

## hiTraceChain.end

end(id: HiTraceId): void

Stops call chain trace. This API works in synchronous manner.

If the given HiTrace ID is valid and is the same as the HiTrace ID in the current thread's TLS, the tracing is stopped and the HiTrace ID in the current thread's TLS is set to invalid.

If the given HiTrace ID is invalid or is not the same as the HiTrace ID in the current thread's TLS, the tracing fails to be stopped, and a tracing stop failure log is printed.

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

Obtains the trace ID. This API returns the result synchronously.

Obtains the HiTrace ID in the TLS of the current thread.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Return value**

| Type| Description|
| -------- | -------- |
| [HiTraceId](#hitraceid) | **HiTraceId** instance.|

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

Sets a trace ID. This API returns the result synchronously.

Sets the given HiTrace ID to the TLS of the current thread. If the given HiTrace ID is invalid, no operation is performed.

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

Clears the trace ID. This API returns the result synchronously.

Clears the HiTrace ID in the current thread's TLS.

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

Creates a trace span. This API works in synchronous manner.

Specifically, create a **HiTraceId**, use the **chainId** and **spanId** in the TLS of the current thread to initialize the **chainId** and **parentSpanId** of the **HiTraceId**, generate a new **spanId** for the **HiTraceId**, and return the **HiTraceId**.

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

Adds a trace point for the [HiTraceMeter](./js-apis-hitracemeter.md) logging, which is synchronous.

When type is set to **CS** and **SC**, the HiTraceMeter tracing starts. When type is set to **CC** and **SS**, the HiTraceMeter tracing ends. When type is set to **GENERAL**, the HiTraceMeter tracing does not start.

The trace points for **CS** and **CC** types must be used as a pair; likewise, trace points for **SC** and **SS** types must also be used together. Otherwise, the start and end trace points of HiTraceMeter cannot match each other.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| mode | [HiTraceCommunicationMode](#hitracecommunicationmode) | Yes| Communication mode for the trace point.|
| type | [HiTraceTracepointType](#hitracetracepointtype)| Yes| Trace point type.|
| id   | [HiTraceId](#hitraceid) | Yes| **HiTraceId** instance for trace point triggering.|
| msg  | string | No| Trace description information passed by the HiTraceMeter logging.|

**Example**

```ts
// Start tracing. The trace flag is the union of INCLUDE_ASYNC and DONOT_CREATE_SPAN.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.INCLUDE_ASYNC | hiTraceChain.HiTraceFlag.DONOT_CREATE_SPAN);
// Trigger the trace point after the service logic is executed for several times.
hiTraceChain.tracepoint(hiTraceChain.HiTraceCommunicationMode.THREAD, hiTraceChain.HiTraceTracepointType.SS, traceId, "Just a example");
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

Checks whether the trace flag is enabled for **HiTraceId**. This API returns the result synchronously.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id  | [HiTraceId](#hitraceid) | Yes| **HiTraceId** instance to be check.|
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

Enables the trace flag specified in HiTraceId. This API returns the result synchronously.

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
