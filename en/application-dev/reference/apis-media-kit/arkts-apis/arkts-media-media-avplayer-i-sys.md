# AVPlayer

AVPlayer is a playback management class. It provides APIs to manage and play media assets. Before calling any API in AVPlayer, you must use [createAVPlayer()](arkts-media-media-createavplayer-f.md) to create an AVPlayer instance.

When using the AVPlayer instance, you are advised to register the following callbacks to proactively obtain status changes: [on('stateChange')](arkts-media-media-avplayer-i.md#onstatechange): listens for AVPlayer state changes. [on('error')](arkts-media-media-avplayer-i.md#onerror): listens for error events.

Applications must properly manage AVPlayer instances according to their specific needs, creating and freeing them when necessary. Holding too many AVPlayer instances can lead to high memory usage, and in some cases, the system might terminate applications to free up resources.

For details about the audio and video playback demo, see [Audio Playback](../../../media/media/using-avplayer-for-playback.md) and [Video Playback](../../../media/media/video-playback.md).

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## enableCameraPostprocessing

```TypeScript
enableCameraPostprocessing(): Promise<void>
```

Enable the post-processing function of Camera for video playback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called from Non-System applications. Return by promise. |

## forceLoadVideo

```TypeScript
forceLoadVideo(force: boolean): Promise<void>
```

Specifies whether to forcibly load the video. This API can be called only when the AVPlayer is in the prepared, playing, or paused state. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| force | boolean | Yes | specified whether to forcibly load the video. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return when forceLoadVideo completed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called from Non-System applications. Return by promise. |

## enableStartFrameRateOpt

```TypeScript
enableStartFrameRateOpt?: boolean
```

Whether a slower synchronization policy is used at the start of playback to reduce subjective image jitter caused by insufficient frame rate. Default value: false, means that the slower synchronization policy will not be used.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**System API:** This is a system API.
