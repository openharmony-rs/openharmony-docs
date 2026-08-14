# AVRecorder

音视频录制管理类，用于音视频媒体录制。在调用AVRecorder的方法前，需要先调用 [createAVRecorder](arkts-media-media-createavrecorder-f.md#createAVRecorder)接口构建一个 AVRecorder实例。 音视频录制demo可参考：[音频录制开发指导](../../../media/media/using-avrecorder-for-recording.md)、 [视频录制开发指导](../../../media/media/video-recording.md)。 > **说明：** > > - 本Interface首批API从API version 9开始支持。 > > - 相机视频录制功能需配合相机模块使用，相机模块接口的使用详情请参考[相机管理](../../apis-camera-kit/arkts-apis/arkts-multimedia-camera.md#@ohos.multimedia.camera)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-interface AVRecorder--><!--Device-unnamed-interface AVRecorder-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## addWatermark

```TypeScript
addWatermark(watermark: image.PixelMap, config: WatermarkConfiguration): Promise<int>
```

为AVRecorder添加水印。使用Promise异步回调。 应用最多可添加5个水印。 只能在prepared状态之前调用。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVRecorder-addWatermark(watermark: image.PixelMap, config: WatermarkConfiguration): Promise<int>--><!--Device-AVRecorder-addWatermark(watermark: image.PixelMap, config: WatermarkConfiguration): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| watermark | image.PixelMap | 是 | 水印图片。 |
| config | [WatermarkConfiguration](arkts-media-multimedia-media-watermarkconfiguration-i.md) | 是 | 水印配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回水印id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | The parameter check failed, parameter value out of range. |

## getAVRecorderConfig

```TypeScript
getAVRecorderConfig(callback: AsyncCallback<AVRecorderConfig>): void
```

获取实时的配置参数。使用callback异步回调。 只能在prepare接口调用成功后调用。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-AVRecorder-getAVRecorderConfig(callback: AsyncCallback<AVRecorderConfig>): void--><!--Device-AVRecorder-getAVRecorderConfig(callback: AsyncCallback<AVRecorderConfig>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AVRecorderConfig](arkts-media-multimedia-media-avrecorderconfig-i.md)&gt; | 是 | 回调函数。获取实时配置的参数成功时，err为undefined，data为获取到的配置参数，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## getAVRecorderConfig

```TypeScript
getAVRecorderConfig(callback: AsyncCallback<AVRecorderConfig | undefined>): void
```

获取实时的配置参数。使用callback异步回调。 只能在prepare()接口调用成功后调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-getAVRecorderConfig(callback: AsyncCallback<AVRecorderConfig | undefined>): void--><!--Device-AVRecorder-getAVRecorderConfig(callback: AsyncCallback<AVRecorderConfig | undefined>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AVRecorderConfig](arkts-media-multimedia-media-avrecorderconfig-i.md) \| undefined&gt; | 是 | 回调函数，返回实时配置参数，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## getAVRecorderConfig

```TypeScript
getAVRecorderConfig(): Promise<AVRecorderConfig>
```

获取实时的配置参数。使用Promise异步回调。 只能在prepare接口调用成功后调用。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-AVRecorder-getAVRecorderConfig(): Promise<AVRecorderConfig>--><!--Device-AVRecorder-getAVRecorderConfig(): Promise<AVRecorderConfig>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AVRecorderConfig](arkts-media-multimedia-media-avrecorderconfig-i.md)&gt; | Promise对象。返回实时配置参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## getAVRecorderConfig

```TypeScript
getAVRecorderConfig(): Promise<AVRecorderConfig | undefined>
```

获取实时的配置参数。使用Promise异步回调。 只能在prepare()接口调用成功后调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-getAVRecorderConfig(): Promise<AVRecorderConfig | undefined>--><!--Device-AVRecorder-getAVRecorderConfig(): Promise<AVRecorderConfig | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AVRecorderConfig](arkts-media-multimedia-media-avrecorderconfig-i.md) \| undefined&gt; | Promise对象，返回实时配置参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## getAudioCapturerMaxAmplitude

```TypeScript
getAudioCapturerMaxAmplitude(callback: AsyncCallback<int>): void
```

获取当前音频最大振幅。使用callback异步回调。 在prepare接口成功调用后，才能调用此接 口。在stop接口成功调用后，调用此接口会报错。 调用接口时，获取到的返回值是上一次获取最大振幅的时刻到当前这段区间内的音频最大振幅。例如，在1s时获取了一次最大振幅，到2s时再获取到的最大振幅是1-2s这个区间里面的最大值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-getAudioCapturerMaxAmplitude(callback: AsyncCallback<int>): void--><!--Device-AVRecorder-getAudioCapturerMaxAmplitude(callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;int&gt; | 是 | 回调函数。获取当前音频最大振幅成功时，err为undefined，data为获取到的最大振幅，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## getAudioCapturerMaxAmplitude

```TypeScript
getAudioCapturerMaxAmplitude(): Promise<int>
```

获取当前音频最大振幅。使用Promise异步回调。 在prepare接口成功调用后，才能调用此接 口。在stop接口成功调用后，调用此接口会报错。 调用接口时，获取到的返回值是上一次获取最大振幅的时刻到当前这段区间内的音频最大振幅。例如，在1s时获取了一次最大振幅，到2s时再获取到的最大振幅是1-2s这个区间里面的最大值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-getAudioCapturerMaxAmplitude(): Promise<int>--><!--Device-AVRecorder-getAudioCapturerMaxAmplitude(): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回获取的当前音频最大振幅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## getAvailableEncoder

```TypeScript
getAvailableEncoder(callback: AsyncCallback<Array<EncoderInfo>>): void
```

获取可用的编码器参数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-getAvailableEncoder(callback: AsyncCallback<Array<EncoderInfo>>): void--><!--Device-AVRecorder-getAvailableEncoder(callback: AsyncCallback<Array<EncoderInfo>>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;[EncoderInfo](arkts-media-multimedia-media-encoderinfo-i.md)&gt;&gt; | 是 | 回调函数。获取可用的编码器参数成功时，err为undefined，data为获取到的编码器参数，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## getAvailableEncoder

```TypeScript
getAvailableEncoder(): Promise<Array<EncoderInfo>>
```

获取可用的编码器参数。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-getAvailableEncoder(): Promise<Array<EncoderInfo>>--><!--Device-AVRecorder-getAvailableEncoder(): Promise<Array<EncoderInfo>>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[EncoderInfo](arkts-media-multimedia-media-encoderinfo-i.md)&gt;&gt; | Promise对象，返回获取的可用的编码器参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## getCurrentAudioCapturerInfo

```TypeScript
getCurrentAudioCapturerInfo(callback: AsyncCallback<audio.AudioCapturerChangeInfo>): void
```

获取当前音频采集参数。使用callback异步回调。 在prepare接口成功调用后，才能调用此接 口。在stop接口成功调用后，调用此接口会报错。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-AVRecorder-getCurrentAudioCapturerInfo(callback: AsyncCallback<audio.AudioCapturerChangeInfo>): void--><!--Device-AVRecorder-getCurrentAudioCapturerInfo(callback: AsyncCallback<audio.AudioCapturerChangeInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;audio.AudioCapturerChangeInfo&gt; | 是 | 回调函数。当获取音频采集参数成功时，err为undefined，data为获取到的 audio.AudioCapturerChangeInfo，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## getCurrentAudioCapturerInfo

```TypeScript
getCurrentAudioCapturerInfo(callback: AsyncCallback<audio.AudioCapturerChangeInfo | undefined>): void
```

获取当前音频采集参数。使用callback异步回调。 只能在prepare()接口调用成功后调用。在stop()接口成功调用后调用此接口会报错。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-getCurrentAudioCapturerInfo(callback: AsyncCallback<audio.AudioCapturerChangeInfo | undefined>): void--><!--Device-AVRecorder-getCurrentAudioCapturerInfo(callback: AsyncCallback<audio.AudioCapturerChangeInfo | undefined>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;audio.AudioCapturerChangeInfo \| undefined&gt; | 是 | 回调函数，返回audio.AudioCapturerChangeInfo对象，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## getCurrentAudioCapturerInfo

```TypeScript
getCurrentAudioCapturerInfo(): Promise<audio.AudioCapturerChangeInfo>
```

获取当前音频采集参数。使用Promise异步回调。 在prepare接口成功调用后，才能调用此接 口。在stop接口成功调用后，调用此接口会报错。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-AVRecorder-getCurrentAudioCapturerInfo(): Promise<audio.AudioCapturerChangeInfo>--><!--Device-AVRecorder-getCurrentAudioCapturerInfo(): Promise<audio.AudioCapturerChangeInfo>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;audio.AudioCapturerChangeInfo&gt; | Promise对象，返回获取的当前音频采集参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## getCurrentAudioCapturerInfo

```TypeScript
getCurrentAudioCapturerInfo(): Promise<audio.AudioCapturerChangeInfo | undefined>
```

获取当前音频采集参数。使用Promise异步回调。 只能在prepare()接口调用成功后调用。在stop()接口成功调用后调用此接口会报错。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-getCurrentAudioCapturerInfo(): Promise<audio.AudioCapturerChangeInfo | undefined>--><!--Device-AVRecorder-getCurrentAudioCapturerInfo(): Promise<audio.AudioCapturerChangeInfo | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;audio.AudioCapturerChangeInfo \| undefined&gt; | Promise对象，返回当前音频采集参数信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## getInputSurface

```TypeScript
getInputSurface(callback: AsyncCallback<string>): void
```

获取录制需要的surface。使用callback异步回调。 开发者从此surface中获取surfaceBuffer，填入相应的视频数据。 应当注意，填入的视频数据需要携带时间戳（单位ns）和buffersize。时间戳的起始时间请以系统启动时间为基准。 需在prepare接口成功调用后，才能调用 getInputSurface接口。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-AVRecorder-getInputSurface(callback: AsyncCallback<string>): void--><!--Device-AVRecorder-getInputSurface(callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 回调函数。当获取surface成功，err为undefined，data为获取到的surfaceId，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## getInputSurface

```TypeScript
getInputSurface(callback: AsyncCallback<string | undefined>): void
```

获取录制需要的surface。使用callback异步回调。 开发者从此surface中获取surfaceBuffer，填入相应的视频数据。 应当注意，填入的视频数据需要携带时间戳（单位ns）和buffersize。时间戳的起始时间请以系统启动时间为基准。 只能在prepare()接口调用成功后调用getInputSurface接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-getInputSurface(callback: AsyncCallback<string | undefined>): void--><!--Device-AVRecorder-getInputSurface(callback: AsyncCallback<string | undefined>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string \| undefined&gt; | 是 | 回调函数，返回surfaceId，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## getInputSurface

```TypeScript
getInputSurface(): Promise<string>
```

获取录制需要的surface。使用Promise异步回调。 开发者从此surface中获取surfaceBuffer，填入相应的视频数据。 应当注意，填入的视频数据需要携带时间戳（单位ns）和buffersize。时间戳的起始时间请以系统启动时间为基准。 需在prepare接口成功调用后，才能调用getInputSurface接口。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-AVRecorder-getInputSurface(): Promise<string>--><!--Device-AVRecorder-getInputSurface(): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回surfaceId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## getInputSurface

```TypeScript
getInputSurface(): Promise<string | undefined>
```

获取录制需要的surface。使用Promise异步回调。 开发者从此surface中获取surfaceBuffer，填入相应的视频数据。 应当注意，填入的视频数据需要携带时间戳（单位ns）和buffersize。时间戳的起始时间请以系统启动时间为基准。 只能在prepare()接口调用成功后调用getInputSurface接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-getInputSurface(): Promise<string | undefined>--><!--Device-AVRecorder-getInputSurface(): Promise<string | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string \| undefined&gt; | Promise对象，返回surfaceId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## offAudioCapturerChange

```TypeScript
offAudioCapturerChange(callback?: Callback<audio.AudioCapturerChangeInfo>): void
```

Subscribes to audio capturer configuration changes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-offAudioCapturerChange(callback?: Callback<audio.AudioCapturerChangeInfo>): void--><!--Device-AVRecorder-offAudioCapturerChange(callback?: Callback<audio.AudioCapturerChangeInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;audio.AudioCapturerChangeInfo&gt; | 否 | Callback used to return the entire configuration information about the audio capturer. This parameter is supported since API version 12. |

## offError

```TypeScript
offError(callback?: ErrorCallback): void
```

Unsubscribes from AVRecorder errors. After the unsubscription, your application can no longer receive AVRecorder errors.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-offError(callback?: ErrorCallback): void--><!--Device-AVRecorder-offError(callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 否 | Callback invoked when the event is triggered. This parameter is supported since API version 12. |

## offPhotoAssetAvailable

```TypeScript
offPhotoAssetAvailable(callback?: Callback<photoAccessHelper.PhotoAsset>): void
```

Unsubscribes from media asset callback events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-offPhotoAssetAvailable(callback?: Callback<photoAccessHelper.PhotoAsset>): void--><!--Device-AVRecorder-offPhotoAssetAvailable(callback?: Callback<photoAccessHelper.PhotoAsset>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;photoAccessHelper.PhotoAsset&gt; | 否 | Callback used to return the **PhotoAsset** object corresponding to the resource file created by the system. |

## offStateChange

```TypeScript
offStateChange(callback?: OnAVRecorderStateChangeHandler): void
```

Unsubscribes from AVRecorder state changes. This event can be triggered by both user operations and the system.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-offStateChange(callback?: OnAVRecorderStateChangeHandler): void--><!--Device-AVRecorder-offStateChange(callback?: OnAVRecorderStateChangeHandler): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnAVRecorderStateChangeHandler](arkts-media-onavrecorderstatechangehandler-t.md) | 否 | Callback invoked when the event is triggered. This parameter is supported since API version 12. |

## off_audioCapturerChange

```TypeScript
off(type: 'audioCapturerChange', callback?: Callback<audio.AudioCapturerChangeInfo>): void
```

取消订阅录音变化的回调事件。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-AVRecorder-off(type: 'audioCapturerChange', callback?: Callback<audio.AudioCapturerChangeInfo>): void--><!--Device-AVRecorder-off(type: 'audioCapturerChange', callback?: Callback<audio.AudioCapturerChangeInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioCapturerChange' | 是 | 录音配置变化的回调类型，支持的事件：'audioCapturerChange'。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;audio.AudioCapturerChangeInfo&gt; | 否 | 回调函数，返回变化后的录音配置全量信息。如果指定参数则取消对应callback（callback对象不 能是匿名函数），否则取消所有callback。&lt;br/&gt;从API version 12开始支持此参数。<br>**起始版本：** 12 |

## off_error

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

取消订阅录制错误事件，取消后不再接收到AVRecorder的错误事件。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorder-off(type: 'error', callback?: ErrorCallback): void--><!--Device-AVRecorder-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 录制错误事件回调类型'error'。 &lt;br&gt;- 'error'：录制过程中发生错误，触发该事件。 |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 否 | 回调函数，返回录制错误事件。如果指定参数则取消对应callback（callback对象不能是匿名函数），否则取消所有callback。&lt;br/&gt;从API version 12开始支持此参数。<br>**起始版本：** 12 |

## off_photoAssetAvailable

```TypeScript
off(type: 'photoAssetAvailable', callback?: Callback<photoAccessHelper.PhotoAsset>): void
```

取消订阅媒体资源的回调类型。使用callback异步回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-AVRecorder-off(type: 'photoAssetAvailable', callback?: Callback<photoAccessHelper.PhotoAsset>): void--><!--Device-AVRecorder-off(type: 'photoAssetAvailable', callback?: Callback<photoAccessHelper.PhotoAsset>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'photoAssetAvailable' | 是 | 录音配置变化的回调类型，支持的事件：'photoAssetAvailable'。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;photoAccessHelper.PhotoAsset&gt; | 否 | 回调函数，返回系统创建的资源文件对应的PhotoAsset对象。如果指定参数则取消对应callback（ callback对象不能是匿名函数），否则取消所有callback。 |

## off_stateChange

```TypeScript
off(type: 'stateChange', callback?: OnAVRecorderStateChangeHandler): void
```

取消订阅录制状态机AVRecorderState切换的事件。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorder-off(type: 'stateChange', callback?: OnAVRecorderStateChangeHandler): void--><!--Device-AVRecorder-off(type: 'stateChange', callback?: OnAVRecorderStateChangeHandler): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 录制状态机切换事件回调类型，支持的事件：'stateChange'，用户操作和系统都会触发此事件。 |
| callback | [OnAVRecorderStateChangeHandler](arkts-media-onavrecorderstatechangehandler-t.md) | 否 | 回调函数，返回录制状态机切换事件。如果指定参数则取消对应callback（callback对象不能是匿名函数），否则取消 所有callback。&lt;br/&gt;从API version 12开始支持此参数。<br>**起始版本：** 12 |

## onAudioCapturerChange

```TypeScript
onAudioCapturerChange(callback: Callback<audio.AudioCapturerChangeInfo>): void
```

Subscribes to audio capturer configuration changes. Any configuration change triggers the callback that returns the entire configuration information. When the application initiates multiple subscriptions to this event, the last subscription is applied.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-onAudioCapturerChange(callback: Callback<audio.AudioCapturerChangeInfo>): void--><!--Device-AVRecorder-onAudioCapturerChange(callback: Callback<audio.AudioCapturerChangeInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;audio.AudioCapturerChangeInfo&gt; | 是 | Callback used to return the entire configuration information about the audio capturer. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

## onError

```TypeScript
onError(callback: ErrorCallback): void
```

Subscribes to AVRecorder errors. This event is used only for error prompt and does not require the user to stop recording control. If the AVRecorderState is also switched to error, call reset() or release() to exit the recording. An application can subscribe to only one AVRecorder error event. When the application initiates multiple subscriptions to this event, the last subscription is applied. This event is triggered when an error occurs during recording.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-onError(callback: ErrorCallback): void--><!--Device-AVRecorder-onError(callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 是 | Callback invoked when the event is triggered. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [5400107](../errorcode-media.md#5400107-音频焦点冲突) | Audio interrupted. |
| [5400104](../errorcode-media.md#5400104-操作超时) | Time out. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. |

## onPhotoAssetAvailable

```TypeScript
onPhotoAssetAvailable(callback: Callback<photoAccessHelper.PhotoAsset>): void
```

Subscribes to media asset callback events. When FileGenerationMode is used during media file creation, the PhotoAsset object is called back to the application after the stop operation is complete. When the application initiates multiple subscriptions to this event, the last subscription is applied. The event is triggered when a photo asset is available.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-onPhotoAssetAvailable(callback: Callback<photoAccessHelper.PhotoAsset>): void--><!--Device-AVRecorder-onPhotoAssetAvailable(callback: Callback<photoAccessHelper.PhotoAsset>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;photoAccessHelper.PhotoAsset&gt; | 是 | Callback used to return the **PhotoAsset** object corresponding to the resource file created by the system. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## onStateChange

```TypeScript
onStateChange(callback: OnAVRecorderStateChangeHandler): void
```

Subscribes to AVRecorder state changes. An application can subscribe to only one AVRecorder state change event. When the application initiates multiple subscriptions to this event, the last subscription is applied. This event can be triggered by both user operations and the system.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-onStateChange(callback: OnAVRecorderStateChangeHandler): void--><!--Device-AVRecorder-onStateChange(callback: OnAVRecorderStateChangeHandler): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnAVRecorderStateChangeHandler](arkts-media-onavrecorderstatechangehandler-t.md) | 是 | Callback invoked when the event is triggered. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## on_audioCapturerChange

```TypeScript
on(type: 'audioCapturerChange', callback: Callback<audio.AudioCapturerChangeInfo>): void
```

订阅录音配置变化的回调，任意录音配置的变化会触发变化后的录音配置全量信息回调。使用callback异步回调。 当用户重复订阅时，以最后一次订阅的回调接口为准。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-AVRecorder-on(type: 'audioCapturerChange', callback: Callback<audio.AudioCapturerChangeInfo>): void--><!--Device-AVRecorder-on(type: 'audioCapturerChange', callback: Callback<audio.AudioCapturerChangeInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioCapturerChange' | 是 | 录音配置变化的回调类型，支持的事件：'audioCapturerChange'。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;audio.AudioCapturerChangeInfo&gt; | 是 | 回调函数，返回变化后的录音配置全量信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

## on_error

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

订阅AVRecorder的错误事件，该事件仅用于错误提示，不需要用户停止播控动作。如果此时 AVRecorderState也切换至error状态，用户需要通过 reset或者 release接口退出录制操作。使用callback异步回调。 用户只能订阅一个错误事件的回调方法，当用户重复订阅时，以最后一次订阅的回调接口为准。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorder-on(type: 'error', callback: ErrorCallback): void--><!--Device-AVRecorder-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 录制错误事件回调类型'error'。 &lt;br&gt;- 'error'：录制过程中发生错误，触发该事件。 |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 是 | 回调函数，返回录制错误事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [5400107](../errorcode-media.md#5400107-音频焦点冲突) | Audio interrupted.<br>**适用版本：** 11+ |
| [5400104](../errorcode-media.md#5400104-操作超时) | Time out. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. |

## on_photoAssetAvailable

```TypeScript
on(type: 'photoAssetAvailable', callback: Callback<photoAccessHelper.PhotoAsset>): void
```

订阅媒体资源回调事件，当FileGenerationMode枚举设置为系统创建媒体文件时，会在 stop操作结束后把 PhotoAsset对象回调给应用。使用callback异步回调。 当用户重复订阅时，以最后一次订阅的回调接口为准。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-AVRecorder-on(type: 'photoAssetAvailable', callback: Callback<photoAccessHelper.PhotoAsset>): void--><!--Device-AVRecorder-on(type: 'photoAssetAvailable', callback: Callback<photoAccessHelper.PhotoAsset>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'photoAssetAvailable' | 是 | 录像资源的回调类型，支持的事件：'photoAssetAvailable'。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;photoAccessHelper.PhotoAsset&gt; | 是 | 回调函数，返回系统创建的资源文件对应的PhotoAsset对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## on_stateChange

```TypeScript
on(type: 'stateChange', callback: OnAVRecorderStateChangeHandler): void
```

订阅录制状态机AVRecorderState切换的事件，当AVRecorderState状态机发生变化时，会通过订阅的回调方法通知用户。用户只能订阅一个录制状态机切换事件的回调方法，当用户重复订阅时，以最后一次订阅的回调接口为 准。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorder-on(type: 'stateChange', callback: OnAVRecorderStateChangeHandler): void--><!--Device-AVRecorder-on(type: 'stateChange', callback: OnAVRecorderStateChangeHandler): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 录制状态机切换事件回调类型，支持的事件：'stateChange'，用户操作和系统都会触发此事件。 |
| callback | [OnAVRecorderStateChangeHandler](arkts-media-onavrecorderstatechangehandler-t.md) | 是 | 回调函数，返回录制状态机切换事件。<br>**起始版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## pause

```TypeScript
pause(callback: AsyncCallback<void>): void
```

暂停视频录制。使用callback异步回调。 需要start接口成功调用后，才能调用pause接口，可以通过调用 resume接口来恢复录制。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-pause(callback: AsyncCallback<void>): void--><!--Device-AVRecorder-pause(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当暂停视频录制成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## pause

```TypeScript
pause(): Promise<void>
```

暂停视频录制。使用Promise异步回调。 需要start接口成功调用后，才能调用pause接口，可以通过调用resume接口来恢复 录制。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorder-pause(): Promise<void>--><!--Device-AVRecorder-pause(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## prepare

```TypeScript
prepare(config: AVRecorderConfig, callback: AsyncCallback<void>): void
```

音视频录制的参数设置。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MICROPHONE

<!--Device-AVRecorder-prepare(config: AVRecorderConfig, callback: AsyncCallback<void>): void--><!--Device-AVRecorder-prepare(config: AVRecorderConfig, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [AVRecorderConfig](arkts-media-multimedia-media-avrecorderconfig-i.md) | 是 | 配置音视频录制的相关参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当prepare接口成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by callback. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## prepare

```TypeScript
prepare(config: AVRecorderConfig): Promise<void>
```

音视频录制的参数设置。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** 
- API版本12+：ohos.permission.MICROPHONE This permission is required only if audio recording is involved.
- API版本9 - 11：ohos.permission.MICROPHONE

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorder-prepare(config: AVRecorderConfig): Promise<void>--><!--Device-AVRecorder-prepare(config: AVRecorderConfig): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [AVRecorderConfig](arkts-media-multimedia-media-avrecorderconfig-i.md) | 是 | 配置音视频录制的相关参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放音视频录制资源。使用callback异步回调。 释放音视频录制资源之后，该AVRecorder实例不能再进行任何操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-release(callback: AsyncCallback<void>): void--><!--Device-AVRecorder-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当释放音视频录制资源成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## release

```TypeScript
release(): Promise<void>
```

释放音视频录制资源。使用Promise异步回调。 释放音视频录制资源之后，该AVRecorder实例不能再进行任何操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorder-release(): Promise<void>--><!--Device-AVRecorder-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## reset

```TypeScript
reset(callback: AsyncCallback<void>): void
```

重置音视频录制。使用callback异步回调。 纯音频录制时，需要重新调用prepare接口 才能重新录制。纯视频录制，音视频录制时，需要重新调用 prepare和 getInputSurface接口才能重新录制。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-reset(callback: AsyncCallback<void>): void--><!--Device-AVRecorder-reset(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当重置音视频录制成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## reset

```TypeScript
reset(): Promise<void>
```

重置音视频录制。使用Promise异步回调。 纯音频录制时，需要重新调用prepare接口才能重新录制。纯视频录制，音视频录制时，需要重新调用 prepare和 getInputSurface接口才能重新录制。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-reset(): Promise<void>--><!--Device-AVRecorder-reset(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## resume

```TypeScript
resume(callback: AsyncCallback<void>): void
```

恢复视频录制。使用callback异步回调。 需要在pause接口成功调用后，才能调用resume接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-resume(callback: AsyncCallback<void>): void--><!--Device-AVRecorder-resume(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当恢复视频录制成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## resume

```TypeScript
resume(): Promise<void>
```

恢复视频录制。使用Promise异步回调。 需要在pause接口成功调用后，才能调用resume接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorder-resume(): Promise<void>--><!--Device-AVRecorder-resume(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## setWillMuteWhenInterrupted

```TypeScript
setWillMuteWhenInterrupted(muteWhenInterrupted: boolean): Promise<void>
```

设置当前录制音频流是否启用静音打断模式。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-setWillMuteWhenInterrupted(muteWhenInterrupted: boolean): Promise<void>--><!--Device-AVRecorder-setWillMuteWhenInterrupted(muteWhenInterrupted: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| muteWhenInterrupted | boolean | 是 | 设置当前录制音频流是否启用静音打断模式, true表示启用，false表示不启用，保持为默认打断模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

开始视频录制。使用callback异步回调。 纯音频录制需在prepare接口成功调用后， 才能调用start接口。纯视频录制，音视频录制需在 getInputSurface接口成功调用后，才能调用start接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-start(callback: AsyncCallback<void>): void--><!--Device-AVRecorder-start(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当开始录制视频成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## start

```TypeScript
start(): Promise<void>
```

开始视频录制。使用Promise异步回调。 纯音频录制需在prepare接口成功调用后，才能调用start接口。纯视频录制，音视频录制需在 getInputSurface接口成功调用后，才能调用start接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorder-start(): Promise<void>--><!--Device-AVRecorder-start(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

停止视频录制。使用callback异步回调。 需要在start或 pause接口成功调用后，才能调用stop接口。 纯音频录制时，需要重新调用prepare接口 才能重新录制。纯视频录制，音视频录制时，需要重新调用 prepare和 getInputSurface接口才能重新录制。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-stop(callback: AsyncCallback<void>): void--><!--Device-AVRecorder-stop(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当停止视频录制成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## stop

```TypeScript
stop(): Promise<void>
```

停止视频录制。使用Promise异步回调。 需要在start或pause接口成功调用后，才能调用stop接口。 纯音频录制时，需要重新调用prepare接口才能重新录制。纯视频录制，音视频录制时，需要重新调用 prepare和 getInputSurface接口才能重新录制。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorder-stop(): Promise<void>--><!--Device-AVRecorder-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## updateRotation

```TypeScript
updateRotation(rotation: int): Promise<void>
```

更新视频旋转角度。使用Promise异步回调。 当且仅当prepare接口成功调用后，且在 start接口之前，才能调用updateRotation接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVRecorder-updateRotation(rotation: int): Promise<void>--><!--Device-AVRecorder-updateRotation(rotation: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotation | int | 是 | 旋转角度，取值仅支持0、90、180、270度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## state

```TypeScript
readonly state: AVRecorderState
```

音视频录制的状态。 **原子化服务API：** 从API version 12 开始，该接口支持在原子化服务中使用。

**类型：** [AVRecorderState](arkts-media-avrecorderstate-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorder-readonly state: AVRecorderState--><!--Device-AVRecorder-readonly state: AVRecorderState-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

