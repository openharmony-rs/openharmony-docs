# AudioRenderer

提供音频渲染的相关接口。

在使用AudioRenderer的接口之前，需先通过[createAudioRenderer](arkts-audio-audio-createaudiorenderer-f.md#createaudiorenderer)获取AudioRenderer实例。
> **说明：**  
>  
> - 本Interface首批接口从API version 8开始支持。

**起始版本：** 8

<!--Device-audio-interface AudioRenderer--><!--Device-audio-interface AudioRenderer-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getTarget

```TypeScript
getTarget(): RenderTarget
```

Gets the currently render target of this audio renderer.If the render target has not been changed, the default value {@link RenderTarget#PLAYBACK} will be returned.Ensure that the {@link setTarget} promise is resolved successfully before calling this interface,otherwise, the obtained value may be inaccurate.

**起始版本：** 22

<!--Device-AudioRenderer-getTarget(): RenderTarget--><!--Device-AudioRenderer-getTarget(): RenderTarget-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderTarget](arkts-audio-audio-rendertarget-e-sys.md) | Render target of this audio renderer. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例：**

```TypeScript
async function getTarget(){
  // 可选步骤：设置注入模式。
  await audioRenderer.setTarget(audio.RenderTarget.INJECT_TO_VOICE_COMMUNICATION_CAPTURE);
  console.info('Succeeded in setting target.');

  // 调用此接口前，若已经调用过SetTarget接口，请确保SetTarget接口已经设置成功，否则获取到的数值可能不准确。
  let renderTarget = audioRenderer.getTarget();
  console.info(`Succeeded in getting target, RenderTarget: ${renderTarget}.`);
}

```

## setTarget

```TypeScript
setTarget(target: RenderTarget): Promise<void>
```

Sets the render target of this audio renderer.This function can only be called when the audio renderer is not in the running or released state.Otherwise, it will return an error. The caller must have the ohos.permission.INJECT_PLAYBACK_TO_AUDIO_CAPTURE permission when target is not {@link RenderTarget#PLAYBACK}.This method can only be called when the audio renderer is ​​not​​ in the RUNNING or RELEASED state.Otherwise, an error will be returned.After changing render target to non-PLAYBACK：1. The audio route and interruption strategy of this renderer will not be affected by{@link AudioSessionManager}.2. The device type of this renderer will be {@link DeviceType#SYSTEM_PRIVATE}.3. Calling {@link start} when the audio scene is not {@link AudioScene#AUDIO_SCENE_VOICE_CHAT} will return error code 6800103.4. Calling {@link getAudioTime} or {@link getAudioTimeSync} will return error code 6800103.5. Calling {@link getAudioTimestampInfo} or {@link getAudioTimestampInfoSync} will return error code 6800103.6. Calling {@link setDefaultOutputDevice} will return error code 6800103.

**起始版本：** 22

**需要权限：** ohos.permission.INJECT_PLAYBACK_TO_AUDIO_CAPTURE

<!--Device-AudioRenderer-setTarget(target: RenderTarget): Promise<void>--><!--Device-AudioRenderer-setTarget(target: RenderTarget): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | [RenderTarget](arkts-audio-audio-rendertarget-e-sys.md) | 是 | Render target. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Operation not permit at running and release state. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Current renderer is not supported to set target. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, System error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioRenderer.setTarget(audio.RenderTarget.INJECT_TO_VOICE_COMMUNICATION_CAPTURE).then(() => {
  console.info('Succeeded in setting target.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set target. code: ${err.code}, message: ${err.message}`);
});

```

