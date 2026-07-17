# AudioRenderer

提供音频渲染的相关接口。

在使用AudioRenderer的接口之前，需先通过[createAudioRenderer](arkts-audio-audio-createaudiorenderer-f.md#createaudiorenderer-1)获取AudioRenderer实例。

> **说明：**  
>  
> - 本Interface首批接口从API version 8开始支持。

**起始版本：** 8

<!--Device-audio-interface AudioRenderer--><!--Device-audio-interface AudioRenderer-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## drain

```TypeScript
drain(callback: AsyncCallback<void>): void
```

检查缓冲区是否已被耗尽。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-drain(callback: AsyncCallback<void>): void--><!--Device-AudioRenderer-drain(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当检查缓冲区是否已被耗尽成功，err为undefined，否则为错误对象。 |

## drain

```TypeScript
drain(): Promise<void>
```

检查缓冲区是否已被耗尽。使用Promise异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-drain(): Promise<void>--><!--Device-AudioRenderer-drain(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

## flush

```TypeScript
flush(): Promise<void>
```

清空缓冲区（[AudioState](arkts-audio-audio-audiostate-e.md)为STATE_RUNNING、STATE_PAUSED、STATE_STOPPED状态下可用）。使用Promise异步回调。

**起始版本：** 11

<!--Device-AudioRenderer-flush(): Promise<void>--><!--Device-AudioRenderer-flush(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Operation not permit at current state. Return by promise. |

## getAudioEffectMode

```TypeScript
getAudioEffectMode(callback: AsyncCallback<AudioEffectMode>): void
```

获取当前音效模式。使用callback异步回调。

**起始版本：** 10

<!--Device-AudioRenderer-getAudioEffectMode(callback: AsyncCallback<AudioEffectMode>): void--><!--Device-AudioRenderer-getAudioEffectMode(callback: AsyncCallback<AudioEffectMode>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<AudioEffectMode> | 是 | 回调函数。当获取当前音效模式成功，err为undefined，data为获取到的当前音效模式；否则为错误对象。 |

## getAudioEffectMode

```TypeScript
getAudioEffectMode(): Promise<AudioEffectMode>
```

获取当前音效模式。使用Promise异步回调。

**起始版本：** 10

<!--Device-AudioRenderer-getAudioEffectMode(): Promise<AudioEffectMode>--><!--Device-AudioRenderer-getAudioEffectMode(): Promise<AudioEffectMode>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<AudioEffectMode> | Promise对象，返回当前音效模式。 |

## getAudioStreamId

```TypeScript
getAudioStreamId(callback: AsyncCallback<number>): void
```

获取音频流id。使用callback异步回调。

**起始版本：** 9

<!--Device-AudioRenderer-getAudioStreamId(callback: AsyncCallback<long>): void--><!--Device-AudioRenderer-getAudioStreamId(callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

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

<!--Device-AudioRenderer-getAudioStreamId(): Promise<long>--><!--Device-AudioRenderer-getAudioStreamId(): Promise<long>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

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

<!--Device-AudioRenderer-getAudioStreamIdSync(): long--><!--Device-AudioRenderer-getAudioStreamIdSync(): long-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回音频流id。 |

## getAudioTime

```TypeScript
getAudioTime(callback: AsyncCallback<number>): void
```

获取当前播放位置的时间戳（从1970年1月1日开始），单位为纳秒。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-getAudioTime(callback: AsyncCallback<long>): void--><!--Device-AudioRenderer-getAudioTime(callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。当获取时间戳成功，err为undefined，data为获取到的时间戳；否则为错误对象。 |

## getAudioTime

```TypeScript
getAudioTime(): Promise<number>
```

获取当前播放位置的时间戳（从1970年1月1日开始），单位为纳秒。使用Promise异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-getAudioTime(): Promise<long>--><!--Device-AudioRenderer-getAudioTime(): Promise<long>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回时间戳。 |

## getAudioTimeSync

```TypeScript
getAudioTimeSync(): number
```

获取当前播放位置的时间戳（从1970年1月1日开始），单位为纳秒。同步返回结果。

**起始版本：** 10

<!--Device-AudioRenderer-getAudioTimeSync(): long--><!--Device-AudioRenderer-getAudioTimeSync(): long-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回时间戳。 |

## getAudioTimestampInfo

```TypeScript
getAudioTimestampInfo(): Promise<AudioTimestampInfo>
```

获取输出音频流时间戳和位置信息，适配倍速接口。使用Promise异步回调。

获取输出音频流时间戳和位置信息，通常用于进行音画同步对齐。

注意，当实际播放位置（framePosition）为0时，时间戳（timestamp）是固定值，直到流真正开始播放时才会更新。当调用Flush接口时实际播放位置也会被重置。

当音频流路由（route）变化时，例如设备变化或者输出类型变化时，播放位置也会被重置，但此时时间戳仍会持续增长。推荐当实际播放位置和时间戳的变化稳定后再使用该接口获取的值。该接口适配倍速接口，例如当播放速度设置为2倍时，播放位置的增长速度也会返回为正常的2倍。

**起始版本：** 19

<!--Device-AudioRenderer-getAudioTimestampInfo(): Promise<AudioTimestampInfo>--><!--Device-AudioRenderer-getAudioTimestampInfo(): Promise<AudioTimestampInfo>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

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

<!--Device-AudioRenderer-getAudioTimestampInfoSync(): AudioTimestampInfo--><!--Device-AudioRenderer-getAudioTimestampInfoSync(): AudioTimestampInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

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

获取音频渲染器的最小缓冲区大小。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-getBufferSize(callback: AsyncCallback<long>): void--><!--Device-AudioRenderer-getBufferSize(callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。当获取音频渲染器的最小缓冲区大小成功，err为undefined，data为获取到的最小缓冲区大小；否则为错误对象。<br>单位为字节。 |

## getBufferSize

```TypeScript
getBufferSize(): Promise<number>
```

获取音频渲染器的最小缓冲区大小。使用Promise异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-getBufferSize(): Promise<long>--><!--Device-AudioRenderer-getBufferSize(): Promise<long>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回缓冲区大小。<br>单位为字节。 |

## getBufferSizeSync

```TypeScript
getBufferSizeSync(): number
```

获取音频渲染器的最小缓冲区大小。同步返回结果。

**起始版本：** 10

<!--Device-AudioRenderer-getBufferSizeSync(): long--><!--Device-AudioRenderer-getBufferSizeSync(): long-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回缓冲区大小，单位为字节。 |

## getCurrentOutputDevices

```TypeScript
getCurrentOutputDevices(callback: AsyncCallback<AudioDeviceDescriptors>): void
```

获取音频流输出设备信息。使用callback异步回调。

**起始版本：** 10

<!--Device-AudioRenderer-getCurrentOutputDevices(callback: AsyncCallback<AudioDeviceDescriptors>): void--><!--Device-AudioRenderer-getCurrentOutputDevices(callback: AsyncCallback<AudioDeviceDescriptors>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<AudioDeviceDescriptors> | 是 | 回调函数。当获取音频流输出设备信息成功，err为undefined，data为获取到的音频流输出设备信息；否则为错误对象。 |

## getCurrentOutputDevices

```TypeScript
getCurrentOutputDevices(): Promise<AudioDeviceDescriptors>
```

获取音频流输出设备信息。使用Promise异步回调。

**起始版本：** 10

<!--Device-AudioRenderer-getCurrentOutputDevices(): Promise<AudioDeviceDescriptors>--><!--Device-AudioRenderer-getCurrentOutputDevices(): Promise<AudioDeviceDescriptors>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<AudioDeviceDescriptors> | Promise对象，返回音频流的输出设备信息。 |

## getCurrentOutputDevicesSync

```TypeScript
getCurrentOutputDevicesSync(): AudioDeviceDescriptors
```

获取音频流输出设备信息。同步返回结果。

**起始版本：** 10

<!--Device-AudioRenderer-getCurrentOutputDevicesSync(): AudioDeviceDescriptors--><!--Device-AudioRenderer-getCurrentOutputDevicesSync(): AudioDeviceDescriptors-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | 返回音频流的输出设备信息。 |

## getLatency

```TypeScript
getLatency(type: AudioLatencyType): number
```

获取当前音频路由的预估时延。

> **说明：**  
>  
> - 无线连接的音频设备，时延估算会存在误差，结果仅供参考。  
>  
> - 由于时延未计入实时缓冲区，建议仅在音频播放开始时获取，避免频繁调用，否则可能因路由切换而阻塞该接口调用。  
>  
> - 音频输出到硬件后的音画同步建议使用[getAudioTimestampInfo](arkts-audio-audio-audiorenderer-i.md#getaudiotimestampinfo-1)或  
> [getAudioTimestampInfoSync](arkts-audio-audio-audiorenderer-i.md#getaudiotimestampinfosync-1)完成。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioRenderer-getLatency(type: AudioLatencyType): int--><!--Device-AudioRenderer-getLatency(type: AudioLatencyType): int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [AudioLatencyType](arkts-audio-audio-audiolatencytype-e.md) | 是 | 获取的时延类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回音频时延，单位为毫秒。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Operation not permitted in release state. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System internal error, like audio service error. |

## getLoudnessGain

```TypeScript
getLoudnessGain(): number
```

获取播放响度。

**起始版本：** 20

<!--Device-AudioRenderer-getLoudnessGain(): double--><!--Device-AudioRenderer-getLoudnessGain(): double-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回播放的响度值，单位为分贝。 |

## getMaxStreamVolume

```TypeScript
getMaxStreamVolume(callback: AsyncCallback<number>): void
```

获取音频流的最大音量。使用callback异步回调。

**起始版本：** 10

<!--Device-AudioRenderer-getMaxStreamVolume(callback: AsyncCallback<double>): void--><!--Device-AudioRenderer-getMaxStreamVolume(callback: AsyncCallback<double>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。当获取音频流的最大音量成功，err为undefined，data为获取到的应用基于音频流的最大音量；否则为错误对象。<br>音量范围为[0.0, 1.0]。 |

## getMaxStreamVolume

```TypeScript
getMaxStreamVolume(): Promise<number>
```

获取音频流的最大音量。使用Promise异步回调。

**起始版本：** 10

<!--Device-AudioRenderer-getMaxStreamVolume(): Promise<double>--><!--Device-AudioRenderer-getMaxStreamVolume(): Promise<double>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回音频流最大音量。<br>音量范围为[0.0, 1.0]。 |

## getMaxStreamVolumeSync

```TypeScript
getMaxStreamVolumeSync(): number
```

获取音频流的最大音量。同步返回结果。

**起始版本：** 10

<!--Device-AudioRenderer-getMaxStreamVolumeSync(): double--><!--Device-AudioRenderer-getMaxStreamVolumeSync(): double-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回音频流最大音量，音量范围为[0.0, 1.0]。 |

## getMinStreamVolume

```TypeScript
getMinStreamVolume(callback: AsyncCallback<number>): void
```

获取音频流的最小音量。使用callback异步回调。

**起始版本：** 10

<!--Device-AudioRenderer-getMinStreamVolume(callback: AsyncCallback<double>): void--><!--Device-AudioRenderer-getMinStreamVolume(callback: AsyncCallback<double>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。当获取音频流的最小音量成功，err为undefined，data为获取到的应用基于音频流的最小音量；否则为错误对象。<br>音量范围为[0.0, 1.0]。 |

## getMinStreamVolume

```TypeScript
getMinStreamVolume(): Promise<number>
```

获取音频流的最小音量。使用Promise异步回调。

**起始版本：** 10

<!--Device-AudioRenderer-getMinStreamVolume(): Promise<double>--><!--Device-AudioRenderer-getMinStreamVolume(): Promise<double>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回音频流最小音量。<br>音量范围为[0.0, 1.0]。 |

## getMinStreamVolumeSync

```TypeScript
getMinStreamVolumeSync(): number
```

获取音频流的最小音量。同步返回结果。

**起始版本：** 10

<!--Device-AudioRenderer-getMinStreamVolumeSync(): double--><!--Device-AudioRenderer-getMinStreamVolumeSync(): double-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回音频流最小音量，音量范围为[0.0, 1.0]。 |

## getRenderRate

```TypeScript
getRenderRate(callback: AsyncCallback<AudioRendererRate>): void
```

获取音频渲染速率。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** getSpeed

<!--Device-AudioRenderer-getRenderRate(callback: AsyncCallback<AudioRendererRate>): void--><!--Device-AudioRenderer-getRenderRate(callback: AsyncCallback<AudioRendererRate>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<AudioRendererRate> | 是 | 回调函数。当获取当前渲染速率成功，err为undefined，data为获取到的当前渲染速率；否则为错误对象。 |

## getRenderRate

```TypeScript
getRenderRate(): Promise<AudioRendererRate>
```

获取音频渲染速率。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** getSpeed

<!--Device-AudioRenderer-getRenderRate(): Promise<AudioRendererRate>--><!--Device-AudioRenderer-getRenderRate(): Promise<AudioRendererRate>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<AudioRendererRate> | Promise对象，返回渲染速率。 |

## getRenderRateSync

```TypeScript
getRenderRateSync(): AudioRendererRate
```

获取音频渲染速率。同步返回结果。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** getSpeed

<!--Device-AudioRenderer-getRenderRateSync(): AudioRendererRate--><!--Device-AudioRenderer-getRenderRateSync(): AudioRendererRate-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioRendererRate](arkts-audio-audio-audiorendererrate-e.md) | 返回渲染速率。 |

## getRendererInfo

```TypeScript
getRendererInfo(callback: AsyncCallback<AudioRendererInfo>): void
```

获取当前创建的音频渲染器信息。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-getRendererInfo(callback: AsyncCallback<AudioRendererInfo>): void--><!--Device-AudioRenderer-getRendererInfo(callback: AsyncCallback<AudioRendererInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<AudioRendererInfo> | 是 | 回调函数。当获取音频渲染器的信息成功，err为undefined，data为获取到的音频渲染器的信息；否则为错误对象。 |

## getRendererInfo

```TypeScript
getRendererInfo(): Promise<AudioRendererInfo>
```

获取当前创建的音频渲染器信息。使用Promise异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-getRendererInfo(): Promise<AudioRendererInfo>--><!--Device-AudioRenderer-getRendererInfo(): Promise<AudioRendererInfo>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<AudioRendererInfo> | Promise对象，返回音频渲染器信息。 |

## getRendererInfoSync

```TypeScript
getRendererInfoSync(): AudioRendererInfo
```

获取当前创建的音频渲染器信息。同步返回结果。

**起始版本：** 10

<!--Device-AudioRenderer-getRendererInfoSync(): AudioRendererInfo--><!--Device-AudioRenderer-getRendererInfoSync(): AudioRendererInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md) | 返回音频渲染器信息。 |

## getSilentModeAndMixWithOthers

```TypeScript
getSilentModeAndMixWithOthers(): boolean
```

获取静音并发播放模式。

**起始版本：** 12

<!--Device-AudioRenderer-getSilentModeAndMixWithOthers(): boolean--><!--Device-AudioRenderer-getSilentModeAndMixWithOthers(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 静音并发播放模式状态。返回true表示打开，返回false表示关闭。 |

## getSpeed

```TypeScript
getSpeed(): number
```

获取播放倍速。

**起始版本：** 11

<!--Device-AudioRenderer-getSpeed(): double--><!--Device-AudioRenderer-getSpeed(): double-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回播放的倍速值，倍速范围为[0.25, 4.0]。 |

## getStreamInfo

```TypeScript
getStreamInfo(callback: AsyncCallback<AudioStreamInfo>): void
```

获取音频流信息。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-getStreamInfo(callback: AsyncCallback<AudioStreamInfo>): void--><!--Device-AudioRenderer-getStreamInfo(callback: AsyncCallback<AudioStreamInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<AudioStreamInfo> | 是 | 回调函数。当获取音频流信息成功，err为undefined，data为获取到的音频流信息；否则为错误对象。 |

## getStreamInfo

```TypeScript
getStreamInfo(): Promise<AudioStreamInfo>
```

获取音频流信息。使用Promise异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-getStreamInfo(): Promise<AudioStreamInfo>--><!--Device-AudioRenderer-getStreamInfo(): Promise<AudioStreamInfo>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<AudioStreamInfo> | Promise对象，返回音频流信息。 |

## getStreamInfoSync

```TypeScript
getStreamInfoSync(): AudioStreamInfo
```

获取音频流信息。同步返回结果。

**起始版本：** 10

<!--Device-AudioRenderer-getStreamInfoSync(): AudioStreamInfo--><!--Device-AudioRenderer-getStreamInfoSync(): AudioStreamInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md) | 返回音频流信息。 |

## getUnderflowCount

```TypeScript
getUnderflowCount(callback: AsyncCallback<number>): void
```

获取当前播放音频流的欠载音频帧数量。使用callback异步回调。

**起始版本：** 10

<!--Device-AudioRenderer-getUnderflowCount(callback: AsyncCallback<long>): void--><!--Device-AudioRenderer-getUnderflowCount(callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。当获取当前播放音频流的欠载音频帧数量成功，err为undefined，data为获取到的当前播放音频流的欠载音频帧数量；否则为错误对象。 |

## getUnderflowCount

```TypeScript
getUnderflowCount(): Promise<number>
```

获取当前播放音频流的欠载音频帧数量。使用Promise异步回调。

**起始版本：** 10

<!--Device-AudioRenderer-getUnderflowCount(): Promise<long>--><!--Device-AudioRenderer-getUnderflowCount(): Promise<long>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回音频流的欠载音频帧数量。 |

## getUnderflowCountSync

```TypeScript
getUnderflowCountSync(): number
```

获取当前播放音频流的欠载音频帧数量，同步返回数据。

**起始版本：** 10

<!--Device-AudioRenderer-getUnderflowCountSync(): long--><!--Device-AudioRenderer-getUnderflowCountSync(): long-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回音频流的欠载音频帧数量。 |

## getVolume

```TypeScript
getVolume(): number
```

获取音频流的音量。同步返回结果。

**起始版本：** 12

<!--Device-AudioRenderer-getVolume(): double--><!--Device-AudioRenderer-getVolume(): double-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回音量大小，音量值范围为[0.0, 1.0]。 |

## off('audioInterrupt')

```TypeScript
off(type: 'audioInterrupt', callback?: Callback<InterruptEvent>): void
```

取消监听音频中断事件。使用callback异步回调。

**起始版本：** 18

<!--Device-AudioRenderer-off(type: 'audioInterrupt', callback?: Callback<InterruptEvent>): void--><!--Device-AudioRenderer-off(type: 'audioInterrupt', callback?: Callback<InterruptEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Interrupt

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | 是 | 事件回调类型，支持的事件为'audioInterrupt'，当取消监听音频中断事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<InterruptEvent> | 否 | 回调函数，返回中断事件信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off('markReach')

```TypeScript
off(type: 'markReach', callback?: Callback<number>): void
```

取消监听标记到达事件。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-off(type: 'markReach', callback?: Callback<long>): void--><!--Device-AudioRenderer-off(type: 'markReach', callback?: Callback<long>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

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

<!--Device-AudioRenderer-off(type: 'periodReach', callback?: Callback<long>): void--><!--Device-AudioRenderer-off(type: 'periodReach', callback?: Callback<long>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

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

<!--Device-AudioRenderer-off(type: 'stateChange', callback?: Callback<AudioState>): void--><!--Device-AudioRenderer-off(type: 'stateChange', callback?: Callback<AudioState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 事件回调类型，支持的事件为'stateChange'，当取消监听状态变化事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AudioState> | 否 | 回调函数，返回当前音频的状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off('outputDeviceChange')

```TypeScript
off(type: 'outputDeviceChange', callback?: Callback<AudioDeviceDescriptors>): void
```

取消监听音频输出设备变化事件。使用callback异步回调。

**起始版本：** 10

<!--Device-AudioRenderer-off(type: 'outputDeviceChange', callback?: Callback<AudioDeviceDescriptors>): void--><!--Device-AudioRenderer-off(type: 'outputDeviceChange', callback?: Callback<AudioDeviceDescriptors>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'outputDeviceChange' | 是 | 事件回调类型，支持的事件为'outputDeviceChange'，当取消监听音频输出设备变化事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AudioDeviceDescriptors> | 否 | 回调函数，返回当前音频流的输出设备描述信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off('outputDeviceChangeWithInfo')

```TypeScript
off(type: 'outputDeviceChangeWithInfo', callback?: Callback<AudioStreamDeviceChangeInfo>): void
```

取消监听音频流输出设备变化及原因事件。使用callback异步回调。

**起始版本：** 11

<!--Device-AudioRenderer-off(type: 'outputDeviceChangeWithInfo', callback?: Callback<AudioStreamDeviceChangeInfo>): void--><!--Device-AudioRenderer-off(type: 'outputDeviceChangeWithInfo', callback?: Callback<AudioStreamDeviceChangeInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'outputDeviceChangeWithInfo' | 是 | 事件回调类型，支持的事件为'outputDeviceChangeWithInfo'，当取消监听音频流输出设备变化及原因事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AudioStreamDeviceChangeInfo> | 否 | 回调函数，返回当前音频流的输出设备描述信息及变化原因。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off('writeData')

```TypeScript
off(type: 'writeData', callback?: AudioRendererWriteDataCallback): void
```

取消监听音频数据写入回调事件。使用callback异步回调。

**起始版本：** 11

<!--Device-AudioRenderer-off(type: 'writeData', callback?: AudioRendererWriteDataCallback): void--><!--Device-AudioRenderer-off(type: 'writeData', callback?: AudioRendererWriteDataCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'writeData' | 是 | 事件回调类型，支持的事件为'writeData'，当取消监听音频数据写入回调事件时，触发该事件。 |
| callback | [AudioRendererWriteDataCallback](arkts-audio-audio-audiorendererwritedatacallback-t.md) | 否 | 回调函数，入参代表应用接收待写入的数据缓冲区。<br>API version 11 不支持返回回调结果，从 API version 12 开始支持返回回调结果[AudioDataCallbackResult](arkts-audio-audio-audiodatacallbackresult-e.md)。<br>**起始版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('audioInterrupt')

```TypeScript
on(type: 'audioInterrupt', callback: Callback<InterruptEvent>): void
```

监听音频中断事件（当音频焦点发生变化时触发）。使用callback异步回调。

AudioRenderer对象在start事件时获取焦点，在pause、stop等事件时释放焦点，无需开发者主动申请。

调用此方法后，如果AudioRenderer对象获取焦点失败或发生中断事件（如被其他音频打断等），会收到[InterruptEvent](arkts-audio-audio-interruptevent-i.md)。建议应用根据InterruptEvent的信息进行进一步处理。更多信息请参阅文档[音频焦点介绍](../../../../media/audio/audio-playback-concurrency.md)。

**起始版本：** 9

<!--Device-AudioRenderer-on(type: 'audioInterrupt', callback: Callback<InterruptEvent>): void--><!--Device-AudioRenderer-on(type: 'audioInterrupt', callback: Callback<InterruptEvent>): void-End-->

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

## on('markReach')

```TypeScript
on(type: 'markReach', frame: number, callback: Callback<number>): void
```

监听标记到达事件（当渲染的帧数到达frame参数的值时触发，仅调用一次）。使用callback异步回调。

如果将frame设置为100，当渲染帧数到达第100帧时，系统将上报信息。

**起始版本：** 8

<!--Device-AudioRenderer-on(type: 'markReach', frame: long, callback: Callback<long>): void--><!--Device-AudioRenderer-on(type: 'markReach', frame: long, callback: Callback<long>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'markReach' | 是 | 事件回调类型，支持的事件为'markReach'，当渲染的帧数到达frame参数的值时，触发该事件。 |
| frame | number | 是 | 触发事件的帧数。该值必须大于0。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<number> | 是 | 回调函数，返回frame参数的值。 |

## on('periodReach')

```TypeScript
on(type: 'periodReach', frame: number, callback: Callback<number>): void
```

监听标记到达事件（每当渲染的帧数达到frame参数的值时触发，即按周期上报信息）。使用callback异步回调。

如果将frame设置为10，每渲染10帧数据均会上报信息（例如：第10帧、第20帧、第30帧......）。

**起始版本：** 8

<!--Device-AudioRenderer-on(type: 'periodReach', frame: long, callback: Callback<long>): void--><!--Device-AudioRenderer-on(type: 'periodReach', frame: long, callback: Callback<long>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'periodReach' | 是 | 事件回调类型，支持的事件为'periodReach'，当渲染的帧数达到frame参数的值时，触发该事件。 |
| frame | number | 是 | 触发事件的帧数。该值必须大于 0。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<number> | 是 | 回调函数，返回frame参数的值。 |

## on('stateChange')

```TypeScript
on(type: 'stateChange', callback: Callback<AudioState>): void
```

监听状态变化事件（当AudioRenderer的状态发生变化时触发）。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-on(type: 'stateChange', callback: Callback<AudioState>): void--><!--Device-AudioRenderer-on(type: 'stateChange', callback: Callback<AudioState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 事件回调类型，支持的事件为'stateChange'，当AudioRenderer的状态发生变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AudioState> | 是 | 回调函数，返回当前音频的状态。 |

## on('outputDeviceChange')

```TypeScript
on(type: 'outputDeviceChange', callback: Callback<AudioDeviceDescriptors>): void
```

监听音频输出设备变化事件（当音频输出设备发生变化时触发）。使用callback异步回调。

**起始版本：** 10

<!--Device-AudioRenderer-on(type: 'outputDeviceChange', callback: Callback<AudioDeviceDescriptors>): void--><!--Device-AudioRenderer-on(type: 'outputDeviceChange', callback: Callback<AudioDeviceDescriptors>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'outputDeviceChange' | 是 | 事件回调类型，支持的事件为'outputDeviceChange'，当音频输出设备发生变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AudioDeviceDescriptors> | 是 | 回调函数，返回当前音频流的输出设备描述信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('outputDeviceChangeWithInfo')

```TypeScript
on(type: 'outputDeviceChangeWithInfo', callback: Callback<AudioStreamDeviceChangeInfo>): void
```

监听音频流输出设备变化及原因事件（当音频输出设备发生变化时触发）。使用callback异步回调。

**起始版本：** 11

<!--Device-AudioRenderer-on(type: 'outputDeviceChangeWithInfo', callback: Callback<AudioStreamDeviceChangeInfo>): void--><!--Device-AudioRenderer-on(type: 'outputDeviceChangeWithInfo', callback: Callback<AudioStreamDeviceChangeInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'outputDeviceChangeWithInfo' | 是 | 事件回调类型，支持的事件为'outputDeviceChangeWithInfo'，当音频输出设备发生变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AudioStreamDeviceChangeInfo> | 是 | 回调函数，返回当前音频流的输出设备描述信息及变化原因。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('writeData')

```TypeScript
on(type: 'writeData', callback: AudioRendererWriteDataCallback): void
```

监听音频数据写入回调事件（当需要写入音频数据时触发）。使用callback异步回调。

> **说明：**  
>  
> - 回调函数仅用来写入音频数据，请勿在回调函数中调用AudioRenderer相关接口。  
>  
> - 为避免音频播放启动和停止时数据不连续可能出现的杂音，系统通常会在启动和停止时对音频数据做20ms以内的淡入淡出处理。

**起始版本：** 11

<!--Device-AudioRenderer-on(type: 'writeData', callback: AudioRendererWriteDataCallback): void--><!--Device-AudioRenderer-on(type: 'writeData', callback: AudioRendererWriteDataCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'writeData' | 是 | 事件回调类型，支持的事件为'writeData'，当需要写入音频数据时，触发该事件。 |
| callback | [AudioRendererWriteDataCallback](arkts-audio-audio-audiorendererwritedatacallback-t.md) | 是 | 回调函数，入参代表应用接收待写入的数据缓冲区。<br>API version 11 不支持返回回调结果，从 API version 12 开始支持返回回调结果[AudioDataCallbackResult](arkts-audio-audio-audiodatacallbackresult-e.md)。<br>**起始版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## pause

```TypeScript
pause(callback: AsyncCallback<void>): void
```

暂停音频渲染。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-pause(callback: AsyncCallback<void>): void--><!--Device-AudioRenderer-pause(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当暂停渲染成功，err为undefined，否则为错误对象。 |

## pause

```TypeScript
pause(): Promise<void>
```

暂停音频渲染。使用Promise异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-pause(): Promise<void>--><!--Device-AudioRenderer-pause(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放音频渲染器。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-release(callback: AsyncCallback<void>): void--><!--Device-AudioRenderer-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当释放音频渲染器成功，err为undefined，否则为错误对象。 |

## release

```TypeScript
release(): Promise<void>
```

释放音频渲染器。使用Promise异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-release(): Promise<void>--><!--Device-AudioRenderer-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

## setAudioEffectMode

```TypeScript
setAudioEffectMode(mode: AudioEffectMode, callback: AsyncCallback<void>): void
```

设置当前音效模式。使用callback异步回调。

**起始版本：** 10

<!--Device-AudioRenderer-setAudioEffectMode(mode: AudioEffectMode, callback: AsyncCallback<void>): void--><!--Device-AudioRenderer-setAudioEffectMode(mode: AudioEffectMode, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AudioEffectMode](arkts-audio-audio-audioeffectmode-e.md) | 是 | 音效模式。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当设置当前音效模式成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by callback. |

## setAudioEffectMode

```TypeScript
setAudioEffectMode(mode: AudioEffectMode): Promise<void>
```

设置当前音效模式。使用Promise异步回调。

**起始版本：** 10

<!--Device-AudioRenderer-setAudioEffectMode(mode: AudioEffectMode): Promise<void>--><!--Device-AudioRenderer-setAudioEffectMode(mode: AudioEffectMode): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AudioEffectMode](arkts-audio-audio-audioeffectmode-e.md) | 是 | 音效模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by promise. |

## setChannelBlendMode

```TypeScript
setChannelBlendMode(mode: ChannelBlendMode): void
```

设置单双声道混合模式。同步返回结果。

**起始版本：** 11

<!--Device-AudioRenderer-setChannelBlendMode(mode: ChannelBlendMode): void--><!--Device-AudioRenderer-setChannelBlendMode(mode: ChannelBlendMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [ChannelBlendMode](arkts-audio-audio-channelblendmode-e.md) | 是 | 声道混合模式类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Operation not permit at current state. |

## setDefaultOutputDevice

```TypeScript
setDefaultOutputDevice(deviceType: DeviceType): Promise<void>
```

设置默认发声设备。使用Promise异步回调。

> **说明：**  
>  
> - 本接口仅适用于[StreamUsage](arkts-audio-audio-streamusage-e.md)为语音消息、VoIP语音通话或者VoIP视频通话的场景，支持听筒、扬声器和系统默认设备。  
>  
> - 本接口允许在AudioRenderer创建后随时调用，系统会记录应用设置的默认本机内置发声设备。应用启动播放时，若外接设备如蓝牙耳机或有线耳机已接入，系统优先从外接设备发声；否则，系统遵循应用设置的默认本机内置发声设  
> 备。

**起始版本：** 12

<!--Device-AudioRenderer-setDefaultOutputDevice(deviceType: DeviceType): Promise<void>--><!--Device-AudioRenderer-setDefaultOutputDevice(deviceType: DeviceType): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | [DeviceType](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-devicetype-e.md) | 是 | 设备类型。<br>仅支持以下设备：EARPIECE（听筒）、SPEAKER（扬声器）和DEFAULT（系统默认设备）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Operation not permit at current state. |

## setIndependentAudioSessionStrategy

```TypeScript
setIndependentAudioSessionStrategy(strategy: AudioSessionStrategy, behavior: number): void
```

设置独立的音频会话策略和行为参数。

> **说明：**  
>  
> 当音频渲染器在运行状态时调用此接口后，必须重新调用接口[start](arkts-audio-audio-audiorenderer-i.md#start-1)使其生效。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioRenderer-setIndependentAudioSessionStrategy(strategy: AudioSessionStrategy, behavior: int): void--><!--Device-AudioRenderer-setIndependentAudioSessionStrategy(strategy: AudioSessionStrategy, behavior: int): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

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

## setInterruptMode

```TypeScript
setInterruptMode(mode: InterruptMode, callback: AsyncCallback<void>): void
```

设置应用的焦点模型。使用callback异步回调。

**起始版本：** 9

<!--Device-AudioRenderer-setInterruptMode(mode: InterruptMode, callback: AsyncCallback<void>): void--><!--Device-AudioRenderer-setInterruptMode(mode: InterruptMode, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Interrupt

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [InterruptMode](arkts-audio-audio-interruptmode-e.md) | 是 | 焦点模型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当设置应用的焦点模型成功，err为undefined，否则为错误对象。 |

## setInterruptMode

```TypeScript
setInterruptMode(mode: InterruptMode): Promise<void>
```

设置应用的焦点模型。使用Promise异步回调。

**起始版本：** 9

<!--Device-AudioRenderer-setInterruptMode(mode: InterruptMode): Promise<void>--><!--Device-AudioRenderer-setInterruptMode(mode: InterruptMode): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Interrupt

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [InterruptMode](arkts-audio-audio-interruptmode-e.md) | 是 | 焦点模型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

## setInterruptModeSync

```TypeScript
setInterruptModeSync(mode: InterruptMode): void
```

设置应用的焦点模型。同步设置。

**起始版本：** 10

<!--Device-AudioRenderer-setInterruptModeSync(mode: InterruptMode): void--><!--Device-AudioRenderer-setInterruptModeSync(mode: InterruptMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Interrupt

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [InterruptMode](arkts-audio-audio-interruptmode-e.md) | 是 | 焦点模型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## setLoudnessGain

```TypeScript
setLoudnessGain(loudnessGain: number): Promise<void>
```

设置播放响度。使用Promise异步回调。

> **说明：**  
>  
> - 该接口仅支持类型为[STREAM_USAGE_MUSIC](arkts-audio-audio-streamusage-e.md)、[STREAM_USAGE_MOVIE](arkts-audio-audio-streamusage-e.md)或  
> [STREAM_USAGE_AUDIOBOOK](arkts-audio-audio-streamusage-e.md)的音频流。  
>  
> - 该接口不支持高清通路的响度设置。  
>  
> - 由于音频框架与硬件之间存在缓冲区，响度调节实际生效存在延迟，时长取决于缓冲区长度。  
>  
> - 建议在不同音频开始播放前预先设置响度，以实现最佳均衡效果。

**起始版本：** 20

<!--Device-AudioRenderer-setLoudnessGain(loudnessGain: double): Promise<void>--><!--Device-AudioRenderer-setLoudnessGain(loudnessGain: double): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| loudnessGain | number | 是 | 设置播放的响度值，单位为dB，响度范围为[-90.0, 24.0]。默认值为0.0dB。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Operation is not supported on this renderer,e.g. the stream usage of this renderer is not one of {@link StreamUsage#STREAM_USAGE_MUSIC},{@link StreamUsage#STREAM_USAGE_MOVIE} or {@link StreamUsage#STREAM_USAGE_AUDIOBOOK}. |

## setRenderRate

```TypeScript
setRenderRate(rate: AudioRendererRate, callback: AsyncCallback<void>): void
```

设置音频渲染速率。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** setSpeed

<!--Device-AudioRenderer-setRenderRate(rate: AudioRendererRate, callback: AsyncCallback<void>): void--><!--Device-AudioRenderer-setRenderRate(rate: AudioRendererRate, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | [AudioRendererRate](arkts-audio-audio-audiorendererrate-e.md) | 是 | 渲染的速率。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当设置音频渲染速率成功，err为undefined，否则为错误对象。 |

## setRenderRate

```TypeScript
setRenderRate(rate: AudioRendererRate): Promise<void>
```

设置音频渲染速率。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** setSpeed

<!--Device-AudioRenderer-setRenderRate(rate: AudioRendererRate): Promise<void>--><!--Device-AudioRenderer-setRenderRate(rate: AudioRendererRate): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | [AudioRendererRate](arkts-audio-audio-audiorendererrate-e.md) | 是 | 渲染的速率。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

## setSilentModeAndMixWithOthers

```TypeScript
setSilentModeAndMixWithOthers(on: boolean): void
```

设置静音并发播放模式。

当设置为true，打开静音并发播放模式，系统将让此音频流静音播放，并且不会打断其他音频流。设置为false，将关闭静音并发播放，音频流可根据系统焦点策略抢占焦点。

**起始版本：** 12

<!--Device-AudioRenderer-setSilentModeAndMixWithOthers(on: boolean): void--><!--Device-AudioRenderer-setSilentModeAndMixWithOthers(on: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| on | boolean | 是 | 打开/关闭静音并发播放模式。true表示设置当前播放的音频流静音播放，并且不会打断其它音频流播放。false表示取消当前播放的音频流静音播放，音频流可根据系统焦点策略抢占焦点。 |

## setSpeed

```TypeScript
setSpeed(speed: number): void
```

设置播放倍速。

**起始版本：** 11

<!--Device-AudioRenderer-setSpeed(speed: double): void--><!--Device-AudioRenderer-setSpeed(speed: double): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| speed | number | 是 | 设置播放的倍速值，倍速范围为[0.25, 4.0]。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## setVolume

```TypeScript
setVolume(volume: number, callback: AsyncCallback<void>): void
```

设置音频流的音量。使用callback异步回调。

**起始版本：** 9

<!--Device-AudioRenderer-setVolume(volume: double, callback: AsyncCallback<void>): void--><!--Device-AudioRenderer-setVolume(volume: double, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volume | number | 是 | 音量值范围为[0.0, 1.0]。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当设置应用的音量成功，err为undefined，否则为错误对象。 |

## setVolume

```TypeScript
setVolume(volume: number): Promise<void>
```

设置音频流的音量。使用Promise异步回调。

**起始版本：** 9

<!--Device-AudioRenderer-setVolume(volume: double): Promise<void>--><!--Device-AudioRenderer-setVolume(volume: double): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volume | number | 是 | 音量值范围为[0.0, 1.0]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

## setVolumeWithRamp

```TypeScript
setVolumeWithRamp(volume: number, duration: number): void
```

在指定时间范围内设置音量渐变模式。同步返回结果。

**起始版本：** 11

<!--Device-AudioRenderer-setVolumeWithRamp(volume: double, duration: int): void--><!--Device-AudioRenderer-setVolumeWithRamp(volume: double, duration: int): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volume | number | 是 | 渐变目标音量值，音量范围为[0.0, 1.0]。 |
| duration | number | 是 | 渐变持续时间，单位为ms。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

启动音频渲染器。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-start(callback: AsyncCallback<void>): void--><!--Device-AudioRenderer-start(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当启动音频渲染器成功，err为undefined，否则为错误对象。异常将返回error对象：<br>错误码6800301：表示包含状态检查异常、焦点抢占失败、系统处理异常（具体错误查看系统日志）。 |

## start

```TypeScript
start(): Promise<void>
```

启动音频渲染器。使用Promise异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-start(): Promise<void>--><!--Device-AudioRenderer-start(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，成功表示启动音频渲染器成功。异常将返回error对象：<br>错误码6800301：表示包含状态检查异常、焦点抢占失败、系统处理异常（具体错误查看系统日志）。 |

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

停止音频渲染。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-stop(callback: AsyncCallback<void>): void--><!--Device-AudioRenderer-stop(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当停止渲染成功，err为undefined，否则为错误对象。 |

## stop

```TypeScript
stop(): Promise<void>
```

停止音频渲染。使用Promise异步回调。

**起始版本：** 8

<!--Device-AudioRenderer-stop(): Promise<void>--><!--Device-AudioRenderer-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

## write

```TypeScript
write(buffer: ArrayBuffer, callback: AsyncCallback<number>): void
```

写入缓冲区。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** event:writeData

<!--Device-AudioRenderer-write(buffer: ArrayBuffer, callback: AsyncCallback<number>): void--><!--Device-AudioRenderer-write(buffer: ArrayBuffer, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 要写入缓冲区的数据。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。当写入缓冲区成功，err为undefined，data为获取到的写入的字节数；否则为错误对象。 |

## write

```TypeScript
write(buffer: ArrayBuffer): Promise<number>
```

写入缓冲区。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** event:writeData

<!--Device-AudioRenderer-write(buffer: ArrayBuffer): Promise<number>--><!--Device-AudioRenderer-write(buffer: ArrayBuffer): Promise<number>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 要写入缓冲区的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回写入的字节数。 |

## state

```TypeScript
readonly state: AudioState
```

音频渲染器的状态。

**类型：** AudioState

**起始版本：** 8

<!--Device-AudioRenderer-readonly state: AudioState--><!--Device-AudioRenderer-readonly state: AudioState-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

