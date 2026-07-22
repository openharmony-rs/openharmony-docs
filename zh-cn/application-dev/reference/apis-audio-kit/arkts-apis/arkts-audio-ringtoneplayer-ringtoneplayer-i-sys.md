# RingtonePlayer（系统接口）

系统铃声播放器，提供系统铃声的参数设置、参数获取、播放、停止等功能。在调用RingtonePlayer的接口前，需要先通过[getRingtonePlayer](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#getringtoneplayer)创建实例。

**起始版本：** 10

<!--Device-unnamed-export interface RingtonePlayer--><!--Device-unnamed-export interface RingtonePlayer-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

## configure

```TypeScript
configure(options: RingtoneOptions, callback: AsyncCallback<void>): void
```

配置铃声播放参数。使用callback异步回调。

**起始版本：** 10

<!--Device-RingtonePlayer-configure(options: RingtoneOptions, callback: AsyncCallback<void>): void--><!--Device-RingtonePlayer-configure(options: RingtoneOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RingtoneOptions](arkts-audio-systemsoundmanager-ringtoneoptions-t-sys.md) | 是 | 指定铃声参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当配置铃声播放参数成功，err为undefined，否则为错误对象。 |

## configure

```TypeScript
configure(options: RingtoneOptions): Promise<void>
```

配置铃声播放参数。使用Promise异步回调。

**起始版本：** 10

<!--Device-RingtonePlayer-configure(options: RingtoneOptions): Promise<void>--><!--Device-RingtonePlayer-configure(options: RingtoneOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RingtoneOptions](arkts-audio-systemsoundmanager-ringtoneoptions-t-sys.md) | 是 | 指定铃声参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

## getAudioRendererInfo

```TypeScript
getAudioRendererInfo(callback: AsyncCallback<audio.AudioRendererInfo>): void
```

获取铃声使用的AudioRendererInfo。使用callback异步回调。

**起始版本：** 10

<!--Device-RingtonePlayer-getAudioRendererInfo(callback: AsyncCallback<audio.AudioRendererInfo>): void--><!--Device-RingtonePlayer-getAudioRendererInfo(callback: AsyncCallback<audio.AudioRendererInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;audio.AudioRendererInfo&gt; | 是 | 回调函数。当获取音频渲染器信息成功，err为undefined data为获取到的音频渲染器信息；否则为错误对象。 |

## getAudioRendererInfo

```TypeScript
getAudioRendererInfo(): Promise<audio.AudioRendererInfo>
```

获取铃声使用的AudioRendererInfo。使用Promise异步回调。

**起始版本：** 10

<!--Device-RingtonePlayer-getAudioRendererInfo(): Promise<audio.AudioRendererInfo>--><!--Device-RingtonePlayer-getAudioRendererInfo(): Promise<audio.AudioRendererInfo>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;audio.AudioRendererInfo&gt; | Promise对象，返回获取的音频渲染器信息。 |

## getTitle

```TypeScript
getTitle(callback: AsyncCallback<string>): void
```

获取铃声标题。使用callback异步回调。

**起始版本：** 10

<!--Device-RingtonePlayer-getTitle(callback: AsyncCallback<string>): void--><!--Device-RingtonePlayer-getTitle(callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。当获取铃声标题成功，err为undefined，data为获取到的铃声标题；否则为错误对象。 |

## getTitle

```TypeScript
getTitle(): Promise<string>
```

获取铃声标题。使用Promise异步回调。

**起始版本：** 10

<!--Device-RingtonePlayer-getTitle(): Promise<string>--><!--Device-RingtonePlayer-getTitle(): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回获取的系统铃声标题。 |

## off

```TypeScript
off(type: 'audioInterrupt'): void
```

取消监听音频中断事件。

**起始版本：** 10

<!--Device-RingtonePlayer-off(type: 'audioInterrupt'): void--><!--Device-RingtonePlayer-off(type: 'audioInterrupt'): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | 是 | 事件回调类型，支持的事件为'audioInterrupt'，当取消监听音频中断事件时，触发该事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('audioInterrupt')

```TypeScript
on(type: 'audioInterrupt', callback: Callback<audio.InterruptEvent>): void
```

监听音频中断事件（当音频焦点发生变化时触发）。使用callback异步回调。

**起始版本：** 10

<!--Device-RingtonePlayer-on(type: 'audioInterrupt', callback: Callback<audio.InterruptEvent>): void--><!--Device-RingtonePlayer-on(type: 'audioInterrupt', callback: Callback<audio.InterruptEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | 是 | 事件回调类型，支持的事件为'audioInterrupt'，当音频焦点状态发生变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;audio.InterruptEvent&gt; | 是 | 回调函数，返回中断事件信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放铃声播放器。使用callback异步回调。

**起始版本：** 10

<!--Device-RingtonePlayer-release(callback: AsyncCallback<void>): void--><!--Device-RingtonePlayer-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当释放铃声播放器成功，err为undefined，否则为错误对象。 |

## release

```TypeScript
release(): Promise<void>
```

释放铃声播放器。使用Promise异步回调。

**起始版本：** 10

<!--Device-RingtonePlayer-release(): Promise<void>--><!--Device-RingtonePlayer-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

开始播放铃声。使用callback异步回调。

**起始版本：** 10

<!--Device-RingtonePlayer-start(callback: AsyncCallback<void>): void--><!--Device-RingtonePlayer-start(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当开始播放铃声成功，err为undefined，否则为错误对象。 |

## start

```TypeScript
start(): Promise<void>
```

开始播放铃声。使用Promise异步回调。

**起始版本：** 10

<!--Device-RingtonePlayer-start(): Promise<void>--><!--Device-RingtonePlayer-start(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

停止播放铃声。使用callback异步回调。

**起始版本：** 10

<!--Device-RingtonePlayer-stop(callback: AsyncCallback<void>): void--><!--Device-RingtonePlayer-stop(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当停止播放铃声成功，err为undefined，否则为错误对象。 |

## stop

```TypeScript
stop(): Promise<void>
```

停止播放铃声。使用Promise异步回调。

**起始版本：** 10

<!--Device-RingtonePlayer-stop(): Promise<void>--><!--Device-RingtonePlayer-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

## state

```TypeScript
readonly state: media.AVPlayerState
```

音频渲染器的状态。

**类型：** media.AVPlayerState

**起始版本：** 10

<!--Device-RingtonePlayer-readonly state: media.AVPlayerState--><!--Device-RingtonePlayer-readonly state: media.AVPlayerState-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

