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
| INCLUDE_ASYNC     | 1      | Asynchronous call flag.<br>If this flag is set, both synchronous and asynchronous calls are traced. By default, only synchronous calls are traced.|
| DONOT_CREATE_SPAN | 1 << 1 | No span flag.<br>If this flag is set, branch information is not created. By default, branch information is created.|
| TP_INFO           | 1 << 2 | Trace point flag.<br>In the debugging scenario, if this flag is set, dotting information HiLog logs are printed when the dotting API tracepoint() is called. By default, dotting information HiLog logs are not printed.|
| NO_BE_INFO        | 1 << 3 | No start or end information flag.<br>In the debugging scenario, if this flag is set, the HiLog logs of the start and end tracing information will be printed when the start tracing API [begin()](#hitracechainbegin) and end tracing API [end()](#hitracechainend) are called. By default, the HiLog logs of the start and end tracing information are not printed.|
| DISABLE_LOG       | 1 << 4 | Log association flag.<br>If this flag is set, HiTraceId information will not be attached to HiLog logs. By default, HiTraceId information is attached to HiLog logs.|
| FAILURE_TRIGGER   | 1 << 5 | Failure trigger flag. This is a preset flag, which is not used currently.|
| D2D_TP_INFO       | 1 << 6 | Device-to-device trace point flag. Subset of TP_INFO, used in debugging scenarios.<br>If the TP_INFO flag has been set, the D2D_TP_INFO flag does not take effect.<br>If the TP_INFO flag is not set, the D2D_TP_INFO flag is set. In this case, the [tracepoint()](#hitracechaintracepoint) API is called. The tracepoint information is recorded in HiLog logs only when the mode parameter is set to DEVICE.|

## HiTraceTracepointType

Enumerates trace point types.

**System capability**: SystemCapability.HiviewDFX.HiTrace

| Name| Value| Description|
| -------- | -------- | -------- |
| CS       | 0 | CS trace point.      |
| CR       | 1 | CR trace point.      |
| SS       | 2 | SS trace point.      |
| SR       | 3 | SR trace point.      |
| GENERAL  | 4 | Common type, which indicates the tracing type other than CS, CR, SS, and SR.|

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
| flags        | number | No| Yes| Trace flag. The default value is 0.|

## hiTraceChain.begin

begin(name: string, flags?: number): HiTraceId

Starts call chain trace. This API returns the result synchronously.

If no valid HiTraceId exists in the thread local storage (TLS) of the current thread, a valid HiTraceId is generated and set to the TLS of the current thread. Then, the HiTraceId is returned.

If a valid HiTraceId already exists in the TLS of the current thread, tracing will not start, and an invalid HiTraceId with all attribute values being 0 is returned.

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

If the given HiTraceId is valid and is the same as the HiTraceId in the TLS of the current thread, the trace ends and the HiTraceId in the TLS of the current thread is set to invalid.

If the given HiTraceId is invalid or is not equal to the HiTraceId in the TLS of the current thread, the trace fails to be stopped, and a HiLog log is printed.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id | [HiTraceId](#hitraceid) | Yes| **HiTraceId** instance.|

**Example**

```ts
// Start tracing. The trace flag is DEFAULT.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.DEFAULT);
// End the call chain trace after the service logic is executed for several times.
hiTraceChain.end(traceId);
```

## hiTraceChain.getId

getId(): HiTraceId

Obtains the trace ID. This API returns the result synchronously.

Obtains the HiTraceId in the TLS of the current thread.

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

Sets the given HiTraceId to the TLS of the current thread. If the given HiTraceId is invalid, no operation is performed.

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

Sets the HiTraceId in the TLS of the current thread to invalid.

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

Specifically, create a **HiTraceId**, use the **chainId** and **spanId** in the Thread-Local Storage (TLS) of the current thread to initialize the **chainId** and **parentSpanId** of the **HiTraceId**, generate a new **spanId** for the **HiTraceId**, and return the **HiTraceId**.

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
// End tracing after the service is complete.
hiTraceChain.end(traceId);
```

## hiTraceChain.tracepoint

tracepoint(mode: HiTraceCommunicationMode, type: HiTraceTracepointType, id: HiTraceId, msg?: string): void

Adds a trace point for the [HiTraceMeter](./js-apis-hitracemeter.md) logging, which is synchronous.

When type is set to CS sent by the client and SC received by the server, the HiTraceMeter starts tracing. When type is set to CC received by the client and SS sent by the server, the HiTraceMeter ends tracing. When type is set to GENERAL, the HiTraceMeter does not trace.

When type is set to CS (client sending) and CC (client receiving), the information tracing points must be used together. When type is set to SC (server receiving) and SS (server sending), the information tracing points must be used together. Otherwise, the start and end logging of HiTraceMeter cannot be matched.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| mode | [HiTraceCommunicationMode](#hitracecommunicationmode) | Yes| Communication mode for the trace point.|
| type | [HiTraceTracepointType](#hitracetracepointtype)| Yes| Trace point type.|
| id   | [HiTraceId](#hitraceid) | Yes| **HiTraceId** instance for trace point triggering.|
| msg  | string | No| Trace description passed to the HiTraceMeter for tracing.|

**Example**

```ts
// Start tracing. The tracing flag is the union of INCLUDE_ASYNC and DONOT_CREATE_SPAN.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.INCLUDE_ASYNC | hiTraceChain.HiTraceFlag.DONOT_CREATE_SPAN);
// Trigger the trace point after the service logic is executed for several times.
hiTraceChain.tracepoint(hiTraceChain.HiTraceCommunicationMode.THREAD, hiTraceChain.HiTraceTracepointType.SS, traceId, "Just a example");
// Stop tracing when the service ends.
hiTraceChain.end(traceId);
```

## hiTraceChain.isValid

isValid(id: HiTraceId): boolean

Determines whether HiTraceId is valid. This is a synchronous API.

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
// Start tracing, and the trace flag is DEFAULT.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.DEFAULT);
// Set the value of traceIdIsvalid to true.
let traceIdIsvalid = hiTraceChain.isValid(traceId);
if (traceIdIsvalid) {
// Processing logic for the scenario where the validity check on the trace ID is successful.
}
// End tracing when the service ends.
hiTraceChain.end(traceId);
```

## hiTraceChain.isFlagEnabled

isFlagEnabled(id: HiTraceId, flag: HiTraceFlag): boolean

Checks whether the trace flag is enabled for a HiTraceId instance. This method is synchronous.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id  | [HiTraceId](#hitraceid) | Yes| HiTraceId instance whose specified trace flag needs to be checked.|
| flag | [HiTraceFlag](#hitraceflag) | Yes| Specified trace flag.|

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | true: HiTraceId is enabled. false: HiTraceId is disabled.|

**Example**

```ts
// Start tracing, and the trace flag is INCLUDE_ASYNC.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.INCLUDE_ASYNC);
// Set the value of enabledIncludeAsyncFlag to true.
let enabledIncludeAsyncFlag = hiTraceChain.isFlagEnabled(traceId, hiTraceChain.HiTraceFlag.INCLUDE_ASYNC);
if (enabledIncludeAsyncFlag) {
// Processing logic for the scenario where the INCLUDE_ASYNC trace flag has been set.
}
// Stop tracing when the service ends.
hiTraceChain.end(traceId);
```

## hiTraceChain.enableFlag

enableFlag(id: HiTraceId, flag: HiTraceFlag): void

Enables the tracing flag specified by HiTraceId. This is a synchronous API.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id  | [HiTraceId](#hitraceid) | Yes| HiTraceId instance for which the tracing flag is to be enabled.|
| flag | [HiTraceFlag](#hitraceflag) | Yes| Specified trace flag.|

**Example**

```ts
// Start tracing and set the trace flag to INCLUDE_ASYNC.
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
// Stop tracing when the service ends.
hiTraceChain.end(traceId);
```
