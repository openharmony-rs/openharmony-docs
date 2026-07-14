# AudioLoopback

提供音频返听的相关接口。

在使用AudioLoopback的接口之前，需先通过[audio.createAudioLoopback](arkts-audio-createaudioloopback-f.md#createaudioloopback-1)获取AudioLoopback实例。

当启用音频返听时，系统会创建低时延渲染器与低时延采集器，实现低时延耳返功能。采集的音频直接通过内部路由返回到渲染器。对于渲染器，其音频焦点策略与
[STREAM_USAGE_MUSIC](arkts-audio-streamusage-e.md)相匹配。对于采集器，其音频焦点策略与[SOURCE_TYPE_MIC](arkts-audio-sourcetype-e.md)相匹配。

输入\输出设备由系统自动选择。如果当前输入\输出不支持低时延，则音频返听无法启用。在运行过程中，如果音频焦点被另一个音频流抢占，输入\输出设备切换到不支持低时延的设备，系统会自动禁用音频返听。

> **说明：**
>
> - 本Interface首批接口从API version 20开始支持。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## enable

```TypeScript
enable(enable: boolean): Promise<boolean>
```

启用或禁用音频返听器。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.MICROPHONE

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 表示是否启用音频返听器。true表示启用，false表示不启用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示功能执行成功；返回false表示功能执行失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## getEqualizerPreset

```TypeScript
getEqualizerPreset(): AudioLoopbackEqualizerPreset
```

获取当前音频返听器的均衡器类型。

**起始版本：** 21

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AudioLoopbackEqualizerPreset | 返回当前音频返听器的均衡器类型。<br>在没有被修改的情况下，默认的均衡器类型是FULL。 |

## getPreferredDevicePair

```TypeScript
getPreferredDevicePair(): AudioDevicePair | null
```

获取当前设备连接状态下系统推荐的返听音频输入输出设备组合。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AudioDevicePair | 返回系统推荐的音频输入输出设备组合。<br>如果没有可用的输入输出设备组合，则返回null。 |

## getReverbPreset

```TypeScript
getReverbPreset(): AudioLoopbackReverbPreset
```

获取当前音频返听器的混响模式。

**起始版本：** 21

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AudioLoopbackReverbPreset | 返回当前音频返听器的混响模式。<br>在没有被修改的情况下，默认的混响模式是THEATER。 |

## getStatus

```TypeScript
getStatus(): Promise<AudioLoopbackStatus>
```

获取音频返听状态。使用Promise异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AudioLoopbackStatus&gt; | Promise对象，返回音频返听状态。 |

## getSupportedDevicePairs

```TypeScript
getSupportedDevicePairs(): Array<AudioDevicePair>
```

获取当前设备连接状态下支持返听的音频输入输出设备组合。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;AudioDevicePair&gt; | 返回支持返听的音频输入输出设备数组。<br>如果没有可用的输入输出设备组合，则返回空数组。 |

## getVolume

```TypeScript
getVolume(): number
```

获取音频返听输出音量。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回当前音频返听输出音量，范围为[0.0, 1.0]。 |

## off('statusChange')

```TypeScript
off(type: 'statusChange', callback?: Callback<AudioLoopbackStatus>): void
```

取消监听音频状态事件。使用callback异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'statusChange' | 是 | 事件回调类型，支持的事件为'statusChange'，当取消监听音频状态事件时，触发该事件。 |
| callback | Callback&lt;AudioLoopbackStatus&gt; | 否 | 回调函数，返回当前音频返听的状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('statusChange')

```TypeScript
on(type: 'statusChange', callback: Callback<AudioLoopbackStatus>): void
```

监听返听状态变化事件（当AudioLoopback的状态发生变化时触发）。使用callback异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'statusChange' | 是 | 事件回调类型，支持的事件为'statusChange'，当AudioLoopback的状态发生变化时，触发该事件。 |
| callback | Callback&lt;AudioLoopbackStatus&gt; | 是 | 回调函数，返回当前音频返听的状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## setEqualizerPreset

```TypeScript
setEqualizerPreset(preset: AudioLoopbackEqualizerPreset): boolean
```

设置音频返听器的均衡器类型。

**起始版本：** 21

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| preset | AudioLoopbackEqualizerPreset | 是 | 均衡器类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回均衡器类型是否设置成功。true表示成功，false表示不成功。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## setReverbPreset

```TypeScript
setReverbPreset(preset: AudioLoopbackReverbPreset): boolean
```

设置音频返听器的混响模式。

**起始版本：** 21

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| preset | AudioLoopbackReverbPreset | 是 | 混响模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回混响模式是否设置成功。true表示成功，false表示不成功。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## setVolume

```TypeScript
setVolume(volume: number): Promise<void>
```

设置音频返听的音量。使用Promise异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volume | number | 是 | 音量值范围为[0.0, 1.0]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed, form 0.0 to 1.0. |

