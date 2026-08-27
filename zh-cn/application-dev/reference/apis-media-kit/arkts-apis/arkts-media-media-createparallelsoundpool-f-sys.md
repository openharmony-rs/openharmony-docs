# createParallelSoundPool（系统接口）

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## createParallelSoundPool

```TypeScript
function createParallelSoundPool(maxStreams: number, audioRenderInfo: audio.AudioRendererInfo): Promise<SoundPool>
```

创建音频池实例。使用Promise异步回调。使用[createSoundPool](arkts-media-media-createsoundpool-f.md)创建的音频池实例，在重复播放相同音频时，会停止之前的播放并重新开始；而使用 createParallelSoundPool创建的实例，在重复播放相同音频时，不会停止之前的音频，而是并行播放。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxStreams | number | 是 | soundPool实例的最大播放的流数，设置范围为1-32的正整数。 |
| audioRenderInfo | audio.AudioRendererInfo | 是 | 音频播放参数信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;SoundPool & gt; | Promise对象，返回SoundPool实例，失败时返回null。用于音频池实例的加载播放功能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API error. Return by promise. |

**示例**

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
