# AudioVolumeManager

音量管理。 在使用AudioVolumeManager的接口之前，需先通过[getVolumeManager]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_获取AudioVolumeManager实例。 > **说明：** > > - 本Interface首批接口从API version 9开始支持。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-audio-interface AudioVolumeManager--><!--Device-audio-interface AudioVolumeManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## getAppVolumePercentage

ArkTS-Dyn:
```TypeScript
getAppVolumePercentage(): Promise<number>
```

ArkTS-Sta:
```TypeScript
getAppVolumePercentage(): Promise<int>
```

获取应用的音量（范围为[0, 100]）。使用Promise异步回调。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AudioVolumeManager-getAppVolumePercentage(): Promise<int>--><!--Device-AudioVolumeManager-getAppVolumePercentage(): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;int&gt; | Promise对象，返回应用的音量。 |

## getMaxVolumeByStream

ArkTS-Dyn:
```TypeScript
getMaxVolumeByStream(streamUsage: StreamUsage): number
```

ArkTS-Sta:
```TypeScript
getMaxVolumeByStream(streamUsage: StreamUsage): int
```

获取指定音频流的最大音量。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AudioVolumeManager-getMaxVolumeByStream(streamUsage: StreamUsage): int--><!--Device-AudioVolumeManager-getMaxVolumeByStream(streamUsage: StreamUsage): int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamUsage | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 需要获取的最大音量值的音频流。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 音量值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## getMinVolumeByStream

ArkTS-Dyn:
```TypeScript
getMinVolumeByStream(streamUsage: StreamUsage): number
```

ArkTS-Sta:
```TypeScript
getMinVolumeByStream(streamUsage: StreamUsage): int
```

获取指定音频流的最小音量。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AudioVolumeManager-getMinVolumeByStream(streamUsage: StreamUsage): int--><!--Device-AudioVolumeManager-getMinVolumeByStream(streamUsage: StreamUsage): int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamUsage | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 需要获取的最小音量值的音频流。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 音量值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## getVolumeByStream

ArkTS-Dyn:
```TypeScript
getVolumeByStream(streamUsage: StreamUsage): number
```

ArkTS-Sta:
```TypeScript
getVolumeByStream(streamUsage: StreamUsage): int
```

获取指定音频流的音量。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AudioVolumeManager-getVolumeByStream(streamUsage: StreamUsage): int--><!--Device-AudioVolumeManager-getVolumeByStream(streamUsage: StreamUsage): int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamUsage | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 需要获取音量值的音频流。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 音量值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## getVolumeGroupManager

ArkTS-Dyn:
```TypeScript
getVolumeGroupManager(groupId: number, callback: AsyncCallback<AudioVolumeGroupManager>): void
```

ArkTS-Sta:
```TypeScript
getVolumeGroupManager(groupId: int, callback: AsyncCallback<AudioVolumeGroupManager>): void
```

获取音频组音量管理器实例。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-AudioVolumeManager-getVolumeGroupManager(groupId: int, callback: AsyncCallback<AudioVolumeGroupManager>): void--><!--Device-AudioVolumeManager-getVolumeGroupManager(groupId: int, callback: AsyncCallback<AudioVolumeGroupManager>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| groupId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 音量组id，默认使用DEFAULT\_\_\_ESCAPED\_UNDERSCORE\_\_\_VOLUME\_\_\_ESCAPED\_UNDERSCORE\_\_\_GROUP\_\_\_ESCAPED\_UNDERSCORE\_\_\_ID。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AudioVolumeGroupManager&gt; | 是 | 回调函数。当获取音频组音量管理器实例成功，err为undefined，data为获取到的音频组音量管理器实例；否则为错误对象。 |

## getVolumeGroupManager

ArkTS-Dyn:
```TypeScript
getVolumeGroupManager(groupId: number): Promise<AudioVolumeGroupManager>
```

ArkTS-Sta:
```TypeScript
getVolumeGroupManager(groupId: int): Promise<AudioVolumeGroupManager>
```

获取音频组音量管理器实例。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-AudioVolumeManager-getVolumeGroupManager(groupId: int): Promise<AudioVolumeGroupManager>--><!--Device-AudioVolumeManager-getVolumeGroupManager(groupId: int): Promise<AudioVolumeGroupManager>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| groupId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 音量组id，默认使用DEFAULT\_\_\_ESCAPED\_UNDERSCORE\_\_\_VOLUME\_\_\_ESCAPED\_UNDERSCORE\_\_\_GROUP\_\_\_ESCAPED\_UNDERSCORE\_\_\_ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AudioVolumeGroupManager&gt; | Promise对象，返回音频组音量管理器实例。 |

## getVolumeGroupManagerSync

ArkTS-Dyn:
```TypeScript
getVolumeGroupManagerSync(groupId: number): AudioVolumeGroupManager
```

ArkTS-Sta:
```TypeScript
getVolumeGroupManagerSync(groupId: int): AudioVolumeGroupManager
```

获取音频组音量管理器实例。同步返回结果。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AudioVolumeManager-getVolumeGroupManagerSync(groupId: int): AudioVolumeGroupManager--><!--Device-AudioVolumeManager-getVolumeGroupManagerSync(groupId: int): AudioVolumeGroupManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| groupId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 音量组id，默认使用DEFAULT\_\_\_ESCAPED\_UNDERSCORE\_\_\_VOLUME\_\_\_ESCAPED\_UNDERSCORE\_\_\_GROUP\_\_\_ESCAPED\_UNDERSCORE\_\_\_ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 音频组音量管理器实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## getVolumeInUnitOfDbByStream

ArkTS-Dyn:
```TypeScript
getVolumeInUnitOfDbByStream(streamUsage: StreamUsage, volumeLevel: number, device: DeviceType): number
```

ArkTS-Sta:
```TypeScript
getVolumeInUnitOfDbByStream(streamUsage: StreamUsage, volumeLevel: int, device: DeviceType): double
```

获取系统通过音频流、音量等级和设备类型计算出的音量dB值。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-AudioVolumeManager-getVolumeInUnitOfDbByStream(streamUsage: StreamUsage, volumeLevel: int, device: DeviceType): double--><!--Device-AudioVolumeManager-getVolumeInUnitOfDbByStream(streamUsage: StreamUsage, volumeLevel: int, device: DeviceType): double-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamUsage | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 音频流。 |
| volumeLevel | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 音量等级。 |
| device | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 设备类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 音频流的音量dB值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## isSystemMutedForStream

```TypeScript
isSystemMutedForStream(streamUsage: StreamUsage): boolean
```

检查指定音频流是否静音。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-AudioVolumeManager-isSystemMutedForStream(streamUsage: StreamUsage): boolean--><!--Device-AudioVolumeManager-isSystemMutedForStream(streamUsage: StreamUsage): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamUsage | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 检查是否为静音的音频流。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 音频流是否为静音状态，true表示音频流已静音，false表示音频流未静音。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off('volumeChange')

```TypeScript
off(type: 'volumeChange', callback?: Callback<VolumeEvent>): void
```

取消监听系统音量变化事件。使用callback异步回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** 20

**替代接口：** ohos.multimedia.audio.AudioVolumeManager#event:streamVolumeChange

<!--Device-AudioVolumeManager-off(type: 'volumeChange', callback?: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-off(type: 'volumeChange', callback?: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'volumeChange' | 是 | 事件回调类型，支持的事件为'volumeChange'，当取消监听系统音量变化事件时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;VolumeEvent&gt; | 否 | 回调函数，返回变化后的音量信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters missing;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off('appVolumeChange')

```TypeScript
off(type: 'appVolumeChange', callback?: Callback<VolumeEvent>): void
```

取消监听当前应用的应用级音量变化事件。使用callback异步回调。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

<!--Device-AudioVolumeManager-off(type: 'appVolumeChange', callback?: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-off(type: 'appVolumeChange', callback?: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'appVolumeChange' | 是 | 事件回调类型，支持的事件为'appVolumeChange'，当取消监听当前应用的应用级音量变化事件时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;VolumeEvent&gt; | 否 | 回调函数，返回变化后的音量信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off('streamVolumeChange')

```TypeScript
off(type: 'streamVolumeChange', callback?: Callback<StreamVolumeEvent>): void
```

取消监听系统音频流音量变化事件（当系统音频流音量发生变化时触发）。使用callback异步回调。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-AudioVolumeManager-off(type: 'streamVolumeChange', callback?: Callback<StreamVolumeEvent>): void--><!--Device-AudioVolumeManager-off(type: 'streamVolumeChange', callback?: Callback<StreamVolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'streamVolumeChange' | 是 | 事件回调类型，支持的事件为'streamVolumeChange'，当取消监听系统音量变化事件时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;StreamVolumeEvent&gt; | 否 | 回调函数，返回变化后的音量信息。 |

## offAppVolumeChange

```TypeScript
offAppVolumeChange(callback?: Callback<VolumeEvent>): void
```

Unsubscribes to the app volume change events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AudioVolumeManager-offAppVolumeChange(callback?: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-offAppVolumeChange(callback?: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;VolumeEvent&gt; | 否 | Callback used to obtain the invoking volume change event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## offStreamVolumeChange

```TypeScript
offStreamVolumeChange(callback?: Callback<StreamVolumeEvent>): void
```

Unsubscribes to the stream volume change events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AudioVolumeManager-offStreamVolumeChange(callback?: Callback<StreamVolumeEvent>): void--><!--Device-AudioVolumeManager-offStreamVolumeChange(callback?: Callback<StreamVolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;StreamVolumeEvent&gt; | 否 | Callback used to obtain the invoking volume change event.If there is no callback parameter, all callbacks will be unregistered. |

## on('volumeChange')

```TypeScript
on(type: 'volumeChange', callback: Callback<VolumeEvent>): void
```

监听系统音量变化事件（当系统音量发生变化时触发）。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 20

**替代接口：** ohos.multimedia.audio.AudioVolumeManager#event:streamVolumeChange

<!--Device-AudioVolumeManager-on(type: 'volumeChange', callback: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-on(type: 'volumeChange', callback: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'volumeChange' | 是 | 事件回调类型，支持的事件为'volumeChange'，当系统音量发生变化时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;VolumeEvent&gt; | 是 | 回调函数，返回变化后的音量信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('appVolumeChange')

```TypeScript
on(type: 'appVolumeChange', callback: Callback<VolumeEvent>): void
```

监听当前应用的应用级音量变化事件（当应用级音量发生变化时触发）。使用callback异步回调。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

<!--Device-AudioVolumeManager-on(type: 'appVolumeChange', callback: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-on(type: 'appVolumeChange', callback: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'appVolumeChange' | 是 | 事件回调类型，支持的事件为'appVolumeChange'，当应用级音量发生变化时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;VolumeEvent&gt; | 是 | 回调函数，返回变化后的音量信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('streamVolumeChange')

```TypeScript
on(type: 'streamVolumeChange', streamUsage: StreamUsage, callback: Callback<StreamVolumeEvent>): void
```

监听系统音频流音量变化事件（当系统音频流音量发生变化时触发）。使用callback异步回调。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-AudioVolumeManager-on(type: 'streamVolumeChange', streamUsage: StreamUsage, callback: Callback<StreamVolumeEvent>): void--><!--Device-AudioVolumeManager-on(type: 'streamVolumeChange', streamUsage: StreamUsage, callback: Callback<StreamVolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'streamVolumeChange' | 是 | 事件回调类型，支持的事件为'streamVolumeChange'，当系统音量发生变化时，触发该事件。 |
| streamUsage | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 音频流使用类型。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;StreamVolumeEvent&gt; | 是 | 回调函数，返回变化后的音量信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## onAppVolumeChange

```TypeScript
onAppVolumeChange(callback: Callback<VolumeEvent>): void
```

Listens for app volume change events. The app volume may changed by your called \_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ or other system settings.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AudioVolumeManager-onAppVolumeChange(callback: Callback<VolumeEvent>): void--><!--Device-AudioVolumeManager-onAppVolumeChange(callback: Callback<VolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;VolumeEvent&gt; | 是 | Callback used to get the app volume change event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## onStreamVolumeChange

```TypeScript
onStreamVolumeChange(streamUsage: StreamUsage, callback: Callback<StreamVolumeEvent>): void
```

Listens for stream volume change events. This method uses a callback to get volume change events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AudioVolumeManager-onStreamVolumeChange(streamUsage: StreamUsage, callback: Callback<StreamVolumeEvent>): void--><!--Device-AudioVolumeManager-onStreamVolumeChange(streamUsage: StreamUsage, callback: Callback<StreamVolumeEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamUsage | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | StreamUsage to be listened. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;StreamVolumeEvent&gt; | 是 | Callback used to get the stream volume change event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## setAppVolumePercentage

ArkTS-Dyn:
```TypeScript
setAppVolumePercentage(volume: number): Promise<void>
```

ArkTS-Sta:
```TypeScript
setAppVolumePercentage(volume: int): Promise<void>
```

设置应用的音量（范围为[0, 100]）。使用Promise异步回调。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AudioVolumeManager-setAppVolumePercentage(volume: int): Promise<void>--><!--Device-AudioVolumeManager-setAppVolumePercentage(volume: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volume | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 要设置的音量值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Crash or blocking occurs in system process. |

