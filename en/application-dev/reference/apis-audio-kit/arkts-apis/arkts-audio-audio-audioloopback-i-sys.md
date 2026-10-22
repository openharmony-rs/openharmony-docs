# AudioLoopback (System API)

```TypeScript
interface AudioLoopback
```

This interface provides APIs for audio monitoring.

Before calling any API in AudioLoopback, you must use [audio.createAudioLoopback](arkts-audio-audio-createaudioloopback-f.md#createaudioloopback-1) to create an AudioLoopback instance.

When audio loopback is enabled, the system creates a low-latency renderer and capturer to implement low-latency in- ear monitoring. The audio captured is routed back to the renderer through an internal path. The renderer follows the audio focus strategy for [STREAM_USAGE_MUSIC](arkts-audio-audio-streamusage-e.md), whereas the capturer follows the strategy for [SOURCE_TYPE_MIC](arkts-audio-audio-sourcetype-e.md).

The system automatically chooses the input and output devices. If these devices do not support low latency, audio loopback does not work. If another audio stream takes over the audio focus or if the input or output device changes to the one that does not support low latency, the system disables audio loopback automatically.

> **NOTE:** 
> 
> - The initial APIs of this interface are supported since API version 20.

**Since:** 20

<!--Device-audio-interface AudioLoopback--><!--Device-audio-interface AudioLoopback-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getAvailableStatus

```TypeScript
getAvailableStatus(): AudioLoopbackAvailableStatus
```

Obtains the global audio loopback available status. This feature applies only to the playback control application.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioLoopback-getAvailableStatus(): AudioLoopbackAvailableStatus--><!--Device-AudioLoopback-getAvailableStatus(): AudioLoopbackAvailableStatus-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| AudioLoopbackavailablestatus | The available status of global loopback. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

## offAvailableStatusChange

```TypeScript
offAvailableStatusChange(callback?: Callback<AudioLoopbackAvailableStatus>): void
```

Unsubscribes from the global audio loopback status change event. After you cancel the callback, the system does not trigger the callback. This feature applies only to the playback control application.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioLoopback-offAvailableStatusChange(callback?: Callback<AudioLoopbackAvailableStatus>): void--><!--Device-AudioLoopback-offAvailableStatusChange(callback?: Callback<AudioLoopbackAvailableStatus>): void-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioLoopbackAvailableStatus](arkts-audio-audio-audioloopbackavailablestatus-i-sys.md)&gt; | No | Callback to the canceled. <br>If the callback parameter is not transferred, all subscriptions are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

## onAvailableStatusChange

```TypeScript
onAvailableStatusChange(callback: Callback<AudioLoopbackAvailableStatus>): void
```

Subscribes to the global audio loopback available status change event. This feature applies only to the playback control application.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioLoopback-onAvailableStatusChange(callback: Callback<AudioLoopbackAvailableStatus>): void--><!--Device-AudioLoopback-onAvailableStatusChange(callback: Callback<AudioLoopbackAvailableStatus>): void-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioLoopbackAvailableStatus](arkts-audio-audio-audioloopbackavailablestatus-i-sys.md)&gt; | Yes | Callback function, which is used to return the audio loopback available status after the change. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
