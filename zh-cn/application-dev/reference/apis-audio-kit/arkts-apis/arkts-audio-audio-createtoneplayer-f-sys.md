# createTonePlayer（系统接口）

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## createTonePlayer

```TypeScript
function createTonePlayer(options: AudioRendererInfo, callback: AsyncCallback<TonePlayer>): void
```

Obtains a {@link TonePlayer} instance. This method uses an asynchronous callback to return the renderer instance.

**起始版本：** 9

<!--Device-audio-function createTonePlayer(options: AudioRendererInfo, callback: AsyncCallback<TonePlayer>): void--><!--Device-audio-function createTonePlayer(options: AudioRendererInfo, callback: AsyncCallback<TonePlayer>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Tone

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md) | 是 | Tone playing attribute. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;TonePlayer&gt; | 是 | Callback used to return the tonePlayer instance. |

**示例：**

```TypeScript
import { audio } from '@kit.AudioKit';

let audioRendererInfo: audio.AudioRendererInfo = {
  usage : audio.StreamUsage.STREAM_USAGE_DTMF,
  rendererFlags : 0
};
let tonePlayer: audio.TonePlayer;

audio.createTonePlayer(audioRendererInfo, (err, data) => {
  console.info(`callback call createTonePlayer: audioRendererInfo: ${audioRendererInfo}`);
  if (err) {
    console.error(`callback call createTonePlayer return error: ${err.message}`);
  } else {
    console.info(`callback call createTonePlayer return data: ${data}`);
    tonePlayer = data;
  }
});

```


## createTonePlayer

```TypeScript
function createTonePlayer(options: AudioRendererInfo): Promise<TonePlayer>
```

Obtains a {@link TonePlayer} instance. This method uses a promise to return the renderer instance.

**起始版本：** 9

<!--Device-audio-function createTonePlayer(options: AudioRendererInfo): Promise<TonePlayer>--><!--Device-audio-function createTonePlayer(options: AudioRendererInfo): Promise<TonePlayer>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Tone

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md) | 是 | Tone playing attribute. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;TonePlayer&gt; | Promise used to return the tonePlayer instance. |

**示例：**

```TypeScript
import { audio } from '@kit.AudioKit';

let tonePlayer: audio.TonePlayer;
async function createTonePlayerBefore(){
  let audioRendererInfo: audio.AudioRendererInfo = {
    usage : audio.StreamUsage.STREAM_USAGE_DTMF,
    rendererFlags : 0
  };
  tonePlayer = await audio.createTonePlayer(audioRendererInfo);
}

```

