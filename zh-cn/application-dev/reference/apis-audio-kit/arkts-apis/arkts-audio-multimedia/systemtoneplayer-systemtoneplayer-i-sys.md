# SystemTonePlayer（系统接口）

系统提示音播放器提供了短信提示音、通知提示音的播放、配置、获取信息等功能。在调用SystemTonePlayer的接口前，需要先通过 [getSystemTonePlayer]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 创建实例。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export declare interface SystemTonePlayer--><!--Device-unnamed-export declare interface SystemTonePlayer-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

## getAudioVolumeScale

ArkTS-Dyn:
```TypeScript
getAudioVolumeScale(): number
```

ArkTS-Sta:
```TypeScript
getAudioVolumeScale(): double
```

获取当前音频音量大小，同步返回当前音量。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-SystemTonePlayer-getAudioVolumeScale(): double--><!--Device-SystemTonePlayer-getAudioVolumeScale(): double-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 当前音频音量，音量范围为[0, 1]。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## getHapticsFeature

```TypeScript
getHapticsFeature(): systemSoundManager.ToneHapticsFeature
```

获取播放铃音时的振动风格，同步返回振动风格枚举值。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-SystemTonePlayer-getHapticsFeature(): systemSoundManager.ToneHapticsFeature--><!--Device-SystemTonePlayer-getHapticsFeature(): systemSoundManager.ToneHapticsFeature-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| systemSoundManager.ToneHapticsFeature | 振动风格。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [20700003](../../errorcode-audio-ringtone-sys.md#20700003-操作不支持) | Unsupported operation. |

## getSupportedHapticsFeatures

```TypeScript
getSupportedHapticsFeatures(): Promise<Array<systemSoundManager.ToneHapticsFeature>>
```

获取当前支持的振动风格。使用Promise异步回调。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-SystemTonePlayer-getSupportedHapticsFeatures(): Promise<Array<systemSoundManager.ToneHapticsFeature>>--><!--Device-SystemTonePlayer-getSupportedHapticsFeatures(): Promise<Array<systemSoundManager.ToneHapticsFeature>>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;systemSoundManager.ToneHapticsFeature&gt;&gt; | Promise对象，返回当前支持的振动风格。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [20700003](../../errorcode-audio-ringtone-sys.md#20700003-操作不支持) | Unsupported operation. |

## getTitle

```TypeScript
getTitle(): Promise<string>
```

获取提示音标题。使用Promise异步回调。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-SystemTonePlayer-getTitle(): Promise<string>--><!--Device-SystemTonePlayer-getTitle(): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回获取的系统提示音标题。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [5400103](../../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |

## off('playFinished')

```TypeScript
off(type: 'playFinished', callback?: Callback<int>): void
```

取消监听铃音播放完成事件。使用callback异步回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

<!--Device-SystemTonePlayer-off(type: 'playFinished', callback?: Callback<int>): void--><!--Device-SystemTonePlayer-off(type: 'playFinished', callback?: Callback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playFinished' | 是 | 事件回调类型，支持的事件为'playFinished'，当取消监听铃音播放完成事件时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; | 否 | 回调函数，返回结束事件的音频流的streamId。不填入此参数时，会取消该事件的所有监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [20700002](../../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. |

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

取消监听铃音播放过程中的错误事件。使用callback异步回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

<!--Device-SystemTonePlayer-off(type: 'error', callback?: ErrorCallback): void--><!--Device-SystemTonePlayer-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 事件回调类型，支持的事件为'error'，当取消监听铃音播放过程中的错误事件时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 回调函数，返回错误码和错误信息。不填入此参数时，会取消该事件的所有监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [20700002](../../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. |

## offError

```TypeScript
offError(callback?: ErrorCallback): void
```

取消监听铃音播放过程中的错误事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SystemTonePlayer-offError(callback?: ErrorCallback): void--><!--Device-SystemTonePlayer-offError(callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Error callback while receiving the error event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [20700002](../../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. |

## offPlayFinished

```TypeScript
offPlayFinished(callback?: Callback<int>): void
```

取消监听铃音播放完成事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SystemTonePlayer-offPlayFinished(callback?: Callback<int>): void--><!--Device-SystemTonePlayer-offPlayFinished(callback?: Callback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; | 否 | Callback used to obtain the finished event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [20700002](../../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. |

## on('playFinished')

```TypeScript
on(type: 'playFinished', streamId: int, callback: Callback<int>): void
```

监听铃音播放完成事件（当铃音播放完成时触发）。使用callback异步回调。 监听对象为传入的streamId对应音频流。当streamId传入0时，监听本播放器对应的所有音频流。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

<!--Device-SystemTonePlayer-on(type: 'playFinished', streamId: int, callback: Callback<int>): void--><!--Device-SystemTonePlayer-on(type: 'playFinished', streamId: int, callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playFinished' | 是 | 事件回调类型，支持的事件为'playFinished'，当铃音播放完成时，触发该事件。 |
| streamId | int | 是 | 监听对象为指定streamId对应的音频流，streamId通过[start]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_获取。当streamId传入0时，可监听当前播放器对应的所有音频流。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; | 是 | 'playFinished'的回调方法。返回播放完成的音频流的streamId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [20700002](../../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

监听铃音播放过程中的错误事件（当铃音播放过程中发生错误时触发）。使用callback异步回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

<!--Device-SystemTonePlayer-on(type: 'error', callback: ErrorCallback): void--><!--Device-SystemTonePlayer-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 事件回调类型，支持的事件为'error'，当铃音播放过程中发生错误时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调函数，返回错误码和错误信息。错误码请参考AVPlayer的[on('error')]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [20700002](../../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. |

## onError

```TypeScript
onError(callback: ErrorCallback): void
```

监听铃音播放过程中的错误事件（当铃音播放过程中发生错误时触发）。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SystemTonePlayer-onError(callback: ErrorCallback): void--><!--Device-SystemTonePlayer-onError(callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Error callback while receiving the error event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [20700002](../../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. |

## onPlayFinished

```TypeScript
onPlayFinished(streamId: int, callback: Callback<int>): void
```

监听铃音播放完成事件（当铃音播放完成时触发）。使用callback异步回调。 监听对象为传入的streamId对应音频流。当streamId传入0时，监听本播放器对应的所有音频流。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SystemTonePlayer-onPlayFinished(streamId: int, callback: Callback<int>): void--><!--Device-SystemTonePlayer-onPlayFinished(streamId: int, callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamId | int | 是 | Stream id, received from start(). |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; | 是 | Callback used to obtain the finished event. The callback info is the stream id that is finished. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [20700002](../../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. |

## prepare

```TypeScript
prepare(): Promise<void>
```

准备播放提示音。使用Promise异步回调。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-SystemTonePlayer-prepare(): Promise<void>--><!--Device-SystemTonePlayer-prepare(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [5400102](../../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |

## release

```TypeScript
release(): Promise<void>
```

释放提示音播放器。使用Promise异步回调。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-SystemTonePlayer-release(): Promise<void>--><!--Device-SystemTonePlayer-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## setAudioVolumeScale

ArkTS-Dyn:
```TypeScript
setAudioVolumeScale(scale: number): void
```

ArkTS-Sta:
```TypeScript
setAudioVolumeScale(scale: double): void
```

设置音频音量大小，无返回结果。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-SystemTonePlayer-setAudioVolumeScale(scale: double): void--><!--Device-SystemTonePlayer-setAudioVolumeScale(scale: double): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 音频音量大小，必须在[0, 1]之间取值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400102](../../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [20700002](../../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. For example, value is outside [0,1]. |

## setHapticsFeature

```TypeScript
setHapticsFeature(hapticsFeature: systemSoundManager.ToneHapticsFeature): void
```

设置播放铃音时的振动风格。 调用本接口前，应该先调用[getSupportedHapticsFeatures]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_查询 支持的振动风格，如果设置不支持的振动风格，则设置失败。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-SystemTonePlayer-setHapticsFeature(hapticsFeature: systemSoundManager.ToneHapticsFeature): void--><!--Device-SystemTonePlayer-setHapticsFeature(hapticsFeature: systemSoundManager.ToneHapticsFeature): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapticsFeature | systemSoundManager.ToneHapticsFeature | 是 | 振动风格。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400102](../../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [20700003](../../errorcode-audio-ringtone-sys.md#20700003-操作不支持) | Unsupported operation. |

## start

ArkTS-Dyn:
```TypeScript
start(toneOptions?: SystemToneOptions): Promise<number>
```

ArkTS-Sta:
```TypeScript
start(toneOptions?: SystemToneOptions): Promise<int>
```

开始播放提示音。使用Promise异步回调。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.VIBRATE

<!--Device-SystemTonePlayer-start(toneOptions?: SystemToneOptions): Promise<int>--><!--Device-SystemTonePlayer-start(toneOptions?: SystemToneOptions): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| toneOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 系统提示音选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;int&gt; | Promise对象，返回streamID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400102](../../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |

## stop

ArkTS-Dyn:
```TypeScript
stop(id: number): Promise<void>
```

ArkTS-Sta:
```TypeScript
stop(id: int): Promise<void>
```

停止播放提示音。使用Promise异步回调。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-SystemTonePlayer-stop(id: int): Promise<void>--><!--Device-SystemTonePlayer-stop(id: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | Promise对象，返回streamID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise回调返回停止播放成功或失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400102](../../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |

