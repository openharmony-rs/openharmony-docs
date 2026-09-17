# AudioCapturerMicInData（系统接口）

音频采集器数据，包含处理后的音频数据和未经任何处理的麦克风输入（mic-in）音频数据。

**起始版本：** 24

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## data

```TypeScript
data: ArrayBuffer
```

处理后的音频数据缓冲区。

**类型：** ArrayBuffer

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## ecData

```TypeScript
ecData?: ArrayBuffer
```

回声参考音频数据缓冲区。

如果采集器配置未设置ecStreamInfo，则该字段为空，详情请参考[AudioCapturerMicInConfig](arkts-audio-audio-audiocapturermicinconfig-i-sys.md)。

**类型：** ArrayBuffer

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## micInData

```TypeScript
micInData: ArrayBuffer
```

麦克风输入音频数据缓冲区。

**类型：** ArrayBuffer

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。
