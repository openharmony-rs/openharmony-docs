# AVRecorderProfile

音视频录制配置参数。

## 音频参数配置对照表

此处提供音频参数配置的对照表，每项的具体释义，可查看下述字段解释。

|编码格式|封装格式|采样率|比特率|声道数|  
|----|----|----|----|----|  
| [AUDIO_AAC](arkts-media-media-codecmimetype-e.md) |MP4,M4A|[8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000, 64000, 88200, 96000]|[32000-500000]|[1-2]|
| [AUDIO_MP3](arkts-media-media-codecmimetype-e.md) | [MP3](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md) |[8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000]|<br>- 采样率使用16000以下时，对应比特率范围为[8000, 16000, 32000, 40000, 48000, 56000, 64000]。<br>- 采样率使用16000~32000时对应的比特率范围为[8000, 16000, 32000, 40000, 48000, 56000, 64000, 80000, 96000, 112000, 128000, 160000]。<br>- 采样率使用32000以上时对应的比特率范围为[32000, 40000, 48000, 56000, 64000, 80000, 96000, 112000, 128000, 160000, 192000, 224000, 256000, 320000]。|[1-2]|
| [AUDIO_G711MU](arkts-media-media-codecmimetype-e.md) |WAV|[8000]|[64000]|[1]|
|AUDIO_AMR_NB&lt;sup&gt;18+&lt;/sup&gt; |AMR|[8000]|[4750, 5150, 5900, 6700, 7400, 7950, 10200, 12200]|[1]|
|AUDIO_AMR_WB&lt;sup&gt;18+&lt;/sup&gt; |AMR|[16000]|[6600, 8850, 12650, 14250, 15850, 18250, 19850, 23050, 23850]|[1]|

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## enableStableQualityMode

```TypeScript
enableStableQualityMode?: boolean
```

视频录制是否选择稳定质量模式，选择视频录制时选填，enableStableQualityMode默认为false。设置为true时，启用视频编码策略以实现质量稳定的编码。

**类型：** boolean

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**系统接口：** 此接口为系统接口。
