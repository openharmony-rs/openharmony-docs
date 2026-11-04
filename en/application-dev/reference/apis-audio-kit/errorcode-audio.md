# Audio Error Codes
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=96c2f543d580d0d2b2dabb53953551af3ab0252e translatedAt=2026-11-03T04:34:49.392Z pushedAt=2026-11-04T03:11:47.067Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 6800101 Invalid Parameter

**Error Message**

Invalid parameter.

**Description**

A parameter passed to the API is invalid.

**Possible Causes**

Invalid parameter, for example, the value is out of range, or does not fall within the specified enumeration range.

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

1. Destroy the current instance.
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

1. An internal exception occurs in the system, triggering a timeout check of an internal API.
2. The system relies on timely callback processing by the application. If the application fails to return promptly, the system reports a timeout.

**Solution**

1. For internal system timeouts, the application can only report the error.
2. For API implementations that depend on timely callback processing by the application, the application should check the callback execution and ensure prompt returns to avoid disrupting subsequent system processes.

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

The audio API processing fails due to a system processing exception. Different APIs return this error code for different reasons, so troubleshooting must be performed based on the failed API and system logs.

**Possible cause**

1. System processing exceptions such as system service restart and cross-process call exceptions.
2. Exceptions in API parameter, application permission, or object status verification. For audio APIs added since API version 20, error code 6800301 does not include this semantic information. Whether an API may involve this issue is subject to the error code description declared in the API documentation.
3. Audio focus preemption failure. Only audio stream start APIs that need to activate audio focus (such as the [start](arkts-apis-audio-AudioRenderer.md#start8) API of AudioRenderer and the [start](arkts-apis-audio-AudioCapturer.md#start8) API of AudioCapturer) may return this error code due to audio focus preemption failure. Other APIs that do not involve focus activation will not return this error code for this reason.

**Handling steps**

1. Based on the API constraints and system logs for the API that returns error code `6800301`, refer to the common problem cases below to check the call parameters, application permissions, and service status, and rule out exceptions on the application side.
2. After ruling out exceptions on the application side, attempt to recover the service to avoid repeated retries in an abnormal state.

The following are common problem cases when the AudioCapturer service returns error code `6800301`.


### Failure to Create AudioCapturer by Calling createAudioCapturer - Abnormal Audio Stream Type

When [createAudioCapturer](arkts-apis-audio-f.md#audiocreateaudiocapturer8) returns error code `6800301`, troubleshoot based on the system logs in the following scenarios.

**Criteria**

The application process log indicates `Invalid sourceType`.

```text
<application process name>: [CheckAndReportErrorEvent]Invalid sourceType -1!
```

The preceding log format support starts from API version 20.

**Possible cause**

`AudioCapturerInfo.source` is not within the range of audio source types supported by the API.

**Handling steps**

Check the value of `source` based on [SourceType](arkts-apis-audio-e.md#sourcetype8).

### Failure to Create AudioCapturer by Calling createAudioCapturer - Abnormal Audio Stream Parameters

**Criteria**

The application process log contains any of the following messages:

```text
<application process name>: [CheckCapturerAudioStreamInfo]Unsupported audio capturer parameter
<application process name>: [IsRecordChannelRelatedInfoValid]AudioStream: Invalid source channel 0
<application process name>: [IsRecordChannelRelatedInfoValid]AudioStream: Invalid source channel layout
<application process name>: [IsRecordChannelRelatedInfoValid]AudioStream: not matched source channel and channel layout
```
Support for the preceding log format starts from API version 23.

**Possible cause**

1. The value of `samplingRate`, `sampleFormat`, or `encodingType` is invalid. The `Unsupported audio capturer parameter` log cannot distinguish the specific field alone, and needs to be checked together with the application input parameters.
2. The value of `channels` or `channelLayout` is invalid.
3. `channels` does not match `channelLayout`.

**Handling steps**

1. Check the sampling rate, sample format, encoding type, number of channels, and channel layout based on [AudioStreamInfo](arkts-apis-audio-i.md#audiostreaminfo8).
2. Because the `channelLayout` parameter implicitly contains channel count information, ensure that the channel count in the channel layout matches the value of `channels`. When `channelLayout` is `CH_LAYOUT_UNKNOWN(0x0)`, it does not participate in the matching check. If an explicit channel layout is required, set the corresponding layout explicitly based on `channels`.

### Failure to Create AudioCapturer by Calling createAudioCapturer - Microphone Not Authorized

When [createAudioCapturer](arkts-apis-audio-f.md#audiocreateaudiocapturer8) returns error code `6800301`, troubleshoot the following scenarios in sequence based on the system logs.

**Criteria**

The creation of AudioCapturer using a Mic audio source (that is, [SourceType](arkts-apis-audio-e.md#sourcetype8) being `SOURCE_TYPE_MIC`, `SOURCE_TYPE_VOICE_RECOGNITION`, `SOURCE_TYPE_VOICE_COMMUNICATION`, `SOURCE_TYPE_VOICE_MESSAGE`, or `SOURCE_TYPE_LIVE`) fails, and the system log indicates that the microphone is not authorized. For the permission requirements of each audio source, see [Using AudioCapturer for Audio Recording](../../media/audio/using-audiocapturer-for-recording.md).

The system audio service process may output one or more of the following logs:

```text
audio_server: [VerifyClientPermission]Permission denied [...], [ohos.permission.MICROPHONE]
audio_server: [CheckRecorderPermission]Check record permission failed: No permission.
audio_server: [CreateAudioProcessInner]Create audio process failed, no permission
```

The `CheckRecorderPermission` and `CreateAudioProcessInner` logs are supported since API version 11; the `VerifyClientPermission` log is supported since API version 12.

**Possible cause**

1. The application has not declared the `ohos.permission.MICROPHONE` permission.
2. The application has not requested microphone authorization from the user, or the user has denied the authorization.

**Handling steps**

1. Confirm that the application has declared the [ohos.permission.MICROPHONE](../../security/AccessToken/permissions-for-all-user.md#ohospermissionmicrophone) permission in `module.json5`.
2. Before creating an AudioCapturer, check whether the application has obtained microphone authorization. If not authorized, complete the authorization request as described in [Requesting User Authorization](../../security/AccessToken/request-user-authorization.md).
3. If the user denies authorization, do not create an AudioCapturer that uses the Mic audio source, and prompt the user in the application UI to grant authorization or stop the recording operation.

### Failure to Start AudioCapturer by Calling start - Abnormal AudioCapturer State

When AudioCapturer is created successfully but calling [start](arkts-apis-audio-AudioCapturer.md#start8) returns error code `6800301`, troubleshoot based on the system log according to the following scenarios.

**Criteria**

The system log indicates that the current status does not support starting.

The typical log of the application process is as follows:

```text
<application process name>: [CheckStateAndReportErrorEvent]Start failed. Illegal state 2.
<application process name>: [CheckStateAndReportErrorEvent]Start failed. Illegal state 4.
```

Support for the preceding log format starts from API version 18.

When the status value in the log is `2`, it indicates that AudioCapturer is in the `STATE_RUNNING` state, which is usually caused by repeated calls to `start()`. When the status value is `4`, it indicates that AudioCapturer is in the `STATE_RELEASED` state, which is usually caused by continuing to call `start()` after the instance is released.

**Possible cause**

The application may have repeated starts, calls after release, incomplete asynchronous state transitions, and other situations.

**Handling steps**

1. Before calling `start()`, check [AudioState](arkts-apis-audio-e.md#audiostate8). Start capture only when the AudioCapturer is in the `STATE_PREPARED`, `STATE_PAUSED`, or `STATE_STOPPED` state.
2. Listen for state changes through [on('stateChange')](arkts-apis-audio-AudioCapturer.md#onstatechange8) to avoid starting capture repeatedly and to avoid further operations after the instance is released.
3. Call the APIs in the order of "create an instance -> register callbacks -> start recording -> stop recording -> release resources". For a complete state check, refer to the [complete example](../../media/audio/using-audiocapturer-for-recording.md#complete-sample-code) in *Using AudioCapturer for Audio Recording*.

### Failure to Start AudioCapturer by Calling start - Failure to Activate Audio Focus

**Criteria**

The log indicates a failure to activate the audio focus.

The typical log of the application process is as follows:

```text
<application process name>: [Start]ActivateAudioInterrupt Failed
```

The preceding log format is supported since API version 10.

**Possible cause**

Other audio services such as recording and calls exist on the device at the same time, and the current stream startup is blocked by the focus policy.

**Handling steps**

Refer to [Recording Concurrency Policy](../../media/audio/audio-recording-concurrency.md) to check whether the current recording scenario allows concurrency with other audio services, and adjust the service startup timing or the recording stream type based on the concurrency policy.

### Failure to Start AudioCapturer by Calling start - Underlying Recording Stream Startup Exception

**Criteria**

If, after troubleshooting the cases under 6800301 system processing exception, such as audio stream type exception, microphone not authorized, AudioCapturer status exception, and failure to activate audio focus, the application process still produces one or more of the following logs, a system-side exception may have occurred:

```text
<application process name>: [StartAudioStream]Start call server failed: ...
<application process name>: [StartImpl]Start audio stream failed
```

The `StartAudioStream` log is supported from API version 11; the `StartImpl` log is supported from API version 12.

**Possible cause**

A system exception occurs in the underlying recording stream, audio service, or input device during the startup phase.

**Handling steps**

1. First, rule out object status, application permission, audio focus, and recording concurrency issues based on the preceding cases.
2. Stop and release the current AudioCapturer, recreate it, and retry once. Avoid unconditional repeated retries.

### AudioSessionManager Fails to Process activateAudioSession/deactivateAudioSession/clearSelectedMediaInputDevice - System Exception

**Criteria**

Starting from API version 26.0.0, calling [activateAudioSession](../apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#activateaudiosession12), [deactivateAudioSession](../apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#deactivateaudiosession12), and [clearSelectedMediaInputDevice](../apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#clearselectedmediainputdevice21) returns error code `6800301`. When the corresponding API is called, the error messages captured by the application are as follows:

- "System error. Activate audio session fail."
- "System error. Deactivate audio session fail."
- "System error. Clear selected input device fail."

**Possible cause**

The system service is abnormal and unresponsive.

**Handling steps**

<!--RP1-->
Try again or [submit an issue](https://gitcode.com/openharmony/docs/issues/create/choose) to handle it.
<!--RP1End-->

## 6800302 System Service Process Terminated

**Error message**

System service process terminated.

**Error description**

The system service process is terminated.

**Possible cause**

1. A crash occurs in the internal running of the audio system service.
2. A key thread inside the audio system service becomes unresponsive, triggering a restart for self-recovery.

**Handling steps**

This is a system internal error unrelated to application usage. The available steps are as follows:
1. Prompt the user that a system error has occurred and that they can retry the operation.
2. If the error persists after repeated retries, exit and clear the application from the background, then re-enter the application and retry.
3. If the error still cannot be recovered, the user can restart the device to attempt recovery.
4. Collect information related to the system error and submit it to the system side for analysis and handling.

## 6800501 Network Conditions Not Met

**Error message**

Required network conditions not met.

**Error description**

The network conditions do not meet the API requirements.

**Possible cause**

The current network environment of the user is inconsistent with the network environment required by the API. For example, the API requires a network connection but the device is not connected to a network, or the API requires a Wi-Fi network but the device is not connected to an available Wi-Fi network.

**Handling steps**

1. Check the network connection status of the device and confirm whether it is connected to an available network.
2. If the API has requirements on the network type (for example, a Wi-Fi network is required), confirm whether the current network type of the device meets the requirement.
3. Guide the user to connect to a network that meets the requirements and retry.

## 6800502 Insufficient Storage Space

**Error Message**

Insufficient storage space.

**Error Description**

The device storage space is insufficient.

**Possible Causes**

The device storage space does not meet the storage size required by the current API.

**Solution**

1. Check whether the available storage space of the device meets the API requirements.
2. Guide the user to clear the device storage space and try again.