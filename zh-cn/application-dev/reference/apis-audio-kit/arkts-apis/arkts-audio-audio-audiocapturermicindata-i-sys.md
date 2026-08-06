# AudioCapturerMicInData（系统接口）

描述音频录音数据，其中包含已处理的音频数据和 进行音频处理前的纯净麦克风输入（mic-in）音频数据。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

<!--Device-audio-interface AudioCapturerMicInData--><!--Device-audio-interface AudioCapturerMicInData-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## data

```TypeScript
data: ArrayBuffer
```

处理后的音频数据缓冲。

**类型：** ArrayBuffer

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturerMicInData-data: ArrayBuffer--><!--Device-AudioCapturerMicInData-data: ArrayBuffer-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## ecData

```TypeScript
ecData?: ArrayBuffer
```

回声参考音频数据缓冲。 如果录音配置没有设置ecStreamInfo，则此缓冲将为空。 有关详细信息，请参见\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** ArrayBuffer

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturerMicInData-ecData?: ArrayBuffer--><!--Device-AudioCapturerMicInData-ecData?: ArrayBuffer-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## micInData

```TypeScript
micInData: ArrayBuffer
```

麦克风输入音频数据缓冲。

**类型：** ArrayBuffer

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturerMicInData-micInData: ArrayBuffer--><!--Device-AudioCapturerMicInData-micInData: ArrayBuffer-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

