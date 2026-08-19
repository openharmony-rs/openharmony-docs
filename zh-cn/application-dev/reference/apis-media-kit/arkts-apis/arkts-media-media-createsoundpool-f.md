# createSoundPool

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## createSoundPool

```TypeScript
function createSoundPool(
    maxStreams: number,
    audioRenderInfo: audio.AudioRendererInfo,
    callback: AsyncCallback<SoundPool>
  ): void
```

创建音频池实例。使用callback异步回调。 > **说明：** > > - API version 18以下版本，创建的SoundPool对象底层为单实例模式，一个应用进程只能够创建1个SoundPool实例。 > > - API version 18及API version 18以上版本，创建的SoundPool对象底层为多实例模式，一个应用进程最多能够创建128个SoundPool实例。

**起始版本：** 10

<!--Device-media-function createSoundPool(    maxStreams: number,    audioRenderInfo: audio.AudioRendererInfo,    callback: AsyncCallback<SoundPool>  ): void--><!--Device-media-function createSoundPool(    maxStreams: number,    audioRenderInfo: audio.AudioRendererInfo,    callback: AsyncCallback<SoundPool>  ): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxStreams | number | 是 | soundPool实例的最大播放的流数，设置范围为1-32的正整数。 |
| audioRenderInfo | audio.AudioRendererInfo | 是 | 音频播放参数信息。其中audioRenderInfo中的参数usage取值为STREAM_USAGE_UNKNOWN， STREAM_USAGE_MUSIC，STREAM_USAGE_MOVIE，STREAM_USAGE_AUDIOBOOK时，SoundPool播放短音时为混音模式，不会打断其他音频播放。SoundPool支持将 rendererFlags设置为1用于低时延通路播放。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;SoundPool&gt; | 是 | 回调函数。异步返回SoundPool实例，失败时返回null。用于音频池实例的加载播放功能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by callback. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';

let soundPool: media.SoundPool;
let audioRendererInfo: audio.AudioRendererInfo = {
  usage : audio.StreamUsage.STREAM_USAGE_MUSIC,
  rendererFlags : 0
};

media.createSoundPool(5, audioRendererInfo, (error, soundPool_: media.SoundPool) => {
  if (error) {
    console.error(`Failed to createSoundPool`);
    return;
  } else {
    soundPool = soundPool_;
    console.info(`Succeeded in createSoundPool`);
  }
});
```


## createSoundPool

```TypeScript
function createSoundPool(
    maxStreams: int,
    audioRenderInfo: audio.AudioRendererInfo,
    callback: AsyncCallback<SoundPool | undefined>
  ): void
```

Creates a **SoundPool** instance. This API uses an asynchronous callback to return the result. **NOTE：**- In versions earlier than API version 18, the bottom layer of the created **SoundPool** object is in singleton mode. Therefore, an application process can create only one **SoundPool** instance. - In API version 18 and later versions, the bottom layer of the created **SoundPool** object is in multiton mode. Therefore, an application process can create a maximum of 128 **SoundPool** instances.

**起始版本：** 23

<!--Device-media-function createSoundPool(    maxStreams: int,    audioRenderInfo: audio.AudioRendererInfo,    callback: AsyncCallback<SoundPool | undefined>  ): void--><!--Device-media-function createSoundPool(    maxStreams: int,    audioRenderInfo: audio.AudioRendererInfo,    callback: AsyncCallback<SoundPool | undefined>  ): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxStreams | int | 是 | Maximum number of streams that can be played by the **SoundPool** instance. The value is an integer ranging from 1 to 32. |
| audioRenderInfo | audio.AudioRendererInfo | 是 | Audio renderer parameters. When the **usage** parameter in **audioRenderInfo** is set to **STREAM_USAGE_UNKNOWN**, **STREAM_USAGE_MUSIC**, **STREAM_USAGE_MOVIE**, or **STREAM_USAGE_AUDIOBOOK**, the SoundPool uses the audio mixing mode when playing a short sound, without interrupting the playback of other audios. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;SoundPool \| undefined&gt; | 是 | Callback used to return the result. If the operation is successful, a **SoundPool** instance is returned; otherwise, **null** is returned. The instance is used for loading and playback. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by callback. |


## createSoundPool

```TypeScript
function createSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo): Promise<SoundPool>
```

创建音频池实例。使用Promise异步回调。 > **说明：** > > - API version 18以下版本，创建的SoundPool对象底层为单实例模式，一个应用进程只能够创建1个SoundPool实例。 > > - API version 18及API version 18以上版本，创建的SoundPool对象底层为多实例模式，一个应用进程最多能够创建128个SoundPool实例。

**起始版本：** 10

<!--Device-media-function createSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo): Promise<SoundPool>--><!--Device-media-function createSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo): Promise<SoundPool>-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxStreams | number | 是 | soundPool实例的最大播放的流数，设置范围为1-32的正整数。 |
| audioRenderInfo | audio.AudioRendererInfo | 是 | 音频播放参数信息 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SoundPool&gt; | Promise对象。异步返回SoundPool实例，失败时返回null。用于音频池实例的加载播放功能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let soundPool: media.SoundPool;
let audioRendererInfo: audio.AudioRendererInfo = {
  usage : audio.StreamUsage.STREAM_USAGE_MUSIC,
  rendererFlags : 0
};

media.createSoundPool(5, audioRendererInfo).then((soundpool_: media.SoundPool) => {
  if (soundpool_) {
    soundPool = soundpool_;
    console.info('Succeeded in creating SoundPool');
  } else {
    console.error('Failed to create SoundPool');
  }
}, (error: BusinessError) => {
  console.error(`soundpool catchCallback, error message:${error.message}`);
});
```


## createSoundPool

```TypeScript
function createSoundPool(maxStreams: int, audioRenderInfo: audio.AudioRendererInfo): Promise<SoundPool | undefined>
```

Creates a **SoundPool** instance. This API uses a promise to return the result. **NOTE：**- In versions earlier than API version 18, the bottom layer of the created **SoundPool** object is in singleton mode. Therefore, an application process can create only one **SoundPool** instance. - In API version 18 and later versions, the bottom layer of the created **SoundPool** object is in multiton mode. Therefore, an application process can create a maximum of 128 **SoundPool** instances.

**起始版本：** 23

<!--Device-media-function createSoundPool(maxStreams: int, audioRenderInfo: audio.AudioRendererInfo): Promise<SoundPool | undefined>--><!--Device-media-function createSoundPool(maxStreams: int, audioRenderInfo: audio.AudioRendererInfo): Promise<SoundPool | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxStreams | int | 是 | Maximum number of streams that can be played by the **SoundPool** instance. The value is an integer ranging from 1 to 32. |
| audioRenderInfo | audio.AudioRendererInfo | 是 | Audio renderer parameters. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SoundPool \| undefined&gt; | Promise used to return the result. If the operation is successful, a **SoundPool** instance is returned; otherwise, **null** is returned. The instance is used for loading and playback. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |

