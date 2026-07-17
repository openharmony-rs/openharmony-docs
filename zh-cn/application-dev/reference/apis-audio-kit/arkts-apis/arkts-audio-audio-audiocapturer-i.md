# AudioCapturer

提供音频采集的相关接口。

在使用AudioCapturer的接口之前，需先通过[createAudioCapturer](arkts-audio-audio-createaudiocapturer-f.md#createaudiocapturer-1)获取AudioCapturer实例。

> **说明：**  
>  
> - 本Interface首批接口从API version 8开始支持。

**起始版本：** 8

<!--Device-audio-interface AudioCapturer--><!--Device-audio-interface AudioCapturer-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getAudioStreamId

```TypeScript
getAudioStreamId(callback: AsyncCallback<number>): void
```

获取音频流id。使用callback异步回调。

**起始版本：** 9

<!--Device-AudioCapturer-getAudioStreamId(callback: AsyncCallback<long>): void--><!--Device-AudioCapturer-getAudioStreamId(callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。当获取音频流id成功，err为undefined，data为获取到的音频流id；否则为错误对象。 |

## getAudioStreamId

```TypeScript
getAudioStreamId(): Promise<number>
```

获取音频流id。使用Promise异步回调。

**起始版本：** 9

<!--Device-AudioCapturer-getAudioStreamId(): Promise<long>--><!--Device-AudioCapturer-getAudioStreamId(): Promise<long>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回音频流id。 |

## getAudioStreamIdSync

```TypeScript
getAudioStreamIdSync(): number
```

获取音频流id。同步返回结果。

**起始版本：** 10

<!--Device-AudioCapturer-getAudioStreamIdSync(): long--><!--Device-AudioCapturer-getAudioStreamIdSync(): long-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回音频流id。 |

## getAudioTime

```TypeScript
getAudioTime(callback: AsyncCallback<number>): void
```

获取当前录制位置的时间戳（从1970年1月1日开始），单位为纳秒。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioCapturer-getAudioTime(callback: AsyncCallback<long>): void--><!--Device-AudioCapturer-getAudioTime(callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。当获取时间戳成功，err为undefined，data为获取到的时间戳；否则为错误对象。 |

## getAudioTime

```TypeScript
getAudioTime(): Promise<number>
```

获取当前录制位置的时间戳（从1970年1月1日开始），单位为纳秒。使用Promise异步回调。

**起始版本：** 8

<!--Device-AudioCapturer-getAudioTime(): Promise<long>--><!--Device-AudioCapturer-getAudioTime(): Promise<long>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回时间戳（从1970年1月1日开始）。<br>单位为纳秒。 |

## getAudioTimeSync

```TypeScript
getAudioTimeSync(): number
```

获取当前录制位置的时间戳（从1970年1月1日开始），单位为纳秒。同步返回结果。

**起始版本：** 10

<!--Device-AudioCapturer-getAudioTimeSync(): long--><!--Device-AudioCapturer-getAudioTimeSync(): long-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回时间戳。 |

## getAudioTimestampInfo

```TypeScript
getAudioTimestampInfo(): Promise<AudioTimestampInfo>
```

获取输入音频流时间戳和当前数据帧位置信息。

该接口可以获取到音频通道实际录制位置（framePos）以及录制到该位置时候的时间戳（timestamp），时间戳单位为纳秒。

**起始版本：** 19

<!--Device-AudioCapturer-getAudioTimestampInfo(): Promise<AudioTimestampInfo>--><!--Device-AudioCapturer-getAudioTimestampInfo(): Promise<AudioTimestampInfo>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<AudioTimestampInfo> | Promise对象，返回音频流时间戳和当前数据帧位置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Operation not permit at current state. |

## getAudioTimestampInfoSync

```TypeScript
getAudioTimestampInfoSync(): AudioTimestampInfo
```

获取音频流时间戳和当前数据帧位置信息。同步返回结果。

**起始版本：** 19

<!--Device-AudioCapturer-getAudioTimestampInfoSync(): AudioTimestampInfo--><!--Device-AudioCapturer-getAudioTimestampInfoSync(): AudioTimestampInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioTimestampInfo](arkts-audio-audio-audiotimestampinfo-i.md) | 返回音频流时间戳和当前数据帧位置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Operation not permit at current state. |

## getBufferSize

```TypeScript
getBufferSize(callback: AsyncCallback<number>): void
```

获取采集器合理的最小缓冲区大小。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioCapturer-getBufferSize(callback: AsyncCallback<long>): void--><!--Device-AudioCapturer-getBufferSize(callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。当获取采集器合理的最小缓冲区大小成功，err为undefined，data为获取到的采集器合理的最小缓冲区大小；否则为错误对象。<br>单位为字节。 |

## getBufferSize

```TypeScript
getBufferSize(): Promise<number>
```

获取采集器合理的最小缓冲区大小。使用Promise异步回调。

**起始版本：** 8

<!--Device-AudioCapturer-getBufferSize(): Promise<long>--><!--Device-AudioCapturer-getBufferSize(): Promise<long>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回缓冲区大小。<br>单位为字节。 |

## getBufferSizeSync

```TypeScript
getBufferSizeSync(): number
```

获取采集器合理的最小缓冲区大小。同步返回结果。

**起始版本：** 10

<!--Device-AudioCapturer-getBufferSizeSync(): long--><!--Device-AudioCapturer-getBufferSizeSync(): long-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回缓冲区大小，单位为字节。 |

## getCapturerInfo

```TypeScript
getCapturerInfo(callback: AsyncCallback<AudioCapturerInfo>): void
```

获取音频采集器信息。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioCapturer-getCapturerInfo(callback: AsyncCallback<AudioCapturerInfo>): void--><!--Device-AudioCapturer-getCapturerInfo(callback: AsyncCallback<AudioCapturerInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<AudioCapturerInfo> | 是 | 回调函数。当获取音频采集器信息成功，err为undefined，data为获取到的音频采集器信息；否则为错误对象。 |

## getCapturerInfo

```TypeScript
getCapturerInfo(): Promise<AudioCapturerInfo>
```

获取音频采集器信息。使用Promise异步回调。

**起始版本：** 8

<!--Device-AudioCapturer-getCapturerInfo(): Promise<AudioCapturerInfo>--><!--Device-AudioCapturer-getCapturerInfo(): Promise<AudioCapturerInfo>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<AudioCapturerInfo> | Promise对象，返回音频采集器信息。 |

## getCapturerInfoSync

```TypeScript
getCapturerInfoSync(): AudioCapturerInfo
```

获取音频采集器信息。同步返回结果。

**起始版本：** 10

<!--Device-AudioCapturer-getCapturerInfoSync(): AudioCapturerInfo--><!--Device-AudioCapturer-getCapturerInfoSync(): AudioCapturerInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md) | 返回音频采集器信息。 |

## getCurrentAudioCapturerChangeInfo

```TypeScript
getCurrentAudioCapturerChangeInfo(): AudioCapturerChangeInfo
```

获取录音流配置。同步返回结果。

**起始版本：** 11

<!--Device-AudioCapturer-getCurrentAudioCapturerChangeInfo(): AudioCapturerChangeInfo--><!--Device-AudioCapturer-getCurrentAudioCapturerChangeInfo(): AudioCapturerChangeInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioCapturerChangeInfo](arkts-audio-audio-audiocapturerchangeinfo-i.md) | 同步接口，返回描述音频采集器更改信息。 |

## getCurrentInputDevices

```TypeScript
getCurrentInputDevices(): AudioDeviceDescriptors
```

获取录音流输入设备信息。同步返回结果。

**起始版本：** 11

<!--Device-AudioCapturer-getCurrentInputDevices(): AudioDeviceDescriptors--><!--Device-AudioCapturer-getCurrentInputDevices(): AudioDeviceDescriptors-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | 同步接口，返回设备属性数组类型数据。 |

## getNoiseReductionMode

```TypeScript
getNoiseReductionMode(): NoiseReductionMode
```

获取当前音频捕获器的降噪模式。模式将只考虑默认和设置的状态，音频输入设备和流并发将不被视为。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturer-getNoiseReductionMode(): NoiseReductionMode--><!--Device-AudioCapturer-getNoiseReductionMode(): NoiseReductionMode-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NoiseReductionMode](arkts-audio-audio-noisereductionmode-e.md) | 当前音频采集器的降噪模式，默认值为{@link噪声抑制模式#FIDELITY}。 |

## getOverflowCount

```TypeScript
getOverflowCount(): Promise<number>
```

获取当前录制音频流的过载音频帧数量。使用Promise异步回调。

**起始版本：** 12

<!--Device-AudioCapturer-getOverflowCount(): Promise<long>--><!--Device-AudioCapturer-getOverflowCount(): Promise<long>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | - Promise对象，返回音频流的过载音频帧数量。 |

## getOverflowCountSync

```TypeScript
getOverflowCountSync(): number
```

获取当前录制音频流的过载音频帧数量。同步返回数据。

**起始版本：** 12

<!--Device-AudioCapturer-getOverflowCountSync(): long--><!--Device-AudioCapturer-getOverflowCountSync(): long-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回音频流的过载音频帧数量。 |

## getStreamInfo

```TypeScript
getStreamInfo(callback: AsyncCallback<AudioStreamInfo>): void
```

获取音频采集器流信息。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioCapturer-getStreamInfo(callback: AsyncCallback<AudioStreamInfo>): void--><!--Device-AudioCapturer-getStreamInfo(callback: AsyncCallback<AudioStreamInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<AudioStreamInfo> | 是 | 回调函数。当获取音频采集器流信息成功，err为undefined，data为获取到的音频采集器流信息；否则为错误对象。 |

## getStreamInfo

```TypeScript
getStreamInfo(): Promise<AudioStreamInfo>
```

获取音频采集器流信息。使用Promise异步回调。

**起始版本：** 8

<!--Device-AudioCapturer-getStreamInfo(): Promise<AudioStreamInfo>--><!--Device-AudioCapturer-getStreamInfo(): Promise<AudioStreamInfo>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<AudioStreamInfo> | Promise对象，返回音频流信息。 |

## getStreamInfoSync

```TypeScript
getStreamInfoSync(): AudioStreamInfo
```

获取音频采集器流信息。同步返回结果。

**起始版本：** 10

<!--Device-AudioCapturer-getStreamInfoSync(): AudioStreamInfo--><!--Device-AudioCapturer-getStreamInfoSync(): AudioStreamInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md) | 返回音频流信息。 |

## getSupportedNoiseReductionModes

```TypeScript
getSupportedNoiseReductionModes(): Array<NoiseReductionMode>
```

获取当前设备平台支持的所有降噪模式。目前，降噪效果仅在使用{@link StreamUsage#Stream_USAGE_VOICE_MESSAGE}，其他支持的用法可能会在以后扩展。支持的模式只考虑音频格式和设备平台。不会考虑音频输入设备和流并发。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturer-getSupportedNoiseReductionModes(): Array<NoiseReductionMode>--><!--Device-AudioCapturer-getSupportedNoiseReductionModes(): Array<NoiseReductionMode>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<NoiseReductionMode> | 支持的降噪模式数组，至少支持{@link噪声抑制模式#FIDELITY}。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio server process died. |

## off('markReach')

```TypeScript
off(type: 'markReach', callback?: Callback<number>): void
```

取消监听标记到达事件。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioCapturer-off(type: 'markReach', callback?: Callback<long>): void--><!--Device-AudioCapturer-off(type: 'markReach', callback?: Callback<long>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'markReach' | 是 | 事件回调类型，支持的事件为'markReach'，当取消监听标记到达事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<number> | 否 | 回调函数，返回frame参数的值。<br>**起始版本：** 18 |

## off('periodReach')

```TypeScript
off(type: 'periodReach', callback?: Callback<number>): void
```

取消监听标记到达事件。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioCapturer-off(type: 'periodReach', callback?: Callback<long>): void--><!--Device-AudioCapturer-off(type: 'periodReach', callback?: Callback<long>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'periodReach' | 是 | 事件回调类型，支持的事件为'periodReach'，当取消监听标记到达事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<number> | 否 | 回调函数，返回frame参数的值。<br>**起始版本：** 18 |

## off('stateChange')

```TypeScript
off(type: 'stateChange', callback?: Callback<AudioState>): void
```

取消监听状态变化事件。使用callback异步回调。

**起始版本：** 18

<!--Device-AudioCapturer-off(type: 'stateChange', callback?: Callback<AudioState>): void--><!--Device-AudioCapturer-off(type: 'stateChange', callback?: Callback<AudioState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 事件回调类型，支持的事件为'stateChange'，当取消监听状态变化事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AudioState> | 否 | 回调函数，返回当前音频的状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off

```TypeScript
off(type: 'audioInterrupt'): void
```

取消监听音频中断事件。

**起始版本：** 10

<!--Device-AudioCapturer-off(type: 'audioInterrupt'): void--><!--Device-AudioCapturer-off(type: 'audioInterrupt'): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Interrupt

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | 是 | 事件回调类型，支持的事件为'audioInterrupt'，当取消监听音频中断事件时，触发该事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off('inputDeviceChange')

```TypeScript
off(type: 'inputDeviceChange', callback?: Callback<AudioDeviceDescriptors>): void
```

取消监听音频输入设备更改事件。使用callback异步回调。

**起始版本：** 11

<!--Device-AudioCapturer-off(type: 'inputDeviceChange', callback?: Callback<AudioDeviceDescriptors>): void--><!--Device-AudioCapturer-off(type: 'inputDeviceChange', callback?: Callback<AudioDeviceDescriptors>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'inputDeviceChange' | 是 | 事件回调类型，支持的事件为'inputDeviceChange'，当取消监听音频输入设备更改事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AudioDeviceDescriptors> | 否 | 回调函数，返回音频输入设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off('audioCapturerChange')

```TypeScript
off(type: 'audioCapturerChange', callback?: Callback<AudioCapturerChangeInfo>): void
```

取消监听录音流配置变化事件。使用callback异步回调。

**起始版本：** 11

<!--Device-AudioCapturer-off(type: 'audioCapturerChange', callback?: Callback<AudioCapturerChangeInfo>): void--><!--Device-AudioCapturer-off(type: 'audioCapturerChange', callback?: Callback<AudioCapturerChangeInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioCapturerChange' | 是 | 事件回调类型，支持的事件为'audioCapturerChange'，当取消监听录音流配置变化事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AudioCapturerChangeInfo> | 否 | 回调函数，返回取消监听的录音流配置或状态变化。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off('readData')

```TypeScript
off(type: 'readData', callback?: Callback<ArrayBuffer>): void
```

取消监听音频数据读取回调事件。使用callback异步回调。

**起始版本：** 11

<!--Device-AudioCapturer-off(type: 'readData', callback?: Callback<ArrayBuffer>): void--><!--Device-AudioCapturer-off(type: 'readData', callback?: Callback<ArrayBuffer>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'readData' | 是 | 事件回调类型，支持的事件为'readData'，当取消监听音频数据读取回调事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<ArrayBuffer> | 否 | 回调函数，返回读到的数据缓冲区。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('markReach')

```TypeScript
on(type: 'markReach', frame: number, callback: Callback<number>): void
```

监听标记到达事件（当采集的帧数达到frame参数的值时触发，仅调用一次）。使用callback异步回调。

如果将frame设置为100，当采集帧数到达第100帧时，系统将上报信息。

**起始版本：** 8

<!--Device-AudioCapturer-on(type: 'markReach', frame: long, callback: Callback<long>): void--><!--Device-AudioCapturer-on(type: 'markReach', frame: long, callback: Callback<long>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'markReach' | 是 | 事件回调类型，支持的事件为'markReach'，当采集的帧数达到frame参数的值时，触发该事件。 |
| frame | number | 是 | 触发事件的帧数。该值必须大于0。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<number> | 是 | 回调函数，返回frame参数的值。 |

## on('periodReach')

```TypeScript
on(type: 'periodReach', frame: number, callback: Callback<number>): void
```

监听标记到达事件（当采集的帧数达到frame参数的值时触发，即按周期上报信息）。使用callback异步回调。

如果将frame设置为10，每渲染10帧数据均会上报信息（例如：第10帧、第20帧、第30帧......）。

**起始版本：** 8

<!--Device-AudioCapturer-on(type: 'periodReach', frame: long, callback: Callback<long>): void--><!--Device-AudioCapturer-on(type: 'periodReach', frame: long, callback: Callback<long>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'periodReach' | 是 | 事件回调类型，支持的事件为'periodReach'，当采集的帧数达到frame参数的值时，触发该事件。 |
| frame | number | 是 | 触发事件的帧数。该值必须大于0。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<number> | 是 | 回调函数，返回frame参数的值。 |

## on('stateChange')

```TypeScript
on(type: 'stateChange', callback: Callback<AudioState>): void
```

监听状态变化事件（当AudioCapturer状态发生变化时触发）。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioCapturer-on(type: 'stateChange', callback: Callback<AudioState>): void--><!--Device-AudioCapturer-on(type: 'stateChange', callback: Callback<AudioState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 事件回调类型，支持的事件为'stateChange'，当AudioCapturer状态发生变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AudioState> | 是 | 回调函数，返回当前音频的状态。 |

## on('audioInterrupt')

```TypeScript
on(type: 'audioInterrupt', callback: Callback<InterruptEvent>): void
```

监听音频中断事件（当音频焦点发生变化时触发）。使用callback异步回调。

AudioCapturer对象在start事件时获取焦点，在pause、stop等事件时释放焦点，无需开发者主动申请。

调用此方法后，如果AudioCapturer对象获取焦点失败或发生中断事件（如被其他音频打断等），会收到[InterruptEvent](arkts-audio-audio-interruptevent-i.md)。建议应用根据InterruptEvent的信息进行进一步处理。更多信息请参阅文档[音频焦点介绍](../../../../media/audio/audio-playback-concurrency.md)。

**起始版本：** 10

<!--Device-AudioCapturer-on(type: 'audioInterrupt', callback: Callback<InterruptEvent>): void--><!--Device-AudioCapturer-on(type: 'audioInterrupt', callback: Callback<InterruptEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Interrupt

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | 是 | 事件回调类型，支持的事件为'audioInterrupt'，当音频焦点状态发生变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<InterruptEvent> | 是 | 回调函数，返回中断事件信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('inputDeviceChange')

```TypeScript
on(type: 'inputDeviceChange', callback: Callback<AudioDeviceDescriptors>): void
```

监听音频输入设备变化事件（当音频输入设备发生变化时触发）。使用callback异步回调。

**起始版本：** 11

<!--Device-AudioCapturer-on(type: 'inputDeviceChange', callback: Callback<AudioDeviceDescriptors>): void--><!--Device-AudioCapturer-on(type: 'inputDeviceChange', callback: Callback<AudioDeviceDescriptors>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'inputDeviceChange' | 是 | 事件回调类型，支持的事件为'inputDeviceChange'，当音频输入设备发生变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AudioDeviceDescriptors> | 是 | 回调函数，返回变化后的音频输入设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('audioCapturerChange')

```TypeScript
on(type: 'audioCapturerChange', callback: Callback<AudioCapturerChangeInfo>): void
```

监听录音流配置变化事件（当音频录制流状态变化、设备变化时触发）。使用callback异步回调。订阅内部是异步实现，是非精确回调，在录音流配置变化的同时注册回调，收到的返回结果存在变化可能性。

**起始版本：** 11

<!--Device-AudioCapturer-on(type: 'audioCapturerChange', callback: Callback<AudioCapturerChangeInfo>): void--><!--Device-AudioCapturer-on(type: 'audioCapturerChange', callback: Callback<AudioCapturerChangeInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioCapturerChange' | 是 | 事件回调类型，支持的事件为'audioCapturerChange'，当音频录制流状态变化、设备变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AudioCapturerChangeInfo> | 是 | 回调函数，录音流配置或状态变化时返回监听的录音流当前配置和状态信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('readData')

```TypeScript
on(type: 'readData', callback: Callback<ArrayBuffer>): void
```

监听音频数据读取回调事件（当需要读取音频流数据时触发）。使用callback异步回调。

回调函数仅用来读取音频数据，请勿在回调函数中调用AudioCapturer相关接口。

为了消除麦克风硬件设计带来的上电杂音，通常会对录音启动后的前100ms数据进行静音。

**起始版本：** 11

<!--Device-AudioCapturer-on(type: 'readData', callback: Callback<ArrayBuffer>): void--><!--Device-AudioCapturer-on(type: 'readData', callback: Callback<ArrayBuffer>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'readData' | 是 | 事件回调类型，支持的事件为'readData'，当需要读取音频流数据时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<ArrayBuffer> | 是 | 回调函数，返回读到的数据缓冲区。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## read

```TypeScript
read(size: number, isBlockingRead: boolean, callback: AsyncCallback<ArrayBuffer>): void
```

读入缓冲区。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** event:readData

<!--Device-AudioCapturer-read(size: number, isBlockingRead: boolean, callback: AsyncCallback<ArrayBuffer>): void--><!--Device-AudioCapturer-read(size: number, isBlockingRead: boolean, callback: AsyncCallback<ArrayBuffer>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 读入的字节数。 |
| isBlockingRead | boolean | 是 | 是否阻塞读操作。true表示阻塞，false表示不阻塞。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<ArrayBuffer> | 是 | 回调函数。当读入缓冲区成功，err为undefined，data为获取到的缓冲区；否则为错误对象。 |

## read

```TypeScript
read(size: number, isBlockingRead: boolean): Promise<ArrayBuffer>
```

读入缓冲区。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** event:readData

<!--Device-AudioCapturer-read(size: number, isBlockingRead: boolean): Promise<ArrayBuffer>--><!--Device-AudioCapturer-read(size: number, isBlockingRead: boolean): Promise<ArrayBuffer>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 读入的字节数。 |
| isBlockingRead | boolean | 是 | 是否阻塞读操作。true表示阻塞，false表示不阻塞。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ArrayBuffer> | Promise对象，返回读取的缓冲区数据。 |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放音频采集器。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioCapturer-release(callback: AsyncCallback<void>): void--><!--Device-AudioCapturer-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当释放音频采集器成功，err为undefined，否则为错误对象。 |

## release

```TypeScript
release(): Promise<void>
```

释放音频采集器。使用Promise异步回调。

**起始版本：** 8

<!--Device-AudioCapturer-release(): Promise<void>--><!--Device-AudioCapturer-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

## requestPlaybackCaptureStart

```TypeScript
requestPlaybackCaptureStart(callback: Callback<PlaybackCaptureStartState>): void
```

请求启动内录流接口，内录流只能通过该接口触发启动。使用callback异步回调。

内录是指以系统内部音频数据作为音频源的输入类型，简称为内录，对应的流称为内录流。常用于录制目标设备应用发送到系统以供播放的音频。

该接口为非阻塞接口，系统接收到内录启动请求后，会继续处理用户授权检查和内录流启动，最终结果通过回调函数返回。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturer-requestPlaybackCaptureStart(callback: Callback<PlaybackCaptureStartState>): void--><!--Device-AudioCapturer-requestPlaybackCaptureStart(callback: Callback<PlaybackCaptureStartState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<PlaybackCaptureStartState> | 是 | 回调函数，用于接收启动内录请求的最终结果。 |

## setIndependentAudioSessionStrategy

```TypeScript
setIndependentAudioSessionStrategy(strategy: AudioSessionStrategy, behavior: number): void
```

设置独立的音频会话策略和行为参数。

> **说明：**  
>  
> 当音频采集器在运行状态时调用此接口后，必须重新调用接口[start](arkts-audio-audio-audiocapturer-i.md#start-1)使其生效。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturer-setIndependentAudioSessionStrategy(strategy: AudioSessionStrategy, behavior: int): void--><!--Device-AudioCapturer-setIndependentAudioSessionStrategy(strategy: AudioSessionStrategy, behavior: int): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strategy | [AudioSessionStrategy](arkts-audio-audio-audiosessionstrategy-i.md) | 是 | 音频会话策略。 |
| behavior | number | 是 | 用于设置音频会话行为。<br>该参数可以是单个标志，也可以是多个标志的按位OR组合。<br>当前支持的音频会话行为详见[AudioSessionBehaviorFlags](arkts-audio-audio-audiosessionbehaviorflags-e.md)中定义的标志。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Operation not permit at current state. |

## setMuteHint

```TypeScript
setMuteHint(mute: boolean): Promise<void>
```

应用将当前录音流的自身静音状态传递给系统音频模块。<!--RP1-->该接口不会触发录音流静音，当前仅在部分PC/2in1设备上用于优化设备功耗。<!--RP1End-->使用Promise异步回调。

> **说明：**  
>  
> - 该接口用于向系统音频模块上报应用自身的静音状态，不会改变录音流的实际静音状态。  
>  
> - 该接口仅在录音流处于运行态时允许调用，否则返回错误码6800103。  
>  
> - 同一录音流同时设置流级静音提示接口（本接口）和会话级静音提示接口  
> [AudioSessionManager.setCapturerMuteHint](arkts-audio-audio-audiosessionmanager-i.md#setcapturermutehint-1)时，流级  
> [setMuteHint](arkts-audio-audio-audiocapturer-i.md#setmutehint-1)优先级更高，数值以流级设置值为准。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturer-setMuteHint(mute: boolean): Promise<void>--><!--Device-AudioCapturer-setMuteHint(mute: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | 应用自身给系统音频模块上报的静音状态。true表示应用将当前流静音，false表示取消静音。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Operation not permitted at current state, stream is not running. |

## setNoiseReductionMode

```TypeScript
setNoiseReductionMode(noiseReductionMode: NoiseReductionMode): void
```

设置当前音频捕获器的降噪模式。支持的模式需要通过{@link#getSupportedNoiseReduceModes}获取。实际效果可能因不同的音频设备而异，当有多个时将无效同时运行的录制流。只能在已创建和已停止状态下更改模式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturer-setNoiseReductionMode(noiseReductionMode: NoiseReductionMode): void--><!--Device-AudioCapturer-setNoiseReductionMode(noiseReductionMode: NoiseReductionMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| noiseReductionMode | [NoiseReductionMode](arkts-audio-audio-noisereductionmode-e.md) | 是 | 要设置的降噪模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Illegal state, audio capturer is in running or released state. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | The setted mode is not supported. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio server process died. |

## setWillMuteWhenInterrupted

```TypeScript
setWillMuteWhenInterrupted(muteWhenInterrupted: boolean): Promise<void>
```

设置当前录制音频流是否启用[静音打断模式](../../../../media/audio/using-audiocapturer-for-recording.md#设置静音打断模式)。使用Promise异步回调。

**起始版本：** 20

<!--Device-AudioCapturer-setWillMuteWhenInterrupted(muteWhenInterrupted: boolean): Promise<void>--><!--Device-AudioCapturer-setWillMuteWhenInterrupted(muteWhenInterrupted: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| muteWhenInterrupted | boolean | 是 | 设置当前录制音频流是否启用静音打断模式, true表示启用，false表示不启用，保持为默认打断模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Operation not permitted at current state. |

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

启动音频采集器，开始获取音频数据。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioCapturer-start(callback: AsyncCallback<void>): void--><!--Device-AudioCapturer-start(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当启动音频采集器成功，err为undefined，否则为错误对象。异常将返回error对象：<br>错误码6800301：表示包含状态检查异常、焦点抢占失败、系统处理异常（具体错误查看系统日志）。 |

## start

```TypeScript
start(): Promise<void>
```

启动音频采集器，开始获取音频数据。使用Promise异步回调。

**起始版本：** 8

<!--Device-AudioCapturer-start(): Promise<void>--><!--Device-AudioCapturer-start(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，成功表示启动音频采集器成功。异常将返回error对象：<br>错误码6800301：表示包含状态检查异常、焦点抢占失败、系统处理异常（具体错误查看系统日志）。 |

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

停止音频采集器，停止输入音频流。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioCapturer-stop(callback: AsyncCallback<void>): void--><!--Device-AudioCapturer-stop(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当停止音频采集成功，err为undefined，否则为错误对象。 |

## stop

```TypeScript
stop(): Promise<void>
```

停止音频采集器，停止输入音频流。使用Promise异步回调。

**起始版本：** 8

<!--Device-AudioCapturer-stop(): Promise<void>--><!--Device-AudioCapturer-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

## state

```TypeScript
readonly state: AudioState
```

音频采集器状态。

**类型：** AudioState

**起始版本：** 8

<!--Device-AudioCapturer-readonly state: AudioState--><!--Device-AudioCapturer-readonly state: AudioState-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

