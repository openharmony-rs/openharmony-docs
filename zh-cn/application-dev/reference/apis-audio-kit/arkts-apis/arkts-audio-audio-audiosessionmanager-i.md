# AudioSessionManager

音频会话管理。

在使用AudioSessionManager的接口之前，需先通过[getSessionManager](arkts-audio-audio-audiomanager-i.md#getsessionmanager-1)获取AudioSessionManager实例。

> **说明：**  
>  
> - 本Interface首批接口从API version 12开始支持。

**起始版本：** 12

<!--Device-audio-interface AudioSessionManager--><!--Device-audio-interface AudioSessionManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

<a id="activateaudiosession"></a>
## activateAudioSession

```TypeScript
activateAudioSession(strategy: AudioSessionStrategy): Promise<void>
```

激活音频会话。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AudioSessionManager-activateAudioSession(strategy: AudioSessionStrategy): Promise<void>--><!--Device-AudioSessionManager-activateAudioSession(strategy: AudioSessionStrategy): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strategy | [AudioSessionStrategy](arkts-audio-audio-audiosessionstrategy-i.md) | 是 | 音频会话策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters unspecified.2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Possible causes:1.Focus preemption failure.2.Audio server process died. |

<a id="clearselectedmediainputdevice"></a>
## clearSelectedMediaInputDevice

```TypeScript
clearSelectedMediaInputDevice(): Promise<void>
```

清空通过[selectMediaInputDevice](arkts-audio-audio-audiosessionmanager-i.md#selectmediainputdevice-1)设置的媒体输入设备。使用Promise异步回调。

**起始版本：** 21

<!--Device-AudioSessionManager-clearSelectedMediaInputDevice(): Promise<void>--><!--Device-AudioSessionManager-clearSelectedMediaInputDevice(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, System error. |

<a id="deactivateaudiosession"></a>
## deactivateAudioSession

```TypeScript
deactivateAudioSession(): Promise<void>
```

停用音频会话。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AudioSessionManager-deactivateAudioSession(): Promise<void>--><!--Device-AudioSessionManager-deactivateAudioSession(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Possible causes:1.The audio session is not existed or has been released.2.Audio server process died. |

<a id="enablemutesuggestionwhenmixwithothers"></a>
## enableMuteSuggestionWhenMixWithOthers

```TypeScript
enableMuteSuggestionWhenMixWithOthers(enable: boolean): void
```

启用混音播放下接收静音播放建议通知功能。

通常，当使用混音模式时，如果其他应用同时播放音频，会和其他应用进行混音播放。但在某些场景下（如游戏或广播），应用自身会通过静音自身的音频以给用户提供更好的体验。

如果启用此功能，当订阅音频会话状态更改事件后静音建议和取消静音建议提示将通过[AudioSessionStateChangedEvent](arkts-audio-audio-audiosessionstatechangedevent-i.md)回调发送。收到静音建议表示其他应用程序开始播放音频，且播放的音频和本应用的音频不能混音。

此功能仅支持已设置[AudioSessionScene](arkts-audio-audio-audiosessionscene-e.md)并激活模式模式为CONCURRENCY_MIX_WITH_OTHERS的音频会话使用。并且仅在激活音频会话期间生效一次，每次激活音频会话前都必须重新启用。

详细说明请参考[启用混音播放下静音建议通知](docroot://media/audio/audio-session-management.md#启用混音播放下静音建议通知)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSessionManager-enableMuteSuggestionWhenMixWithOthers(enable: boolean): void--><!--Device-AudioSessionManager-enableMuteSuggestionWhenMixWithOthers(enable: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用混音播放下接收静音播放建议通知功能。true表示启用，false表示不启用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Function is called without setting {@link #AudioSessionScene} or called after audio session activation. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, system internal error. |

<a id="getavailabledevices"></a>
## getAvailableDevices

```TypeScript
getAvailableDevices(deviceUsage: DeviceUsage): AudioDeviceDescriptors
```

获取音频可选设备列表。

**起始版本：** 21

<!--Device-AudioSessionManager-getAvailableDevices(deviceUsage: DeviceUsage): AudioDeviceDescriptors--><!--Device-AudioSessionManager-getAvailableDevices(deviceUsage: DeviceUsage): AudioDeviceDescriptors-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceUsage | [DeviceUsage](arkts-audio-audio-deviceusage-e.md) | 是 | 音频设备类型（根据用途分类）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | 返回设备列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, System error. |

<a id="getbluetoothandnearlinkpreferredrecordcategory"></a>
## getBluetoothAndNearlinkPreferredRecordCategory

```TypeScript
getBluetoothAndNearlinkPreferredRecordCategory(): BluetoothAndNearlinkPreferredRecordCategory
```

获取通过[setBluetoothAndNearlinkPreferredRecordCategory](arkts-audio-audio-audiosessionmanager-i.md#setbluetoothandnearlinkpreferredrecordcategory-1)设置的在使用蓝牙或星闪进行录音时的设备偏好分类。

**起始版本：** 21

<!--Device-AudioSessionManager-getBluetoothAndNearlinkPreferredRecordCategory(): BluetoothAndNearlinkPreferredRecordCategory--><!--Device-AudioSessionManager-getBluetoothAndNearlinkPreferredRecordCategory(): BluetoothAndNearlinkPreferredRecordCategory-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BluetoothAndNearlinkPreferredRecordCategory](arkts-audio-audio-bluetoothandnearlinkpreferredrecordcategory-e.md) | - 在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, System error. |

<a id="getdefaultoutputdevice"></a>
## getDefaultOutputDevice

```TypeScript
getDefaultOutputDevice(): DeviceType
```

获取通过[setDefaultOutputDevice](arkts-audio-audio-audiosessionmanager-i.md#setdefaultoutputdevice-1)设置的默认发声设备。

**起始版本：** 20

<!--Device-AudioSessionManager-getDefaultOutputDevice(): DeviceType--><!--Device-AudioSessionManager-getDefaultOutputDevice(): DeviceType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DeviceType](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-devicetype-e.md) | - 设备类型。<br>仅支持以下设备：EARPIECE（听筒）、SPEAKER（扬声器）和DEFAULT（系统默认设备）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Operation not permit at current state. Return by promise. |

<a id="getselectedmediainputdevice"></a>
## getSelectedMediaInputDevice

```TypeScript
getSelectedMediaInputDevice(): AudioDeviceDescriptor
```

获得通过[selectMediaInputDevice](arkts-audio-audio-audiosessionmanager-i.md#selectmediainputdevice-1)设置的媒体输入设备。如果没有设置，返回一个deviceType属性为INVALID的设备。

**起始版本：** 21

<!--Device-AudioSessionManager-getSelectedMediaInputDevice(): AudioDeviceDescriptor--><!--Device-AudioSessionManager-getSelectedMediaInputDevice(): AudioDeviceDescriptor-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | - 媒体输入设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, System error. |

<a id="isaudiosessionactivated"></a>
## isAudioSessionActivated

```TypeScript
isAudioSessionActivated(): boolean
```

检查音频会话是否已激活。

**起始版本：** 12

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AudioSessionManager-isAudioSessionActivated(): boolean--><!--Device-AudioSessionManager-isAudioSessionActivated(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 音频会话是否处于激活状态。true表示已激活，false表示已停用。 |

<a id="isothermediaplaying"></a>
## isOtherMediaPlaying

```TypeScript
isOtherMediaPlaying(): boolean
```

检查是否有其他应用正在播放MUSIC、MOVIE、AUDIOBOOK、GAME四种媒体类型的音频，已激活媒体类型的音频会话也将会被检查。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSessionManager-isOtherMediaPlaying(): boolean--><!--Device-AudioSessionManager-isOtherMediaPlaying(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否有其他应用正在播放媒体类型的音频。true表示有，false表示没有。 |

<a id="off"></a>
## off('audioSessionDeactivated')

```TypeScript
off(type: 'audioSessionDeactivated', callback?: Callback<AudioSessionDeactivatedEvent>): void
```

取消监听音频会话停用事件。使用callback异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AudioSessionManager-off(type: 'audioSessionDeactivated', callback?: Callback<AudioSessionDeactivatedEvent>): void--><!--Device-AudioSessionManager-off(type: 'audioSessionDeactivated', callback?: Callback<AudioSessionDeactivatedEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioSessionDeactivated' | 是 | 事件回调类型，支持的事件为'audioSessionDeactivated'，当取消监听音频会话停用事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;AudioSessionDeactivatedEvent&gt; | 否 | 回调函数，返回音频会话停用原因。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

<a id="off-1"></a>
## off('audioSessionStateChanged')

```TypeScript
off(type: 'audioSessionStateChanged', callback?: Callback<AudioSessionStateChangedEvent>): void
```

取消监听音频会话状态变更事件。使用callback异步回调。

**起始版本：** 20

<!--Device-AudioSessionManager-off(type: 'audioSessionStateChanged', callback?: Callback<AudioSessionStateChangedEvent>): void--><!--Device-AudioSessionManager-off(type: 'audioSessionStateChanged', callback?: Callback<AudioSessionStateChangedEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioSessionStateChanged' | 是 | 事件回调类型，支持的事件为'audioSessionStateChanged'，当音频会话状态变更时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;AudioSessionStateChangedEvent&gt; | 否 | 回调函数，返回音频会话变更提示信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, System error. |

<a id="off-2"></a>
## off('currentOutputDeviceChanged')

```TypeScript
off(type: 'currentOutputDeviceChanged', callback?: Callback<CurrentOutputDeviceChangedEvent>): void
```

取消监听当前输出设备的变化事件，并使用callback进行异步回调。

**起始版本：** 20

<!--Device-AudioSessionManager-off(type: 'currentOutputDeviceChanged', callback?: Callback<CurrentOutputDeviceChangedEvent>): void--><!--Device-AudioSessionManager-off(type: 'currentOutputDeviceChanged', callback?: Callback<CurrentOutputDeviceChangedEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'currentOutputDeviceChanged' | 是 | 事件回调类型，支持的事件为'currentOutputDeviceChanged'，当前输出设备发生变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;CurrentOutputDeviceChangedEvent&gt; | 否 | 回调函数，用于返回当前输出设备变化的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, System error. |

<a id="off-3"></a>
## off('availableDeviceChange')

```TypeScript
off(type: 'availableDeviceChange', callback?: Callback<DeviceChangeAction>): void
```

取消监听音频可选设备连接状态变化事件。

**起始版本：** 21

<!--Device-AudioSessionManager-off(type: 'availableDeviceChange', callback?: Callback<DeviceChangeAction>): void--><!--Device-AudioSessionManager-off(type: 'availableDeviceChange', callback?: Callback<DeviceChangeAction>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'availableDeviceChange' | 是 | 事件回调类型，支持的事件为'availableDeviceChange'，当取消监听音频可选设备连接变化事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;DeviceChangeAction&gt; | 否 | 回调函数，返回可选设备更新详情。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, System error. |

<a id="off-4"></a>
## off('currentInputDeviceChanged')

```TypeScript
off(type: 'currentInputDeviceChanged', callback?: Callback<CurrentInputDeviceChangedEvent>): void
```

取消监听当前输入设备的变化事件。

**起始版本：** 21

<!--Device-AudioSessionManager-off(type: 'currentInputDeviceChanged', callback?: Callback<CurrentInputDeviceChangedEvent>): void--><!--Device-AudioSessionManager-off(type: 'currentInputDeviceChanged', callback?: Callback<CurrentInputDeviceChangedEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'currentInputDeviceChanged' | 是 | 事件回调类型，支持的事件为'currentInputDeviceChanged'，当前输入设备发生变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;CurrentInputDeviceChangedEvent&gt; | 否 | 回调函数，用于返回当前输入设备变化的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, System error. |

<a id="on"></a>
## on('audioSessionDeactivated')

```TypeScript
on(type: 'audioSessionDeactivated', callback: Callback<AudioSessionDeactivatedEvent>): void
```

监听音频会话停用事件（当音频会话停用时触发）。使用callback异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AudioSessionManager-on(type: 'audioSessionDeactivated', callback: Callback<AudioSessionDeactivatedEvent>): void--><!--Device-AudioSessionManager-on(type: 'audioSessionDeactivated', callback: Callback<AudioSessionDeactivatedEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioSessionDeactivated' | 是 | 事件回调类型，支持的事件为'audioSessionDeactivated'，当音频会话停用时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;AudioSessionDeactivatedEvent&gt; | 是 | 回调函数，返回音频会话停用原因。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters unspecified.2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

<a id="on-1"></a>
## on('audioSessionStateChanged')

```TypeScript
on(type: 'audioSessionStateChanged', callback: Callback<AudioSessionStateChangedEvent>): void
```

监听音频会话状态变更事件（当音频会话焦点变更时触发）。使用callback异步回调。

**起始版本：** 20

<!--Device-AudioSessionManager-on(type: 'audioSessionStateChanged', callback: Callback<AudioSessionStateChangedEvent>): void--><!--Device-AudioSessionManager-on(type: 'audioSessionStateChanged', callback: Callback<AudioSessionStateChangedEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioSessionStateChanged' | 是 | 事件回调类型，支持的事件为'audioSessionStateChanged'，当音频会话状态变更时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;AudioSessionStateChangedEvent&gt; | 是 | 回调函数，返回音频会话变更提示信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800102](../errorcode-audio.md#6800102-分配内存失败) | Allocate memory failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, System error. |

<a id="on-2"></a>
## on('currentOutputDeviceChanged')

```TypeScript
on(type: 'currentOutputDeviceChanged', callback: Callback<CurrentOutputDeviceChangedEvent>): void
```

监听当前输出设备变化事件（当前输出设备发生变化时触发）。使用callback异步回调。

**起始版本：** 20

<!--Device-AudioSessionManager-on(type: 'currentOutputDeviceChanged', callback: Callback<CurrentOutputDeviceChangedEvent>): void--><!--Device-AudioSessionManager-on(type: 'currentOutputDeviceChanged', callback: Callback<CurrentOutputDeviceChangedEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'currentOutputDeviceChanged' | 是 | 事件回调类型，支持的事件为'currentOutputDeviceChanged'，当前输出设备变更时触发。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;CurrentOutputDeviceChangedEvent&gt; | 是 | 回调函数，返回当前输出设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800102](../errorcode-audio.md#6800102-分配内存失败) | Allocate memory failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, System error. |

<a id="on-3"></a>
## on('availableDeviceChange')

```TypeScript
on(type: 'availableDeviceChange', deviceUsage: DeviceUsage, callback: Callback<DeviceChangeAction>): void
```

监听音频可选设备连接状态变化事件（当音频可选设备连接状态发生变化时触发）。

**起始版本：** 21

<!--Device-AudioSessionManager-on(type: 'availableDeviceChange', deviceUsage: DeviceUsage, callback: Callback<DeviceChangeAction>): void--><!--Device-AudioSessionManager-on(type: 'availableDeviceChange', deviceUsage: DeviceUsage, callback: Callback<DeviceChangeAction>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'availableDeviceChange' | 是 | 事件回调类型，支持的事件为'availableDeviceChange'，当音频可选设备连接状态发生变化时，触发该事件。 |
| deviceUsage | [DeviceUsage](arkts-audio-audio-deviceusage-e.md) | 是 | 音频设备类型（根据用途分类）。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;DeviceChangeAction&gt; | 是 | 回调函数，返回设备更新详情。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, System error. |

<a id="on-4"></a>
## on('currentInputDeviceChanged')

```TypeScript
on(type: 'currentInputDeviceChanged', callback: Callback<CurrentInputDeviceChangedEvent>): void
```

监听当前输入设备变化事件（当前输入设备发生变化时触发）。

**起始版本：** 21

<!--Device-AudioSessionManager-on(type: 'currentInputDeviceChanged', callback: Callback<CurrentInputDeviceChangedEvent>): void--><!--Device-AudioSessionManager-on(type: 'currentInputDeviceChanged', callback: Callback<CurrentInputDeviceChangedEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'currentInputDeviceChanged' | 是 | 事件回调类型，支持的事件为'currentInputDeviceChanged'，当前输入设备发生变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;CurrentInputDeviceChangedEvent&gt; | 是 | 回调函数，返回当前输入设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, System error. |

<a id="selectmediainputdevice"></a>
## selectMediaInputDevice

```TypeScript
selectMediaInputDevice(inputAudioDevice: AudioDeviceDescriptor): Promise<void>
```

设置媒体输入设备。使用Promise异步回调。

> **说明：**  
>  
> - 本接口不适用于VoIP通话录音，即[SourceType](arkts-audio-audio-sourcetype-e.md)为SOURCE_TYPE_VOICE_COMMUNICATION的场景不适用。  
>  
> - 本接口调用前需要先调用[getAvailableDevices](arkts-audio-audio-audiosessionmanager-i.md#getavailabledevices-1)接口查询到当前可用输入设备列表，从列表中选择输入  
> 设备。  
>  
> - 当系统中存在其他更高优先级的应用录音流时，实际使用的输入设备会跟随其他高优先级应用所选的输入设备。  
>  
> - 应用程序可以监听  
> [currentInputDeviceChanged](audio.AudioSessionManager.on(type: 'currentInputDeviceChanged', callback: Callback<CurrentInputDeviceChangedEvent>))  
> 事件来获得实际的输入设备。

**起始版本：** 21

<!--Device-AudioSessionManager-selectMediaInputDevice(inputAudioDevice: AudioDeviceDescriptor): Promise<void>--><!--Device-AudioSessionManager-selectMediaInputDevice(inputAudioDevice: AudioDeviceDescriptor): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputAudioDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 媒体输入设备。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed, for example,the selected device does not exist. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, System error. |

<a id="setaudiosessionbehavior"></a>
## setAudioSessionBehavior

```TypeScript
setAudioSessionBehavior(behavior: number): void
```

设置音频会话行为参数，支持多种标志位的组合使用。

> **说明：**  
>  
> 当音频会话在激活状态时调用此接口后，必须重新调用接口[activateAudioSession](arkts-audio-audio-audiosessionmanager-i.md#activateaudiosession-1)使其生效。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSessionManager-setAudioSessionBehavior(behavior: int): void--><!--Device-AudioSessionManager-setAudioSessionBehavior(behavior: int): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| behavior | number | 是 | 用于设置音频会话行为。<br>该参数可以是单个标志，也可以是多个标志的按位OR组合。<br>当前支持的音频会话行为详见[AudioSessionBehaviorFlags](arkts-audio-audio-audiosessionbehaviorflags-e.md)中定义的标志。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Operation not permitted in the current state. |

<a id="setaudiosessionscene"></a>
## setAudioSessionScene

```TypeScript
setAudioSessionScene(scene: AudioSessionScene): void
```

设置音频会话场景参数。

**起始版本：** 20

<!--Device-AudioSessionManager-setAudioSessionScene(scene: AudioSessionScene): void--><!--Device-AudioSessionManager-setAudioSessionScene(scene: AudioSessionScene): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scene | [AudioSessionScene](arkts-audio-audio-audiosessionscene-e.md) | 是 | 音频会话场景。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Operation not permit at current state. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, System error. |

<a id="setbluetoothandnearlinkpreferredrecordcategory"></a>
## setBluetoothAndNearlinkPreferredRecordCategory

```TypeScript
setBluetoothAndNearlinkPreferredRecordCategory(category: BluetoothAndNearlinkPreferredRecordCategory): Promise<void>
```

设置在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。使用Promise异步回调。

> **说明：**  
>  
> - 应用程序可以在蓝牙或星闪连接之前设置此分类，系统将在设备连接时优先使用蓝牙或星闪进行录音。  
>  
> - 当系统中存在其他更高优先级的应用录音流时，实际使用的输入设备会跟随其他高优先级应用所选的输入设备。  
>  
> - 应用程序可以监听  
> [currentInputDeviceChanged](audio.AudioSessionManager.on(type: 'currentInputDeviceChanged', callback: Callback<CurrentInputDeviceChangedEvent>))  
> 事件来获得实际的输入设备。

**起始版本：** 21

<!--Device-AudioSessionManager-setBluetoothAndNearlinkPreferredRecordCategory(category: BluetoothAndNearlinkPreferredRecordCategory): Promise<void>--><!--Device-AudioSessionManager-setBluetoothAndNearlinkPreferredRecordCategory(category: BluetoothAndNearlinkPreferredRecordCategory): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| category | [BluetoothAndNearlinkPreferredRecordCategory](arkts-audio-audio-bluetoothandnearlinkpreferredrecordcategory-e.md) | 是 | 在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, System error. |

<a id="setcapturermutehint"></a>
## setCapturerMuteHint

```TypeScript
setCapturerMuteHint(mute: boolean): Promise<void>
```

应用将当前音频会话内录音流的自身静音状态传递给系统音频模块。<!--RP1-->该接口不会触发录音流静音，当前仅在部分PC/2in1设备上用于优化设备功耗。<!--RP1End-->使用Promise异步回调。

> **说明：**  
>  
> - 该接口用于向系统音频模块上报当前音频会话内录音流的静音状态，不会改变录音流的实际静音状态。  
>  
> - 该接口仅在当前音频会话存在运行中的录音流时允许调用，否则返回错误码6800103。  
>  
> - 若某条录音流同时调用了流级接口[AudioCapturer.setMuteHint](arkts-audio-audio-audiocapturer-i.md#setmutehint-1)和本接口，流级接口设置优先级更高，以流级接口设置值为准。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSessionManager-setCapturerMuteHint(mute: boolean): Promise<void>--><!--Device-AudioSessionManager-setCapturerMuteHint(mute: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | 应用自身给系统音频模块上报的静音状态。true表示应用将当前流静音，false表示取消静音。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Operation not permitted at current state, there is no audio capturer running. |

<a id="setdefaultoutputdevice"></a>
## setDefaultOutputDevice

```TypeScript
setDefaultOutputDevice(deviceType: DeviceType): Promise<void>
```

设置默认发声设备。使用Promise方式进行异步回调。

> **说明：**  
>  
> - 本接口适用于以下情况：当设置的[AudioSessionScene](arkts-audio-audio-audiosessionscene-e.md)为VoIP场景时，激活AudioSession后立即生效。若  
> [AudioSessionScene](arkts-audio-audio-audiosessionscene-e.md)为非VoIP场景，激活AudioSession时不会生效，仅在启动播放的  
> [StreamUsage](arkts-audio-audio-streamusage-e.md)为语音消息、VoIP语音通话或VoIP视频通话时才生效。支持听筒、扬声器和系统默认设备。  
>  
> - 本接口允许在AudioSessionManager创建后随时调用，系统会记录应用设置的默认本机内置发声设备。但只有激活AudioSession后才能生效。应用启动播放时，若外接设备如蓝牙耳机或有线耳机已接入，系统优先从  
> 外接设备发声。否则，系统遵循应用设置的默认本机内置发声设备。

**起始版本：** 20

<!--Device-AudioSessionManager-setDefaultOutputDevice(deviceType: DeviceType): Promise<void>--><!--Device-AudioSessionManager-setDefaultOutputDevice(deviceType: DeviceType): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | [DeviceType](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-devicetype-e.md) | 是 | 设备类型。<br>仅支持以下设备：EARPIECE（听筒）、SPEAKER（扬声器）和DEFAULT（系统默认设备）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by promise. |
| [6800102](../errorcode-audio.md#6800102-分配内存失败) | Allocate memory failed. Return by promise. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio client call audio service error, System error. |

<a id="setmediaoutputdevice"></a>
## setMediaOutputDevice

```TypeScript
setMediaOutputDevice(deviceType: DeviceType): Promise<void>
```

当连接其他音频外设（如蓝牙耳机或有线耳机）时，将媒体输出设备切换为内置扬声器。使用Promise异步回调。

> **说明：**  
>  
> - 本接口仅适用于媒体播放场景，并且会作用于应用内发起的所有媒体流。  
>  
> - 若存在更高优先级的并发播放流或用户手动选择输出设备，则应用程序实际使用的输出设备将与本接口设置的设备不同。应用程序可通过监听  
> [CurrentOutputDeviceChangedEvent](arkts-audio-audio-currentoutputdevicechangedevent-i.md)事件获取当前活跃的输出设备。  
>  
> - 当应用程序需要清除之前通过接口设置的扬声器输出配置时，可通过调用接口将媒体输出设备设置为DEFAULT（系统默认设备）来实现。该设置仅在应用程序运行期间有效，当应用程序退出时，此接口的设置将自动清除。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSessionManager-setMediaOutputDevice(deviceType: DeviceType): Promise<void>--><!--Device-AudioSessionManager-setMediaOutputDevice(deviceType: DeviceType): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | [DeviceType](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-devicetype-e.md) | 是 | 设备类型。<br>仅支持以下设备：SPEAKER（扬声器）和DEFAULT（系统默认设备）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed, for example,the selected device type is not supported. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Possible causes:1.Internal variable memory allocation failed.2.Audio server process died.3.Speaker device is not available. |

