# Types
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=46feed4577bffdfe046a46315f0b167380ccfaa2 translatedAt=2026-09-01T12:50:17.368Z pushedAt=2026-09-07T07:57:52.747Z -->

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { avSession } from '@kit.AVSessionKit';
```

## AVSessionType<sup>10+</sup>

type AVSessionType = 'audio' | 'video' | 'voice_call' | 'video_call' | 'photo'

Defines the session type supported by the session.

You can use the strings listed in the following table.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

| Type | Description|
| -----  | ---- |
| 'audio' | Audio.|
| 'video' | Video.|
| 'voice_call'<sup>11+</sup> | Voice call.|
| 'video_call'<sup>12+</sup> | Video call.|
| 'photo'<sup>22+</sup> |  Image.|

## AVCastControlCommandType<sup>10+</sup>

type AVCastControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' |
  'seek' | 'setVolume' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'toggleMute'

Defines the commands that can be sent by a cast controller.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

| Type            | Description        |
| ---------------- | ------------ |
| 'play'           | Play the media. No parameter is required.|
| 'pause'          | Pause the playback. No parameter is required.  |
| 'stop'           | Stop the playback. No parameter is required.        |
| 'playNext'       | Play the next media asset. No parameter is required.      |
| 'playPrevious'   | Play the previous media asset. No parameter is required.      |
| 'fastForward'    | Fast forward. The corresponding parameter is of the number type, in milliseconds.       |
| 'rewind'         | Rewind. The corresponding parameter is of the number type, in milliseconds.        |
| 'seek'           | Seek to the specified time. The corresponding parameter is of the number type, in milliseconds. |
| 'setVolume'      | Set the volume. The corresponding parameter is of the number type. You can use [AVPlaybackState.maxVolume](arkts-apis-avsession-i.md#avplaybackstate10) to obtain the maximum system volume.    |
| 'setSpeed'       | Set the playback speed. In the audio and video casting scenario, when the remote device is connected using the DLNA protocol, this parameter cannot be set. The corresponding parameter is [media.PlaybackSpeed](../apis-media-kit/arkts-apis-media-e.md#playbackspeed8). |
| 'setLoopMode'    | Set the loop mode. The corresponding parameter is [LoopMode](arkts-apis-avsession-e.md#loopmode10).|
| 'toggleFavorite' | Switch to the favorite status. The corresponding parameter is [AVMetadata.assetId](arkts-apis-avsession-i.md#avmetadata10), which specifies the media asset ID. |
| 'toggleMute' | Switch to the mute status. No parameter is required.|

## ExtraInfo<sup>18+</sup>

type ExtraInfo = {[key: string]: Object;} 

Defines the custom media packet set by the provider.

**System capability:** SystemCapability.Multimedia.AVSession.Core

| Type                               | Description                         |
| ----------------------------------- | ----------------------------- |
|{[key: string]: Object;} |**key** specifies the remote distributed event type. Currently, the following event types are supported:<br>**AUDIO_GET_VOLUME**: obtains the volume of the remote device.<br>**AUDIO_GET_AVAILABLE_DEVICES**: obtains all available remote devices.<br>**AUDIO_GET_PREFERRED_OUTPUT_DEVICE_FOR_RENDERER_INFO**: obtains the actual remote audio device.<br>The provider returns the corresponding media packet object based on the event type. |

## KeyRequestCallback<sup>12+</sup>

type KeyRequestCallback = (assetId: string, requestData: Uint8Array) => void

Defines the callback invoked for the media key request event.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name| Type  | Mandatory| Description                                     |
| ------ | ------ | ---- | ----------------------------------------- |
| assetId     | string  | Yes   | Unique ID of a media asset. |
| requestData |  Uint8Array  | Yes  | Data carried in the media key request.                           |

**Example**
<!--code_no_check-->
```ts
let keyRequestCallback: avSession.KeyRequestCallback = async(assetId: string, requestData: Uint8Array) => {
  console.info(`Succeeded in keyRequestCallback. assetId: ${assetId}, requestData: ${requestData}`);
};
```

## AVControlCommandType<sup>10+</sup>

type AVControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' |
  'seek' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'playFromAssetId' | 'playWithAssetId' | 'answer' | 'hangUp' | 'toggleCallMute' | 'setTargetLoopMode'

Defines the commands that can be sent to a session.

The value of this type can be any of the following strings.

**System capability:** SystemCapability.Multimedia.AVSession.Core

| Type            | Description        |
| ---------------- | ------------ |
| 'play'           | Play the media. No parameter is required.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| 'pause'          | Pause the playback. No parameter is required.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| 'stop'           | Stop the playback. No parameter is required.<br>**Atomic service API**: This API can be used in atomic services since API version 12. |
| 'playNext'       | Play the next media asset. No parameter is required.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| 'playPrevious'   | Play the previous media asset. No parameter is required.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| 'fastForward'    | Fast-forward. For details about the corresponding parameters, see [SkipIntervals](arkts-apis-avsession-e.md#skipintervals11), which indicates the fast-forward skip interval.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| 'rewind'         | Rewind. For details about the corresponding parameters, see [SkipIntervals](arkts-apis-avsession-e.md#skipintervals11), which indicates the rewind skip interval.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| 'seek'           | Seek to the specified time. The corresponding parameter is of the number type, in milliseconds (ms).<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| 'setSpeed'       | Set the playback speed. The corresponding parameter is of the number type.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| 'setLoopMode'    | Set the loop mode. The corresponding parameter is [LoopMode](arkts-apis-avsession-e.md#loopmode10).<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| 'setTargetLoopMode' <sup>18+</sup>   | Set the target loop mode. The corresponding parameter is [LoopMode](arkts-apis-avsession-e.md#loopmode10).<br>**Atomic service API:** This API can be used in atomic services since API version 18. |
| 'toggleFavorite' | Switch to the favorite status. The corresponding parameter is [AVMetadata.assetId](arkts-apis-avsession-i.md#avmetadata10), which specifies the media asset ID.<br>**Atomic service API**: This API can be used in atomic services since API version 12.    |
| 'playFromAssetId' <sup>11+</sup>| Play the media asset with the specified asset ID.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| 'playWithAssetId' <sup>20+</sup>    | Play the media asset with the specified asset ID. The corresponding parameter is [AVMetadata.assetId](arkts-apis-avsession-i.md#avmetadata10). The string length of **assetId** must be less than 40,960 bytes.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| 'answer' <sup>11+</sup>        | Answer a call. No parameter is required.<br>**Atomic service API:** This API can be used in atomic services since API version 12.     |
| 'hangUp' <sup>11+</sup>         | The call is disconnecting. No parameter is required.<br>**Atomic service API:** This API can be used in atomic services since API version 12.     |
| 'toggleCallMute' <sup>11+</sup>  | Switch to the mute status of a call. No parameter is required.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|

## AVMediaCenterControlType

type AVMediaCenterControlType = 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite'

Defines control types of the media center.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

| Type            | Description        |
| ---------------- | ------------ |
| 'playNext'       | Play the next media asset.|
| 'playPrevious'   | Play the previous media asset.|
| 'fastForward'    | Fast-forward.|
| 'rewind'         | Rewind.|
| 'setSpeed'       | Set the playback speed.|
| 'setLoopMode'    | Set the loop mode.|
| 'toggleFavorite' | Favorite the media asset.|

## NoParamCallback<sup>22+</sup>

type NoParamCallback = () => void

Defines a callback function type that takes no parameters.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## TwoParamCallback<sup>22+</sup>

type TwoParamCallback\<T, G\> = (data1: T, data2: G) => void

Defines a callback type that takes two parameters.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type | Required | Description   |
|-------|----| ---- |------|
| data1 | T  | Yes   | First data parameter received by the callback function. The specific type and meaning are defined by the caller. |
| data2 | G  | Yes   | Second data parameter received by the callback function. The specific type and meaning are defined by the caller. |

## EventProcess

type EventProcess = (event: string, args: Record\<string, Object) => void

Defines a general function type for processing events and parameters.

**Since:** 26.1.0

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type| Mandatory| Description  |
|-------|----| ---- |------|
| event | string  | Yes   | Request event. |
| args | Record\<string, Object>  | Yes   | Parameters associated with the event. |
