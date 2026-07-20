# createParallelSoundPool（系统接口）

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

<a id="createparallelsoundpool"></a>
## createParallelSoundPool

```TypeScript
function createParallelSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo): Promise<SoundPool>
```

Creates a **SoundPool** instance. This API uses a promise to return the result.

If a **SoundPool** instance created using [createSoundPool](#createSoundPool) is used to play the same sound again, it stops the current audio and restarts the audio. However, if the instance is created using **createParallelSoundPool**, it keeps playing the first audio and starts the new one alongside it.

**起始版本：** 20

<!--Device-media-function createParallelSoundPool(maxStreams: int, audioRenderInfo: audio.AudioRendererInfo): Promise<SoundPool>--><!--Device-media-function createParallelSoundPool(maxStreams: int, audioRenderInfo: audio.AudioRendererInfo): Promise<SoundPool>-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxStreams | number | 是 | Maximum number of streams that can be played by the **SoundPool** instance.The value is an integer ranging from 1 to 32. |
| audioRenderInfo | audio.AudioRendererInfo | 是 | Audio renderer parameters. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SoundPool&gt; | Promise used to return the result. If the operation is successful, a **SoundPool** instance is returned; otherwise, **null** is returned. The instance is used for loading and playback. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API error. Return by promise. |

**示例：**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let soundPool: media.SoundPool;
let audioRendererInfo: audio.AudioRendererInfo = {
  usage : audio.StreamUsage.STREAM_USAGE_MUSIC,
  rendererFlags : 0
}

media.createParallelSoundPool(5, audioRendererInfo).then((soundpool_: media.SoundPool) => {
  if (soundpool_ != null) {
    soundPool = soundpool_;
    console.info('Succeeded in creating SoundPool');
  } else {
    console.error('Failed to create SoundPool');
  }
}, (error: BusinessError) => {
  console.error(`soundpool catchCallback, error message:${error.message}`);
});

```

