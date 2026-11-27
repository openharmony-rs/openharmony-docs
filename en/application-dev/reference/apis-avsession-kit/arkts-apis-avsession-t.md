# Types
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_7KSyM10J; @devil_red-->
<!--Designer: @gcw_7KSyM10J-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=b1fd8b3f51834f9eb9230d7ab9fdd9c5dc437803 translatedAt=2026-11-18T03:20:25.575Z pushedAt=2026-11-19T11:31:39.552Z nl=1 -->

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
| 'audio' | Audio session.|
| 'video' | Video session.|
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
| 'fastForward'    | Fast-forward. The parameter is of the number type, in milliseconds.      |
| 'rewind'         | Rewind. The parameter is of the number type, in milliseconds.       |
| 'seek'           | Seek to the specified time. The parameter is of the number type, in milliseconds.|
| 'setVolume'      | Set the volume. The parameter is of the number type. You can use [AVPlaybackState.maxVolume](arkts-apis-avsession-i.md#avplaybackstate10) to obtain the maximum system volume.    |
| 'setSpeed'       | Set the playback speed. In the audio and video casting scenario, when the remote device is connected using the DLNA protocol, this parameter cannot be set. The corresponding parameter is [media.PlaybackSpeed](../apis-media-kit/arkts-apis-media-e.md#playbackspeed8).|
| 'setLoopMode'    | Set the loop mode. The corresponding parameter is [LoopMode](arkts-apis-avsession-e.md#loopmode10).|
| 'toggleFavorite' | Switch to the favorite status. The corresponding parameter is [AVMetadata.assetId](arkts-apis-avsession-i.md#avmetadata10), which specifies the media asset ID.|
| 'toggleMute' | Switch to the mute status. No parameter is required.|

## ExtraInfo<sup>18+</sup>

type ExtraInfo = {[key: string]: Object;} 

Defines a custom media data packet object set by the media provider. Starting from API version 26.0.1, in the cockpit cold start scenario, it is used to pass cold start extension information.

**System capability:** SystemCapability.Multimedia.AVSession.Core

| Type                               | Description                         |
| ----------------------------------- | ----------------------------- |
|{[key: string]: Object;} | **key** is the remote distributed event type. The currently supported event types are as follows:<br>**AUDIO_GET_VOLUME**: Gets the volume of the remote device.<br>**AUDIO_GET_AVAILABLE_DEVICES**: Gets all available devices on the remote device.<br>**AUDIO_GET_PREFERRED_OUTPUT_DEVICE_FOR_RENDERER_INFO**: Gets the actual sound output device on the remote device.<br>The media provider returns the corresponding media data packet object based on different remote distributed event types.<br>Since API version 26.0.1, in the cockpit cold start scenario, **ExtraInfo** supports the following fields:<br>**controlCommand**: Control command, including: **play**: Play. **playNext**: Next. **playPrevious**: Previous.<br>**isPlayList**: Whether to use the **PlayMusicList** intent to implement playback. **1**: yes, other values: no. |

## KeyRequestCallback<sup>12+</sup>

type KeyRequestCallback = (assetId: string, requestData: Uint8Array) => void

Defines the callback invoked for the media key request event.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name| Type  | Mandatory| Description                                     |
| ------ | ------ | ---- | ----------------------------------------- |
| assetId     | string  | Yes  | Unique ID of a media asset.|
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
| 'stop'           | Stop the playback. No parameter is required.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| 'playNext'       | Play the next media asset. No parameter is required.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| 'playPrevious'   | Play the previous media asset. No parameter is required.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| 'fastForward'    | Fast-forward. For details about the corresponding parameters, see [SkipIntervals](arkts-apis-avsession-e.md#skipintervals11), which indicates the fast-forward skip interval.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| 'rewind'         | Rewind. For details about the corresponding parameters, see [SkipIntervals](arkts-apis-avsession-e.md#skipintervals11), which indicates the rewind skip interval.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| 'seek'           | Seek to the specified time. The corresponding parameter is of the number type, in milliseconds.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| 'setSpeed'       | Set the playback speed. The corresponding parameter is of the number type.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| 'setLoopMode'    | Set the loop mode. The corresponding parameter is [LoopMode](arkts-apis-avsession-e.md#loopmode10).<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| 'setTargetLoopMode' <sup>18+</sup>   | Set the target loop mode. The corresponding parameter is [LoopMode](arkts-apis-avsession-e.md#loopmode10).<br>**Atomic service API:** This API can be used in atomic services since API version 18. |
| 'toggleFavorite' | Switch to the favorite status. The corresponding parameter is [AVMetadata.assetId](arkts-apis-avsession-i.md#avmetadata10), which specifies the media asset ID.<br>**Atomic service API:** This API can be used in atomic services since API version 12.   |
| 'playFromAssetId' <sup>11+</sup>| Play the media asset with the specified asset ID.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| 'playWithAssetId' <sup>20+</sup>    | Play the media asset with the specified asset ID. The corresponding parameter is [AVMetadata.assetId](arkts-apis-avsession-i.md#avmetadata10).<br>The string length of **assetId** must be less than 40,960 bytes.<br>**Atomic service API:** This API can be used in atomic services since API version 20.|
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

| Name  | Type| Mandatory| Description  |
|-------|----| ---- |------|
| data1 | T  | Yes  | First data parameter received by the callback function. The specific type and meaning are defined by the caller.|
| data2 | G  | Yes  | Second data parameter received by the callback function. The specific type and meaning are defined by the caller.|

## EventProcess

type EventProcess = (event: string, args: Record\<string, Object>) => void

Defines a general function type for processing events and parameters.

**Since:** 26.0.1

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type | Mandatory | Description  |
|-------|----| ---- |------|
| event | string  | Yes   | Request event. |
| args | Record\<string, Object>  | Yes   | Parameters associated with the event. |