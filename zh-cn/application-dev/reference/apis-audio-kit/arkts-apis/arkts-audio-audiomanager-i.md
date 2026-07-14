# AudioManager

音频音量和设备管理。

在使用AudioManager的接口之前，需先通过[getAudioManager](arkts-audio-getaudiomanager-f.md#getaudiomanager-1)获取AudioManager实例。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Audio.Core

## getAudioParameter

```TypeScript
getAudioParameter(key: string, callback: AsyncCallback<string>): void
```

获取指定音频参数值。使用callback异步回调。

本接口的使用场景为：根据硬件设备的支持能力扩展音频配置。在不同的设备平台上，所支持的音频参数会存在差异。示例代码内使用样例参数，实际支持的音频配置参数见具体设备平台的资料描述。

> **说明：**
>
> 从API version 7开始支持，从API version 11开始废弃。

**起始版本：** 7

**废弃版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待获取的音频参数的键。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。当获取指定音频参数值成功，err为undefined，data为获取到的指定音频参数值；否则为错误对象。 |

## getAudioParameter

```TypeScript
getAudioParameter(key: string): Promise<string>
```

获取指定音频参数值。使用Promise异步回调。

本接口的使用场景为：根据硬件设备的支持能力扩展音频配置。在不同的设备平台上，所支持的音频参数会存在差异。示例代码内使用样例参数，实际支持的音频配置参数见具体设备平台的资料描述。

> **说明：**
>
> 从API version 7开始支持，从API version 11开始废弃。

**起始版本：** 7

**废弃版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待获取的音频参数的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回获取的音频参数值。 |

## getAudioScene

```TypeScript
getAudioScene(callback: AsyncCallback<AudioScene>): void
```

获取音频场景模式。使用callback异步回调。

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;AudioScene&gt; | 是 | 回调函数。当获取音频场景模式成功，err为undefined，data为获取到的音频场景模式；否则为错误对象。 |

## getAudioScene

```TypeScript
getAudioScene(): Promise<AudioScene>
```

获取音频场景模式。使用Promise异步回调。

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AudioScene&gt; | Promise对象，返回音频场景模式。 |

## getAudioSceneSync

```TypeScript
getAudioSceneSync(): AudioScene
```

获取音频场景模式。同步返回结果。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AudioScene | 音频场景模式。 |

## getDebuggingManager

```TypeScript
getDebuggingManager(): AudioDebuggingManager
```

获取音频调试管理器实例。该实例为单例，获取后可重复使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AudioDebuggingManager | 返回AudioDebuggingManager实例。 |

## getDeviceEnhanceManager

```TypeScript
getDeviceEnhanceManager(): AudioDeviceEnhanceManager
```

获取音频设备增强管理器实例。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.DeviceEnhance

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AudioDeviceEnhanceManager | 返回一个AudioDeviceEnhanceManager实例。 |

## getDevices

```TypeScript
getDevices(deviceFlag: DeviceFlag, callback: AsyncCallback<AudioDeviceDescriptors>): void
```

获取音频设备列表。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getDevices

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceFlag | DeviceFlag | 是 | 音频设备类型。 |
| callback | AsyncCallback&lt;AudioDeviceDescriptors&gt; | 是 | 回调函数。当获取音频设备列表成功，err为undefined，data为获取到的音频设备列表；否则为错误对象。 |

## getDevices

```TypeScript
getDevices(deviceFlag: DeviceFlag): Promise<AudioDeviceDescriptors>
```

获取音频设备列表。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getDevices

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceFlag | DeviceFlag | 是 | 音频设备类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AudioDeviceDescriptors&gt; | Promise对象，返回设备列表。 |

## getMaxVolume

```TypeScript
getMaxVolume(volumeType: AudioVolumeType, callback: AsyncCallback<number>): void
```

获取指定流的最大音量等级。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。在API version 9-19

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getMaxVolume

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | 音频音量类型。 |
| callback | AsyncCallback&lt;number&gt; | 是 | 回调函数。当获取指定流的最大音量成功，err为undefined，data为获取到的指定流的最大音量等级；否则为错误对象。 |

## getMaxVolume

```TypeScript
getMaxVolume(volumeType: AudioVolumeType): Promise<number>
```

获取指定流的最大音量等级。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。在API version 9-19

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getMaxVolume

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回最大音量等级。 |

## getMinVolume

```TypeScript
getMinVolume(volumeType: AudioVolumeType, callback: AsyncCallback<number>): void
```

获取指定流的最小音量等级。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。在API version 9-19

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getMinVolume

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | 音频音量类型。 |
| callback | AsyncCallback&lt;number&gt; | 是 | 回调函数。当获取指定流的最小音量成功，err为undefined，data为获取到的指定流的最小音量等级；否则为错误对象。 |

## getMinVolume

```TypeScript
getMinVolume(volumeType: AudioVolumeType): Promise<number>
```

获取指定流的最小音量等级。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。在API version 9-19

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getMinVolume

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回最小音量等级。 |

## getRingerMode

```TypeScript
getRingerMode(callback: AsyncCallback<AudioRingMode>): void
```

获取铃声模式。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getRingerMode

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;AudioRingMode&gt; | 是 | 回调函数。当获取铃声模式成功，err为undefined，data为获取到的铃声模式；否则为错误对象。 |

## getRingerMode

```TypeScript
getRingerMode(): Promise<AudioRingMode>
```

获取铃声模式。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getRingerMode

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AudioRingMode&gt; | Promise对象，返回系统的铃声模式。 |

## getRoutingManager

```TypeScript
getRoutingManager(): AudioRoutingManager
```

获取音频路由管理器。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AudioRoutingManager | AudioRoutingManager实例。 |

## getSessionManager

```TypeScript
getSessionManager(): AudioSessionManager
```

获取音频会话管理器。

**起始版本：** 12

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AudioSessionManager | AudioSessionManager实例。 |

## getSpatializationManager

```TypeScript
getSpatializationManager(): AudioSpatializationManager
```

获取空间音频管理器。

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AudioSpatializationManager | AudioSpatializationManager实例。 |

## getStreamManager

```TypeScript
getStreamManager(): AudioStreamManager
```

获取音频流管理器。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AudioStreamManager | AudioStreamManager实例。 |

## getVolume

```TypeScript
getVolume(volumeType: AudioVolumeType, callback: AsyncCallback<number>): void
```

获取指定流的音量等级。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。在API version 9-19

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getVolume

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | 音频音量类型。 |
| callback | AsyncCallback&lt;number&gt; | 是 | 回调函数。当获取指定流的音量成功，err为undefined，data为获取到的指定流的音量等级；否则为错误对象。指定流的音量等级范围可通过[getMinVolume](arkts-audio-audiomanager-i.md#getminvolume-1)和[getMaxVolume](arkts-audio-audiomanager-i.md#getmaxvolume-1)获取。 |

## getVolume

```TypeScript
getVolume(volumeType: AudioVolumeType): Promise<number>
```

获取指定流的音量等级。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。在API version 9-19

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getVolume

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回指定流的音量等级。指定流的音量等级范围可通过[getMinVolume](arkts-audio-audiomanager-i.md#getminvolume-1)和[getMaxVolume](arkts-audio-audiomanager-i.md#getmaxvolume-1)获取。 |

## getVolumeManager

```TypeScript
getVolumeManager(): AudioVolumeManager
```

获取音频音量管理器。

**起始版本：** 9

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AudioVolumeManager | AudioVolumeManager实例。 |

## isActive

```TypeScript
isActive(volumeType: AudioVolumeType, callback: AsyncCallback<boolean>): void
```

获取指定音量流的活跃状态。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。在API version 9-19

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isActive

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | 音频音量类型。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。当获取指定音量流的活跃状态成功，err为undefined，data为true表示活跃，false表示不活跃；否则为错误对象。 |

## isActive

```TypeScript
isActive(volumeType: AudioVolumeType): Promise<boolean>
```

获取指定音量流的活跃状态。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。在API version 9-19

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isActive

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示流状态为活跃；返回false表示流状态不活跃。 |

## isDeviceActive

```TypeScript
isDeviceActive(deviceType: ActiveDeviceType, callback: AsyncCallback<boolean>): void
```

获取指定设备的激活状态。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isCommunicationDeviceActive

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | ActiveDeviceType | 是 | 活跃音频设备类型。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。当获取指定设备的激活状态成功，err为undefined，data为true表示激活，false表示未激活；否则为错误对象。 |

## isDeviceActive

```TypeScript
isDeviceActive(deviceType: ActiveDeviceType): Promise<boolean>
```

获取指定设备的激活状态。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isCommunicationDeviceActive

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | ActiveDeviceType | 是 | 活跃音频设备类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示设备已激活；返回false表示设备未激活。 |

## isMicrophoneMute

```TypeScript
isMicrophoneMute(callback: AsyncCallback<boolean>): void
```

获取麦克风静音状态。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isMicrophoneMute

**需要权限：** ohos.permission.MICROPHONE

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。当获取麦克风静音状态成功，err为undefined，data为true表示静音，false表示非静音；否则为错误对象。 |

## isMicrophoneMute

```TypeScript
isMicrophoneMute(): Promise<boolean>
```

获取麦克风静音状态。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isMicrophoneMute

**需要权限：** ohos.permission.MICROPHONE

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示麦克风被静音；返回false表示麦克风未被静音。 |

## isMute

```TypeScript
isMute(volumeType: AudioVolumeType, callback: AsyncCallback<boolean>): void
```

获取指定音量流的静音状态。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。在API version 9-19

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isMute

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | 音频音量类型。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。当获取指定音量流的静音状态成功，err为undefined，data为true表示静音，false表示非静音；否则为错误对象。 |

## isMute

```TypeScript
isMute(volumeType: AudioVolumeType): Promise<boolean>
```

获取指定音量流的静音状态。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。在API version 9-19

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isMute

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示静音；返回false表示非静音。 |

## mute

```TypeScript
mute(volumeType: AudioVolumeType, mute: boolean, callback: AsyncCallback<void>): void
```

设置指定音量流静音。使用callback异步回调。

当该音量流可设置的最小音量不能为0时，不支持静音操作。例如：闹钟和通话。

> **说明：**
>
> - 从API version 7开始支持，从API version 9开始废弃。
>
> - 应用无法直接静音流音量，建议通过系统音量面板组件进行静音。具体样例和介绍请参考API文档
> [@ohos.multimedia.avVolumePanel (音量面板)](arkts-multimedia-avvolumepanel.md)。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** AVVolumePanel

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | 音频音量类型。 |
| mute | boolean | 是 | 是否设置指定音量流为静音状态。true表示静音，false表示非静音。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置指定音量流静音成功，err为undefined，否则为错误对象。 |

## mute

```TypeScript
mute(volumeType: AudioVolumeType, mute: boolean): Promise<void>
```

设置指定音量流静音。使用Promise异步回调。

当该音量流可设置的最小音量不能为0时，不支持静音操作。例如：闹钟和通话。

> **说明：**
>
> - 从API version 7开始支持，从API version 9开始废弃。
>
> - 应用无法直接静音流音量，建议通过系统音量面板组件进行静音。具体样例和介绍请参考API文档
> [@ohos.multimedia.avVolumePanel (音量面板)](arkts-multimedia-avvolumepanel.md)。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** AVVolumePanel

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | 音频音量类型。 |
| mute | boolean | 是 | 是否设置指定音量流为静音状态。true表示静音，false表示非静音。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

## off('audioSceneChange')

```TypeScript
off(type: 'audioSceneChange', callback?: Callback<AudioScene>): void
```

取消监听音频场景变化事件。使用callback异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioSceneChange' | 是 | 事件回调类型，支持的事件为'audioSceneChange'，当取消监听当前音频场景变化事件时，触发该事件。 |
| callback | Callback&lt;AudioScene&gt; | 否 | 回调函数，返回当前音频场景模式。 |

## off('deviceChange')

```TypeScript
off(type: 'deviceChange', callback?: Callback<DeviceChangeAction>): void
```

取消监听音频设备连接变化事件。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** event:deviceChange

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceChange' | 是 | 事件回调类型，支持的事件为'deviceChange'，当取消监听音频设备连接变化事件时，触发该事件。 |
| callback | Callback&lt;DeviceChangeAction&gt; | 否 | 回调函数，返回设备更新详情。 |

## off('interrupt')

```TypeScript
off(type: 'interrupt', interrupt: AudioInterrupt, callback?: Callback<InterruptAction>): void
```

取消监听音频打断事件。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** event:audioInterrupt

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'interrupt' | 是 | 事件回调类型，支持的事件为'interrupt'，当取消监听音频打断事件时，触发该事件。 |
| interrupt | AudioInterrupt | 是 | 音频打断事件类型的参数。 |
| callback | Callback&lt;InterruptAction&gt; | 否 | 回调函数，返回打断事件信息。 |

## on('audioSceneChange')

```TypeScript
on(type: 'audioSceneChange', callback: Callback<AudioScene>): void
```

监听音频场景变化事件。使用callback异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioSceneChange' | 是 | 事件回调类型，支持的事件为'audioSceneChange'，当音频场景模式发生变化时，触发该事件。 |
| callback | Callback&lt;AudioScene&gt; | 是 | 回调函数，返回当前音频场景模式。 |

## on('deviceChange')

```TypeScript
on(type: 'deviceChange', callback: Callback<DeviceChangeAction>): void
```

监听音频设备连接变化事件（当音频设备连接状态发生变化时触发）。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** event:deviceChange

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceChange' | 是 | 事件回调类型，支持的事件为'deviceChange'，当音频设备连接状态发生变化时，触发该事件。 |
| callback | Callback&lt;DeviceChangeAction&gt; | 是 | 回调函数，返回设备更新详情。 |

## on('interrupt')

```TypeScript
on(type: 'interrupt', interrupt: AudioInterrupt, callback: Callback<InterruptAction>): void
```

监听音频打断事件（当音频焦点发生变化时触发）。使用callback异步回调。

与[on('audioInterrupt')](arkts-audio-audiorenderer-i.md#on-1)
作用一致，均用于监听焦点变化。为无音频流的场景（未曾创建AudioRenderer对象），比如FM、语音唤醒等提供焦点变化监听功能。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** event:audioInterrupt

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'interrupt' | 是 | 事件回调类型，支持的事件为'interrupt'，当音频焦点状态发生变化时，触发该事件。 |
| interrupt | AudioInterrupt | 是 | 音频打断事件类型的参数。 |
| callback | Callback&lt;InterruptAction&gt; | 是 | 回调函数，返回打断事件信息。 |

## setAudioParameter

```TypeScript
setAudioParameter(key: string, value: string, callback: AsyncCallback<void>): void
```

音频参数设置。使用callback异步回调。

接口根据硬件设备的支持能力扩展音频配置。支持的参数与产品和设备强相关，非通用参数，示例代码内使用样例参数。

> **说明：**
>
> 从API version 7开始支持，从API version 11开始废弃。

**起始版本：** 7

**废弃版本：** 11

**需要权限：** ohos.permission.MODIFY_AUDIO_SETTINGS

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 被设置的音频参数的键。 |
| value | string | 是 | 被设置的音频参数的值。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当音频参数设置成功，err为undefined，否则为错误对象。 |

## setAudioParameter

```TypeScript
setAudioParameter(key: string, value: string): Promise<void>
```

音频参数设置。使用Promise异步回调。

接口根据硬件设备的支持能力扩展音频配置。支持的参数与产品和设备强相关，非通用参数，示例代码内使用样例参数。

> **说明：**
>
> 从API version 7开始支持，从API version 11开始废弃。

**起始版本：** 7

**废弃版本：** 11

**需要权限：** ohos.permission.MODIFY_AUDIO_SETTINGS

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 被设置的音频参数的键。 |
| value | string | 是 | 被设置的音频参数的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

## setDeviceActive

```TypeScript
setDeviceActive(deviceType: ActiveDeviceType, active: boolean, callback: AsyncCallback<void>): void
```

设置设备激活状态。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setCommunicationDevice

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | ActiveDeviceType | 是 | 活跃音频设备类型。 |
| active | boolean | 是 | 是否设置设备为激活状态。true表示已激活，false表示未激活。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置设备激活状态成功，err为undefined，否则为错误对象。 |

## setDeviceActive

```TypeScript
setDeviceActive(deviceType: ActiveDeviceType, active: boolean): Promise<void>
```

设置设备激活状态。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setCommunicationDevice

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | ActiveDeviceType | 是 | 活跃音频设备类型。 |
| active | boolean | 是 | 是否设置设备为激活状态。true表示已激活，false表示未激活。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

## setMicrophoneMute

```TypeScript
setMicrophoneMute(mute: boolean, callback: AsyncCallback<void>): void
```

设置麦克风静音状态。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.MICROPHONE

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | 是否设置麦克风为静音状态。true表示静音，false表示非静音。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置麦克风静音状态成功，err为undefined，否则为错误对象。 |

## setMicrophoneMute

```TypeScript
setMicrophoneMute(mute: boolean): Promise<void>
```

设置麦克风静音状态。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.MICROPHONE

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | 是否设置麦克风为静音状态。true表示静音，false表示非静音。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

## setRingerMode

```TypeScript
setRingerMode(mode: AudioRingMode, callback: AsyncCallback<void>): void
```

设置铃声模式。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | AudioRingMode | 是 | 音频铃声模式。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置铃声模式成功，err为undefined，否则为错误对象。 |

## setRingerMode

```TypeScript
setRingerMode(mode: AudioRingMode): Promise<void>
```

设置铃声模式。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | AudioRingMode | 是 | 音频铃声模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

## setVolume

```TypeScript
setVolume(volumeType: AudioVolumeType, volume: number, callback: AsyncCallback<void>): void
```

设置指定流的音量等级。使用callback异步回调。

> **说明：**
>
> - 从API version 7开始支持，从API version 9开始废弃。
>
> - 应用无法直接调节系统音量，建议通过系统音量面板组件调节音量。具体样例和介绍请参考API文档
> [@ohos.multimedia.avVolumePanel (音量面板)](arkts-multimedia-avvolumepanel.md)。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** AVVolumePanel

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | 音频音量类型。 |
| volume | number | 是 | 音量等级，可设置范围通过[getMinVolume](arkts-audio-audiomanager-i.md#getminvolume-1)和[getMaxVolume](arkts-audio-audiomanager-i.md#getmaxvolume-1)获取。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置指定流的音量成功，err为undefined，否则为错误对象。 |

## setVolume

```TypeScript
setVolume(volumeType: AudioVolumeType, volume: number): Promise<void>
```

设置指定流的音量等级。使用Promise异步回调。

> **说明：**
>
> - 从API version 7开始支持，从API version 9开始废弃。
>
> - 应用无法直接调节系统音量，建议通过系统音量面板组件调节音量。具体样例和介绍请参考API文档
> [@ohos.multimedia.avVolumePanel (音量面板)](arkts-multimedia-avvolumepanel.md)。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** AVVolumePanel

**需要权限：** ohos.permission.ACCESS_NOTIFICATION_POLICY

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | AudioVolumeType | 是 | 音频音量类型。 |
| volume | number | 是 | 音量等级，可设置范围通过[getMinVolume](arkts-audio-audiomanager-i.md#getminvolume-1)和[getMaxVolume](arkts-audio-audiomanager-i.md#getmaxvolume-1)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

