# Audio Error Codes
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=59c3fabc0701f94b960b606856aa3cc084316830 translatedAt=2026-11-10T03:11:59.861Z pushedAt=2026-11-10T04:49:42.574Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 6800101 Invalid Parameter

**Error Message**

Invalid parameter.

**Description**

A parameter passed in the API is invalid.

**Possible Causes**

The parameter is invalid. For example, the parameter value is not within the range supported.

**Solution**

Pass the correct parameters in the API.

## 6800102 Memory Allocation Failure

**Error Message**

Memory allocation failed.

**Description**

When the API is called, the memory fails to be allocated or a null pointer occurs.

**Possible Causes**

1. The system does not have sufficient memory for mapping.
2. Invalid instances are not destroyed in time to release the memory.

**Solution**

1. Destroy the existing instances.
2. Create a new instance. If the creation fails, stop related operations.

## 6800103 Unsupported State

**Error Message**

Operation not permitted at current state.

**Description**

The current state of the object does not support this operation.

**Possible Causes**

The operation is not supported in the current state of the object, for example, attempting to play data without starting the stream.

**Solution**

1. Check whether this operation is supported in the current state.
2. Transition the object to the correct state before performing the operation.

## 6800104 Unsupported Parameter Value

**Error Message**

Unsupported option.

**Description**

The parameter value is not supported.

**Possible Causes**

The value of the input parameter is not within the range supported.

**Solution**

1. Confirm the enums or other input parameters supported by the current API.
2. Use a supported value.

## 6800105 Processing Timeout

**Error Message**

Timeout.

**Description**

The processing times out.

**Possible Causes**

1. An internal exception occurs in the system, triggering a timeout check of an internal interface.
2. The system relies on timely callback processing by the application. If the application fails to return promptly, the system reports a timeout.

**Solution**

1. For internal system timeouts, the application can only report the error.
2. For interface implementations that depend on timely callback processing by the application, the application should check the callback execution and ensure prompt returns to avoid disrupting subsequent system processes.

## 6800201 Too Many Audio Streams

**Error Message**

Too many audio streams.

**Description**

The number of audio streams reaches the upper limit.

**Possible Causes**

Excess audio streams are not released in a timely manner.

**Solution**

1. Release unused audio stream resources and retry.
2. If the system limit is reached due to other applications, report an error message to the user, asking them to close other applications.

## 6800301 System Error

**Error Message**

System error.

**Description**

The audio API fails to be processed due to a system processing exception. Different APIs return this error code for different reasons. You need to troubleshoot based on the failed API and system logs.

**Possible Causes**

1. System processing exceptions such as system service restart and cross-process call exceptions.
2. Exceptions in API parameter, application permission, or object state verification. For audio APIs added since API version 20, error code 6800301 does not carry this semantic information. For whether an API may involve this issue, refer to the error code description declared in the API documentation.
3. Failure to preempt the audio focus. Only audio stream start APIs that need to activate the audio focus (such as the [start](arkts-apis-audio-AudioRenderer.md#start8) API of AudioRenderer and the [start](arkts-apis-audio-AudioCapturer.md#start8) API of AudioCapturer) may return this error code due to failure to preempt the audio focus. Other APIs that do not involve focus activation will not return this error code for this reason.

**Solution**

1. Based on the API constraints and system logs for the returned error code `6800301`, refer to the common problem cases below to check the call parameters, application permissions, and service status, and rule out exceptions on the application side.
2. After ruling out exceptions on the application side, try to restore the service and avoid repeated retries in an abnormal state.

The following are common problem cases when the AudioCapturer service returns error code `6800301`.


### Failure to Create an AudioCapturer by Calling createAudioCapturer - Abnormal Audio Stream Type

When [createAudioCapturer](arkts-apis-audio-f.md#audiocreateaudiocapturer8) returns error code `6800301`, perform troubleshooting based on the system logs in the following scenarios.

**Basis for Judgment**

The application process log displays `Invalid sourceType`.

```text
<Application process name>: [CheckAndReportErrorEvent]Invalid sourceType -1!
```

The preceding log format is supported since API version 20.

**Possible Causes**

`AudioCapturerInfo.source` is not within the audio source types supported by the API.

**Solution**

Check the value of `source` based on [SourceType](arkts-apis-audio-e.md#sourcetype8).

### Failure to Create AudioCapturer by Calling createAudioCapturer - Audio Stream Parameter Exception

**Basis for Judgment**

Any of the following messages appears in the application process log:

```text
<Application process name>: [CheckCapturerAudioStreamInfo]Unsupported audio capturer parameter
<Application process name>: [IsRecordChannelRelatedInfoValid]AudioStream: Invalid source channel 0
<Application process name>: [IsRecordChannelRelatedInfoValid]AudioStream: Invalid source channel layout
<Application process name>: [IsRecordChannelRelatedInfoValid]AudioStream: not matched source channel and channel layout
```
The preceding log format is supported since API version 23.

**Possible Causes**

1. The value of `samplingRate`, `sampleFormat`, or `encodingType` is invalid. The `Unsupported audio capturer parameter` log cannot distinguish the specific field alone, and must be checked together with the application input parameters.
2. The value of `channels` or `channelLayout` is invalid.
3. `channels` does not match `channelLayout`.

**Solution**

1. Check the sampling rate, sample format, encoding type, number of channels, and channel layout based on [AudioStreamInfo](arkts-apis-audio-i.md#audiostreaminfo8).
2. Because the `channelLayout` parameter implicitly contains the number of channels, ensure that the number of channels in the channel layout matches the value of `channels`. When `channelLayout` is `CH_LAYOUT_UNKNOWN(0x0)`, it does not participate in the matching check. If an explicit channel layout is required, set the corresponding layout explicitly based on `channels`.

### Failure to Create an AudioCapturer by Calling createAudioCapturer - Microphone Not Authorized

When [createAudioCapturer](arkts-apis-audio-f.md#audiocreateaudiocapturer8) returns error code `6800301`, troubleshoot the following scenarios in sequence based on the system logs.

**Basis for Judgment**

The creation of an AudioCapturer using a Mic audio source (that is, [SourceType](arkts-apis-audio-e.md#sourcetype8) is `SOURCE_TYPE_MIC`, `SOURCE_TYPE_VOICE_RECOGNITION`, `SOURCE_TYPE_VOICE_COMMUNICATION`, `SOURCE_TYPE_VOICE_MESSAGE`, or `SOURCE_TYPE_LIVE`) fails, and the system log indicates that the microphone is not authorized. For the permission requirements of each audio source, see [Using AudioCapturer for Audio Recording](../../media/audio/using-audiocapturer-for-recording.md).

The system audio service process may output one or more of the following logs:

```text
audio_server: [VerifyClientPermission]Permission denied [...], [ohos.permission.MICROPHONE]
audio_server: [CheckRecorderPermission]Check record permission failed: No permission.
audio_server: [CreateAudioProcessInner]Create audio process failed, no permission
```

The `CheckRecorderPermission` and `CreateAudioProcessInner` logs are supported since API version 11; the `VerifyClientPermission` log is supported since API version 12.

**Possible Causes**

1. The application has not declared the `ohos.permission.MICROPHONE` permission.
2. The application has not requested microphone authorization from the user, or the user has denied the authorization.

**Solution**

1. Confirm that the application has declared the [ohos.permission.MICROPHONE](../../security/AccessToken/permissions-for-all-user.md#ohospermissionmicrophone) permission in `module.json5`.
2. Before creating an AudioCapturer, check whether the application has obtained microphone authorization. If not, complete the authorization request as described in [Requesting User Authorization](../../security/AccessToken/request-user-authorization.md).
3. If the user rejects the authorization request, do not create an AudioCapturer that uses the Mic audio source, and prompt the user in the application UI to grant the permission or stop the recording operation.

### Failure to Start AudioCapturer by Calling start - Abnormal AudioCapturer State

If the AudioCapturer is created successfully but calling [start](arkts-apis-audio-AudioCapturer.md#start8) returns error code `6800301`, troubleshoot the issue based on the system logs in the following scenarios.

**Basis for Judgment**

The system log indicates that the current state does not support starting.

The typical log of the application process is as follows:

```text
<Application process name>: [CheckStateAndReportErrorEvent]Start failed. Illegal state 2.
<Application process name>: [CheckStateAndReportErrorEvent]Start failed. Illegal state 4.
```

The preceding log format is supported since API version 18.

When the state value in the log is `2`, it indicates that the AudioCapturer is in the `STATE_RUNNING` state, which is usually caused by calling `start()` repeatedly. When the state value is `4`, it indicates that the AudioCapturer is in the `STATE_RELEASED` state, which is usually caused by calling `start()` again after the instance is released.

**Possible Causes**

The application may have repeated starts, calls after release, incomplete asynchronous state transitions, and so on.

**Solution**

1. Check [AudioState](arkts-apis-audio-e.md#audiostate8) before calling `start()`. Start capturing only when the AudioCapturer is in the `STATE_PREPARED`, `STATE_PAUSED`, or `STATE_STOPPED` state.
2. Listen for state changes through [on('stateChange')](arkts-apis-audio-AudioCapturer.md#onstatechange8) to avoid repeated starts and avoid further operations after the instance is released.
3. Call the APIs in the sequence of "create an instance -> register callbacks -> start recording -> stop recording -> release resources". For a complete state check, refer to the [complete example](../../media/audio/using-audiocapturer-for-recording.md#complete-sample-code) in *Audio Recording Development Using AudioCapturer*.

### Failure to Start AudioCapturer by Calling start - Failure to Activate Audio Focus

**Basis for Judgment**

The log indicates a failure to activate the audio focus.

The typical log of the application process is as follows:

```text
<Application process name>: [Start]ActivateAudioInterrupt Failed
```

The preceding log format is supported since API version 10.

**Possible Causes**

Other audio services such as recording and calls exist on the device at the same time, and the startup of the current stream is blocked by the focus policy.

**Solution**

Refer to [Recording Concurrency Policy](../../media/audio/audio-recording-concurrency.md) to check whether the current recording scenario allows concurrency with other audio services, and adjust the service startup timing or the recording stream type based on the concurrency policy.

### Failure to Start AudioCapturer by Calling start - Exception in Starting the Underlying Recording Stream

**Basis for Judgment**

If, after troubleshooting based on the cases of audio stream type exception, microphone not authorized, AudioCapturer state exception, and audio focus activation failure under error code 6800301 system processing exception, the application process still reports one or more of the following logs, a system-side exception may have occurred:

```text
<Application process name>: [StartAudioStream]Start call server failed: ...
<Application process name>: [StartImpl]Start audio stream failed
```

The `StartAudioStream` log is supported since API version 11; the `StartImpl` log is supported since API version 12.

**Possible Causes**

A system exception occurs in the underlying recording stream, audio service, or input device during the startup phase.

**Solution**

1. First, rule out object state, application permission, audio focus, and recording concurrency issues based on the preceding cases.
2. Stop and release the current AudioCapturer, recreate it, and retry once. Avoid retrying repeatedly without conditions.

### AudioSessionManager Fails to Process activateAudioSession/deactivateAudioSession/clearSelectedMediaInputDevice - System Exception

**Basis for Judgment**

Starting from API version 26.0.0, calling [activateAudioSession](../apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#activateaudiosession12), [deactivateAudioSession](../apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#deactivateaudiosession12), or [clearSelectedMediaInputDevice](../apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#clearselectedmediainputdevice21) returns error code `6800301`. When the corresponding API is called, the error message captured by the application is as follows:

- "System error. Activate audio session fail."
- "System error. Deactivate audio session fail."
- "System error. Clear selected input device fail."

**Possible Causes**

The system service is abnormal and unresponsive.

**Solution**

<!--RP1-->
Try again or [submit an issue](https://gitcode.com/openharmony/docs/issues/create/choose) for handling.
<!--RP1End-->