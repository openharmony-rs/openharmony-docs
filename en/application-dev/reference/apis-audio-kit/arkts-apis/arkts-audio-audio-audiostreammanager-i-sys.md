# AudioStreamManager (System API)

```TypeScript
interface AudioStreamManager
```

This interface implements audio stream management.

Before calling any API in AudioStreamManager, you must use [getStreamManager](arkts-audio-audio-audiomanager-i.md#getstreammanager) to obtain an AudioStreamManager instance.

> **NOTE:** 
> 
> - The initial APIs of this interface are supported since API version 9.

**Since:** 9

<!--Device-audio-interface AudioStreamManager--><!--Device-audio-interface AudioStreamManager-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getHighestPipeStreamInfo

```TypeScript
getHighestPipeStreamInfo(deviceDescriptor: AudioDeviceDescriptor, uid?: number): Promise<AudioStreamInfo | null>
```

Obtains information about the stream with the highest specification among streams routed to the specified device in the selected playback path.

> **NOTE:** 
> The returned format is the format of the path actually selected after system routing, which may differ from the
> format requested when creating stream. If **uid** is not specified, streams from all applications are
> queried. if no playback stream is routed to the specified device, **null** is returned. This may occur if the
> application has not created an **AudioRenderer** or the output device of the created **AudioRenderer** is not
> the passed device.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioStreamManager-getHighestPipeStreamInfo(deviceDescriptor: AudioDeviceDescriptor, uid?: int): Promise<AudioStreamInfo | null>--><!--Device-AudioStreamManager-getHighestPipeStreamInfo(deviceDescriptor: AudioDeviceDescriptor, uid?: int): Promise<AudioStreamInfo | null>-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | Audio device descriptor. |
| uid | number | No | ID of the application to query. This parameter is optional. The value must be an integer. If **uid** id not specified, stream information of all applications is queried. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md) &#124; null&gt; | Promise used to return the stream information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. Eusure that the specified AudioDeviceDescriptor is valid and the device exists. Ensure that the specified uid is valid. |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error. An unexpected error occurred in audio system. |
