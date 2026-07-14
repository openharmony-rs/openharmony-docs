# AudioCapturerMicInData（系统接口）

描述音频录音数据，其中包含已处理的音频数据和
进行音频处理前的纯净麦克风输入（mic-in）音频数据。

**起始版本：** 24

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## data

```TypeScript
data: ArrayBuffer
```

处理后的音频数据缓冲。

**类型：** ArrayBuffer

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## ecData

```TypeScript
ecData?: ArrayBuffer
```

回声参考音频数据缓冲。
如果录音配置没有设置ecStreamInfo，则此缓冲将为空。
有关详细信息，请参见{@link #AudioCapturerMicInConfig}。

**类型：** ArrayBuffer

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## micInData

```TypeScript
micInData: ArrayBuffer
```

麦克风输入音频数据缓冲。

**类型：** ArrayBuffer

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

