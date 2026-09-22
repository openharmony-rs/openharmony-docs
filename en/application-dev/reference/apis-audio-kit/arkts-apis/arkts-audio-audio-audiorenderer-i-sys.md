# AudioRenderer

```TypeScript
interface AudioRenderer
```

This interface provides APIs for audio rendering.

Before calling any API in AudioRenderer, you must use [createAudioRenderer](arkts-audio-audio-createaudiorenderer-f.md) to create an AudioRenderer instance.

> **NOTE:** 
> 
> - The initial APIs of this interface are supported since API version 8.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getTarget

```TypeScript
getTarget(): RenderTarget
```

Gets the currently render target of this audio renderer. If the render target has not been changed, the default value [PLAYBACK](arkts-audio-audio-rendertarget-e-sys.md#playback) will be returned. If the [setTarget](#settarget) has been called before calling this interface, ensure its promise object has been resolved successfully, otherwise, the obtained value may be inaccurate.

**Since:** 22

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [RenderTarget](arkts-audio-audio-rendertarget-e-sys.md) | Render target of this audio renderer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

**Examples**

```TypeScript
async function getTarget(){
  // (Optional) Set the injection mode.
  await audioRenderer.setTarget(audio.RenderTarget.INJECT_TO_VOICE_COMMUNICATION_CAPTURE);
  console.info('Succeeded in setting target.');

  // If the SetTarget API has been called before this API is called, ensure that the SetTarget API has been successfully called. Otherwise, the obtained value may be inaccurate.
  let renderTarget = audioRenderer.getTarget();
  console.info(`Succeeded in getting target, RenderTarget: ${renderTarget}.`);
}
```

## setTarget

```TypeScript
setTarget(target: RenderTarget): Promise<void>
```

Sets the render target of this audio renderer. This function can only be called when the audio renderer is not in the running or released state. Otherwise, it will return an error. The caller must have the ohos.permission.INJECT_PLAYBACK_TO_AUDIO_CAPTURE permission when target is not [PLAYBACK](arkts-audio-audio-rendertarget-e-sys.md#playback). After changing render target to non-PLAYBACK：

1. The audio route and interruption strategy of this renderer will not be affected by [AudioSessionManager](arkts-audio-audio-audiosessionmanager-i.md).
2. The device type of this renderer will be [SYSTEM_PRIVATE](arkts-audio-audio-devicetype-e.md#system_private).
3. Calling start when the audio scene is not [AUDIO_SCENE_VOICE_CHAT](arkts-audio-audio-audioscene-e.md#audio_scene_voice_chat) will
return error code 6800301.
4. Calling getAudioTime or getAudioTimeSync will return error code 6800301.
5. Calling getAudioTimestampInfo or getAudioTimestampInfoSync will return error code 6800301.
6. Calling setDefaultOutputDevice will return error code 6800301.

**Since:** 22

**Required permissions:** ohos.permission.INJECT_PLAYBACK_TO_AUDIO_CAPTURE

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [RenderTarget](arkts-audio-audio-rendertarget-e-sys.md) | Yes | Render target. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800103](../errorcode-audio.md#6800103-unsupported-state) | Operation not permit at running and release state. |
| [6800104](../errorcode-audio.md#6800104-unsupported-parameter-value) | Current renderer is not supported to set target. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioRenderer.setTarget(audio.RenderTarget.INJECT_TO_VOICE_COMMUNICATION_CAPTURE).then(() => {
  console.info('Succeeded in setting target.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set target. code: ${err.code}, message: ${err.message}`);
});
```

<a id="settarget-1"></a>

## setTarget

```TypeScript
setTarget(target: RenderTarget, targetParams?: AudioRendererTargetParams): Promise<void>
```

Sets the render target of this audio renderer. This function can only be called when the audio renderer is not in the running or released state. Otherwise, it will return an error. The caller must have the ohos.permission.INJECT_PLAYBACK_TO_AUDIO_CAPTURE permission when target is not [PLAYBACK](arkts-audio-audio-rendertarget-e-sys.md#playback). After changing render target to non-PLAYBACK:

1. The audio route and interruption strategy of this renderer will not be affected by
[AudioSessionManager](arkts-audio-audio-audiosessionmanager-i.md).
2. The device type of this renderer will be [SYSTEM_PRIVATE](arkts-audio-audio-devicetype-e.md#system_private).
3. Calling start when the audio scene is not [AUDIO_SCENE_VOICE_CHAT](arkts-audio-audio-audioscene-e.md#audio_scene_voice_chat) will
return error code 6800301.
4. Calling getAudioTime or getAudioTimeSync will return error code 6800301.
5. Calling getAudioTimestampInfo or getAudioTimestampInfoSync will return error code 6800301.
6. Calling setDefaultOutputDevice will return error code 6800301.

This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.INJECT_PLAYBACK_TO_AUDIO_CAPTURE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [RenderTarget](arkts-audio-audio-rendertarget-e-sys.md) | Yes | Render target. |
| targetParams | [AudioRendererTargetParams](arkts-audio-audio-audiorenderertargetparams-i-sys.md) | No | Parameter used to specify the target capturer stream into which the renderer stream is injected. If this parameter is not specified when target is not [PLAYBACK](arkts-audio-audio-rendertarget-e-sys.md#playback), the renderer stream is automatically injected into all voice communication capture streams by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800103](../errorcode-audio.md#6800103-unsupported-state) | Operation not permit at running and release state. |
| [6800104](../errorcode-audio.md#6800104-unsupported-parameter-value) | Current renderer is not supported to set target. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio server process died. |

**Examples**

See [setTarget](#settarget)
