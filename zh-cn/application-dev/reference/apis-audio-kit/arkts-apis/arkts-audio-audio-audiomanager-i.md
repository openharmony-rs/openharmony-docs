# AudioManager

音频音量和设备管理。

在使用AudioManager的接口之前，需先通过[getAudioManager](arkts-audio-audio-getaudiomanager-f.md#getaudiomanager-1)获取AudioManager实例。

**起始版本：** 7

<!--Device-audio-interface AudioManager--><!--Device-audio-interface AudioManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

<a id="getaudioparameter"></a>
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

<!--Device-AudioManager-getAudioParameter(key: string, callback: AsyncCallback<string>): void--><!--Device-AudioManager-getAudioParameter(key: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待获取的音频参数的键。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。当获取指定音频参数值成功，err为undefined，data为获取到的指定音频参数值；否则为错误对象。 |

<a id="getaudioparameter-1"></a>
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

<!--Device-AudioManager-getAudioParameter(key: string): Promise<string>--><!--Device-AudioManager-getAudioParameter(key: string): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待获取的音频参数的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回获取的音频参数值。 |

<a id="getaudioscene"></a>
## getAudioScene

```TypeScript
getAudioScene(callback: AsyncCallback<AudioScene>): void
```

获取音频场景模式。使用callback异步回调。

**起始版本：** 8

<!--Device-AudioManager-getAudioScene(callback: AsyncCallback<AudioScene>): void--><!--Device-AudioManager-getAudioScene(callback: AsyncCallback<AudioScene>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;AudioScene&gt; | 是 | 回调函数。当获取音频场景模式成功，err为undefined，data为获取到的音频场景模式；否则为错误对象。 |

<a id="getaudioscene-1"></a>
## getAudioScene

```TypeScript
getAudioScene(): Promise<AudioScene>
```

获取音频场景模式。使用Promise异步回调。

**起始版本：** 8

<!--Device-AudioManager-getAudioScene(): Promise<AudioScene>--><!--Device-AudioManager-getAudioScene(): Promise<AudioScene>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AudioScene&gt; | Promise对象，返回音频场景模式。 |

<a id="getaudioscenesync"></a>
## getAudioSceneSync

```TypeScript
getAudioSceneSync(): AudioScene
```

获取音频场景模式。同步返回结果。

**起始版本：** 10

<!--Device-AudioManager-getAudioSceneSync(): AudioScene--><!--Device-AudioManager-getAudioSceneSync(): AudioScene-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioScene](arkts-audio-audio-audioscene-e.md) | 音频场景模式。 |

<a id="getdebuggingmanager"></a>
## getDebuggingManager

```TypeScript
getDebuggingManager(): AudioDebuggingManager
```

获取音频调试管理器实例。该实例为单例，获取后可重复使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioManager-getDebuggingManager(): AudioDebuggingManager--><!--Device-AudioManager-getDebuggingManager(): AudioDebuggingManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioDebuggingManager](arkts-audio-audio-audiodebuggingmanager-i.md) | 返回AudioDebuggingManager实例。 |

<a id="getdeviceenhancemanager"></a>
## getDeviceEnhanceManager

```TypeScript
getDeviceEnhanceManager(): AudioDeviceEnhanceManager
```

获取音频设备增强管理器实例。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioManager-getDeviceEnhanceManager(): AudioDeviceEnhanceManager--><!--Device-AudioManager-getDeviceEnhanceManager(): AudioDeviceEnhanceManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.DeviceEnhance

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioDeviceEnhanceManager](arkts-audio-audio-audiodeviceenhancemanager-i.md) | 返回一个AudioDeviceEnhanceManager实例。 |

<a id="getdevices"></a>
## getDevices

```TypeScript
getDevices(deviceFlag: DeviceFlag, callback: AsyncCallback<AudioDeviceDescriptors>): void
```

获取音频设备列表。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getDevices

<!--Device-AudioManager-getDevices(deviceFlag: DeviceFlag, callback: AsyncCallback<AudioDeviceDescriptors>): void--><!--Device-AudioManager-getDevices(deviceFlag: DeviceFlag, callback: AsyncCallback<AudioDeviceDescriptors>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceFlag | [DeviceFlag](arkts-audio-audio-deviceflag-e.md) | 是 | 音频设备类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;AudioDeviceDescriptors&gt; | 是 | 回调函数。当获取音频设备列表成功，err为undefined，data为获取到的音频设备列表；否则为错误对象。 |

<a id="getdevices-1"></a>
## getDevices

```TypeScript
getDevices(deviceFlag: DeviceFlag): Promise<AudioDeviceDescriptors>
```

获取音频设备列表。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getDevices

<!--Device-AudioManager-getDevices(deviceFlag: DeviceFlag): Promise<AudioDeviceDescriptors>--><!--Device-AudioManager-getDevices(deviceFlag: DeviceFlag): Promise<AudioDeviceDescriptors>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceFlag | [DeviceFlag](arkts-audio-audio-deviceflag-e.md) | 是 | 音频设备类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AudioDeviceDescriptors&gt; | Promise对象，返回设备列表。 |

<a id="getmaxvolume"></a>
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

<!--Device-AudioManager-getMaxVolume(volumeType: AudioVolumeType, callback: AsyncCallback<number>): void--><!--Device-AudioManager-getMaxVolume(volumeType: AudioVolumeType, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当获取指定流的最大音量成功，err为undefined，data为获取到的指定流的最大音量等级；否则为错误对象。 |

<a id="getmaxvolume-1"></a>
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

<!--Device-AudioManager-getMaxVolume(volumeType: AudioVolumeType): Promise<number>--><!--Device-AudioManager-getMaxVolume(volumeType: AudioVolumeType): Promise<number>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回最大音量等级。 |

<a id="getminvolume"></a>
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

<!--Device-AudioManager-getMinVolume(volumeType: AudioVolumeType, callback: AsyncCallback<number>): void--><!--Device-AudioManager-getMinVolume(volumeType: AudioVolumeType, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当获取指定流的最小音量成功，err为undefined，data为获取到的指定流的最小音量等级；否则为错误对象。 |

<a id="getminvolume-1"></a>
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

<!--Device-AudioManager-getMinVolume(volumeType: AudioVolumeType): Promise<number>--><!--Device-AudioManager-getMinVolume(volumeType: AudioVolumeType): Promise<number>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回最小音量等级。 |

<a id="getringermode"></a>
## getRingerMode

```TypeScript
getRingerMode(callback: AsyncCallback<AudioRingMode>): void
```

获取铃声模式。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getRingerMode

<!--Device-AudioManager-getRingerMode(callback: AsyncCallback<AudioRingMode>): void--><!--Device-AudioManager-getRingerMode(callback: AsyncCallback<AudioRingMode>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;AudioRingMode&gt; | 是 | 回调函数。当获取铃声模式成功，err为undefined，data为获取到的铃声模式；否则为错误对象。 |

<a id="getringermode-1"></a>
## getRingerMode

```TypeScript
getRingerMode(): Promise<AudioRingMode>
```

获取铃声模式。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getRingerMode

<!--Device-AudioManager-getRingerMode(): Promise<AudioRingMode>--><!--Device-AudioManager-getRingerMode(): Promise<AudioRingMode>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AudioRingMode&gt; | Promise对象，返回系统的铃声模式。 |

<a id="getroutingmanager"></a>
## getRoutingManager

```TypeScript
getRoutingManager(): AudioRoutingManager
```

获取音频路由管理器。

**起始版本：** 9

<!--Device-AudioManager-getRoutingManager(): AudioRoutingManager--><!--Device-AudioManager-getRoutingManager(): AudioRoutingManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioRoutingManager](arkts-audio-audio-audioroutingmanager-i.md) | AudioRoutingManager实例。 |

<a id="getsessionmanager"></a>
## getSessionManager

```TypeScript
getSessionManager(): AudioSessionManager
```

获取音频会话管理器。

**起始版本：** 12

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AudioManager-getSessionManager(): AudioSessionManager--><!--Device-AudioManager-getSessionManager(): AudioSessionManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioSessionManager](arkts-audio-audio-audiosessionmanager-i.md) | AudioSessionManager实例。 |

<a id="getspatializationmanager"></a>
## getSpatializationManager

```TypeScript
getSpatializationManager(): AudioSpatializationManager
```

获取空间音频管理器。

**起始版本：** 18

<!--Device-AudioManager-getSpatializationManager(): AudioSpatializationManager--><!--Device-AudioManager-getSpatializationManager(): AudioSpatializationManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioSpatializationManager](arkts-audio-audio-audiospatializationmanager-i.md) | AudioSpatializationManager实例。 |

<a id="getstreammanager"></a>
## getStreamManager

```TypeScript
getStreamManager(): AudioStreamManager
```

获取音频流管理器。

**起始版本：** 9

<!--Device-AudioManager-getStreamManager(): AudioStreamManager--><!--Device-AudioManager-getStreamManager(): AudioStreamManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioStreamManager](arkts-audio-audio-audiostreammanager-i.md) | AudioStreamManager实例。 |

<a id="getvolume"></a>
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

<!--Device-AudioManager-getVolume(volumeType: AudioVolumeType, callback: AsyncCallback<number>): void--><!--Device-AudioManager-getVolume(volumeType: AudioVolumeType, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当获取指定流的音量成功，err为undefined，data为获取到的指定流的音量等级；否则为错误对象。指定流的音量等级范围可通过[getMinVolume](arkts-audio-audio-audiomanager-i.md#getminvolume-1)和[getMaxVolume](arkts-audio-audio-audiomanager-i.md#getmaxvolume-1)获取。 |

<a id="getvolume-1"></a>
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

<!--Device-AudioManager-getVolume(volumeType: AudioVolumeType): Promise<number>--><!--Device-AudioManager-getVolume(volumeType: AudioVolumeType): Promise<number>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回指定流的音量等级。指定流的音量等级范围可通过[getMinVolume](arkts-audio-audio-audiomanager-i.md#getminvolume-1)和[getMaxVolume](arkts-audio-audio-audiomanager-i.md#getmaxvolume-1)获取。 |

<a id="getvolumemanager"></a>
## getVolumeManager

```TypeScript
getVolumeManager(): AudioVolumeManager
```

获取音频音量管理器。

**起始版本：** 9

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AudioManager-getVolumeManager(): AudioVolumeManager--><!--Device-AudioManager-getVolumeManager(): AudioVolumeManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioVolumeManager](arkts-audio-audio-audiovolumemanager-i.md) | AudioVolumeManager实例。 |

<a id="isactive"></a>
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

<!--Device-AudioManager-isActive(volumeType: AudioVolumeType, callback: AsyncCallback<boolean>): void--><!--Device-AudioManager-isActive(volumeType: AudioVolumeType, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。当获取指定音量流的活跃状态成功，err为undefined，data为true表示活跃，false表示不活跃；否则为错误对象。 |

<a id="isactive-1"></a>
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

<!--Device-AudioManager-isActive(volumeType: AudioVolumeType): Promise<boolean>--><!--Device-AudioManager-isActive(volumeType: AudioVolumeType): Promise<boolean>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示流状态为活跃；返回false表示流状态不活跃。 |

<a id="isdeviceactive"></a>
## isDeviceActive

```TypeScript
isDeviceActive(deviceType: ActiveDeviceType, callback: AsyncCallback<boolean>): void
```

获取指定设备的激活状态。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isCommunicationDeviceActive

<!--Device-AudioManager-isDeviceActive(deviceType: ActiveDeviceType, callback: AsyncCallback<boolean>): void--><!--Device-AudioManager-isDeviceActive(deviceType: ActiveDeviceType, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | [ActiveDeviceType](arkts-audio-audio-activedevicetype-e.md) | 是 | 活跃音频设备类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。当获取指定设备的激活状态成功，err为undefined，data为true表示激活，false表示未激活；否则为错误对象。 |

<a id="isdeviceactive-1"></a>
## isDeviceActive

```TypeScript
isDeviceActive(deviceType: ActiveDeviceType): Promise<boolean>
```

获取指定设备的激活状态。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isCommunicationDeviceActive

<!--Device-AudioManager-isDeviceActive(deviceType: ActiveDeviceType): Promise<boolean>--><!--Device-AudioManager-isDeviceActive(deviceType: ActiveDeviceType): Promise<boolean>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | [ActiveDeviceType](arkts-audio-audio-activedevicetype-e.md) | 是 | 活跃音频设备类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示设备已激活；返回false表示设备未激活。 |

<a id="ismicrophonemute"></a>
## isMicrophoneMute

```TypeScript
isMicrophoneMute(callback: AsyncCallback<boolean>): void
```

获取麦克风静音状态。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isMicrophoneMute

**需要权限：** ohos.permission.MICROPHONE

<!--Device-AudioManager-isMicrophoneMute(callback: AsyncCallback<boolean>): void--><!--Device-AudioManager-isMicrophoneMute(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。当获取麦克风静音状态成功，err为undefined，data为true表示静音，false表示非静音；否则为错误对象。 |

<a id="ismicrophonemute-1"></a>
## isMicrophoneMute

```TypeScript
isMicrophoneMute(): Promise<boolean>
```

获取麦克风静音状态。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isMicrophoneMute

**需要权限：** ohos.permission.MICROPHONE

<!--Device-AudioManager-isMicrophoneMute(): Promise<boolean>--><!--Device-AudioManager-isMicrophoneMute(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示麦克风被静音；返回false表示麦克风未被静音。 |

<a id="ismute"></a>
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

<!--Device-AudioManager-isMute(volumeType: AudioVolumeType, callback: AsyncCallback<boolean>): void--><!--Device-AudioManager-isMute(volumeType: AudioVolumeType, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。当获取指定音量流的静音状态成功，err为undefined，data为true表示静音，false表示非静音；否则为错误对象。 |

<a id="ismute-1"></a>
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

<!--Device-AudioManager-isMute(volumeType: AudioVolumeType): Promise<boolean>--><!--Device-AudioManager-isMute(volumeType: AudioVolumeType): Promise<boolean>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示静音；返回false表示非静音。 |

<a id="mute"></a>
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

<!--Device-AudioManager-mute(volumeType: AudioVolumeType, mute: boolean, callback: AsyncCallback<void>): void--><!--Device-AudioManager-mute(volumeType: AudioVolumeType, mute: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| mute | boolean | 是 | 是否设置指定音量流为静音状态。true表示静音，false表示非静音。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置指定音量流静音成功，err为undefined，否则为错误对象。 |

<a id="mute-1"></a>
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

<!--Device-AudioManager-mute(volumeType: AudioVolumeType, mute: boolean): Promise<void>--><!--Device-AudioManager-mute(volumeType: AudioVolumeType, mute: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| mute | boolean | 是 | 是否设置指定音量流为静音状态。true表示静音，false表示非静音。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

<a id="off"></a>
## off('audioSceneChange')

```TypeScript
off(type: 'audioSceneChange', callback?: Callback<AudioScene>): void
```

取消监听音频场景变化事件。使用callback异步回调。

**起始版本：** 20

<!--Device-AudioManager-off(type: 'audioSceneChange', callback?: Callback<AudioScene>): void--><!--Device-AudioManager-off(type: 'audioSceneChange', callback?: Callback<AudioScene>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioSceneChange' | 是 | 事件回调类型，支持的事件为'audioSceneChange'，当取消监听当前音频场景变化事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;AudioScene&gt; | 否 | 回调函数，返回当前音频场景模式。 |

<a id="off-1"></a>
## off('deviceChange')

```TypeScript
off(type: 'deviceChange', callback?: Callback<DeviceChangeAction>): void
```

取消监听音频设备连接变化事件。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** event:deviceChange

<!--Device-AudioManager-off(type: 'deviceChange', callback?: Callback<DeviceChangeAction>): void--><!--Device-AudioManager-off(type: 'deviceChange', callback?: Callback<DeviceChangeAction>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceChange' | 是 | 事件回调类型，支持的事件为'deviceChange'，当取消监听音频设备连接变化事件时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;DeviceChangeAction&gt; | 否 | 回调函数，返回设备更新详情。 |

<a id="off-2"></a>
## off('interrupt')

```TypeScript
off(type: 'interrupt', interrupt: AudioInterrupt, callback?: Callback<InterruptAction>): void
```

取消监听音频打断事件。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** event:audioInterrupt

<!--Device-AudioManager-off(type: 'interrupt', interrupt: AudioInterrupt, callback?: Callback<InterruptAction>): void--><!--Device-AudioManager-off(type: 'interrupt', interrupt: AudioInterrupt, callback?: Callback<InterruptAction>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'interrupt' | 是 | 事件回调类型，支持的事件为'interrupt'，当取消监听音频打断事件时，触发该事件。 |
| interrupt | [AudioInterrupt](arkts-audio-audio-audiointerrupt-i.md) | 是 | 音频打断事件类型的参数。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;InterruptAction&gt; | 否 | 回调函数，返回打断事件信息。 |

<a id="on"></a>
## on('audioSceneChange')

```TypeScript
on(type: 'audioSceneChange', callback: Callback<AudioScene>): void
```

监听音频场景变化事件。使用callback异步回调。

**起始版本：** 20

<!--Device-AudioManager-on(type: 'audioSceneChange', callback: Callback<AudioScene>): void--><!--Device-AudioManager-on(type: 'audioSceneChange', callback: Callback<AudioScene>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'audioSceneChange' | 是 | 事件回调类型，支持的事件为'audioSceneChange'，当音频场景模式发生变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;AudioScene&gt; | 是 | 回调函数，返回当前音频场景模式。 |

<a id="on-1"></a>
## on('deviceChange')

```TypeScript
on(type: 'deviceChange', callback: Callback<DeviceChangeAction>): void
```

监听音频设备连接变化事件（当音频设备连接状态发生变化时触发）。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** event:deviceChange

<!--Device-AudioManager-on(type: 'deviceChange', callback: Callback<DeviceChangeAction>): void--><!--Device-AudioManager-on(type: 'deviceChange', callback: Callback<DeviceChangeAction>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceChange' | 是 | 事件回调类型，支持的事件为'deviceChange'，当音频设备连接状态发生变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;DeviceChangeAction&gt; | 是 | 回调函数，返回设备更新详情。 |

<a id="on-2"></a>
## on('interrupt')

```TypeScript
on(type: 'interrupt', interrupt: AudioInterrupt, callback: Callback<InterruptAction>): void
```

监听音频打断事件（当音频焦点发生变化时触发）。使用callback异步回调。

与[on('audioInterrupt')](audio.AudioRenderer.on(type: 'audioInterrupt', callback: Callback<InterruptEvent>))作用一致，均用于监听焦点变化。为无音频流的场景（未曾创建AudioRenderer对象），比如FM、语音唤醒等提供焦点变化监听功能。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** event:audioInterrupt

<!--Device-AudioManager-on(type: 'interrupt', interrupt: AudioInterrupt, callback: Callback<InterruptAction>): void--><!--Device-AudioManager-on(type: 'interrupt', interrupt: AudioInterrupt, callback: Callback<InterruptAction>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'interrupt' | 是 | 事件回调类型，支持的事件为'interrupt'，当音频焦点状态发生变化时，触发该事件。 |
| interrupt | [AudioInterrupt](arkts-audio-audio-audiointerrupt-i.md) | 是 | 音频打断事件类型的参数。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;InterruptAction&gt; | 是 | 回调函数，返回打断事件信息。 |

<a id="setaudioparameter"></a>
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

<!--Device-AudioManager-setAudioParameter(key: string, value: string, callback: AsyncCallback<void>): void--><!--Device-AudioManager-setAudioParameter(key: string, value: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 被设置的音频参数的键。 |
| value | string | 是 | 被设置的音频参数的值。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当音频参数设置成功，err为undefined，否则为错误对象。 |

<a id="setaudioparameter-1"></a>
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

<!--Device-AudioManager-setAudioParameter(key: string, value: string): Promise<void>--><!--Device-AudioManager-setAudioParameter(key: string, value: string): Promise<void>-End-->

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

<a id="setdeviceactive"></a>
## setDeviceActive

```TypeScript
setDeviceActive(deviceType: ActiveDeviceType, active: boolean, callback: AsyncCallback<void>): void
```

设置设备激活状态。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setCommunicationDevice

<!--Device-AudioManager-setDeviceActive(deviceType: ActiveDeviceType, active: boolean, callback: AsyncCallback<void>): void--><!--Device-AudioManager-setDeviceActive(deviceType: ActiveDeviceType, active: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | [ActiveDeviceType](arkts-audio-audio-activedevicetype-e.md) | 是 | 活跃音频设备类型。 |
| active | boolean | 是 | 是否设置设备为激活状态。true表示已激活，false表示未激活。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置设备激活状态成功，err为undefined，否则为错误对象。 |

<a id="setdeviceactive-1"></a>
## setDeviceActive

```TypeScript
setDeviceActive(deviceType: ActiveDeviceType, active: boolean): Promise<void>
```

设置设备激活状态。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setCommunicationDevice

<!--Device-AudioManager-setDeviceActive(deviceType: ActiveDeviceType, active: boolean): Promise<void>--><!--Device-AudioManager-setDeviceActive(deviceType: ActiveDeviceType, active: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | [ActiveDeviceType](arkts-audio-audio-activedevicetype-e.md) | 是 | 活跃音频设备类型。 |
| active | boolean | 是 | 是否设置设备为激活状态。true表示已激活，false表示未激活。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

<a id="setmicrophonemute"></a>
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

<!--Device-AudioManager-setMicrophoneMute(mute: boolean, callback: AsyncCallback<void>): void--><!--Device-AudioManager-setMicrophoneMute(mute: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | 是否设置麦克风为静音状态。true表示静音，false表示非静音。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置麦克风静音状态成功，err为undefined，否则为错误对象。 |

<a id="setmicrophonemute-1"></a>
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

<!--Device-AudioManager-setMicrophoneMute(mute: boolean): Promise<void>--><!--Device-AudioManager-setMicrophoneMute(mute: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | 是否设置麦克风为静音状态。true表示静音，false表示非静音。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

<a id="setringermode"></a>
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

<!--Device-AudioManager-setRingerMode(mode: AudioRingMode, callback: AsyncCallback<void>): void--><!--Device-AudioManager-setRingerMode(mode: AudioRingMode, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AudioRingMode](arkts-audio-audio-audioringmode-e.md) | 是 | 音频铃声模式。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置铃声模式成功，err为undefined，否则为错误对象。 |

<a id="setringermode-1"></a>
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

<!--Device-AudioManager-setRingerMode(mode: AudioRingMode): Promise<void>--><!--Device-AudioManager-setRingerMode(mode: AudioRingMode): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AudioRingMode](arkts-audio-audio-audioringmode-e.md) | 是 | 音频铃声模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

<a id="setvolume"></a>
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

<!--Device-AudioManager-setVolume(volumeType: AudioVolumeType, volume: number, callback: AsyncCallback<void>): void--><!--Device-AudioManager-setVolume(volumeType: AudioVolumeType, volume: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| volume | number | 是 | 音量等级，可设置范围通过[getMinVolume](arkts-audio-audio-audiomanager-i.md#getminvolume-1)和[getMaxVolume](arkts-audio-audio-audiomanager-i.md#getmaxvolume-1)获取。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置指定流的音量成功，err为undefined，否则为错误对象。 |

<a id="setvolume-1"></a>
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

<!--Device-AudioManager-setVolume(volumeType: AudioVolumeType, volume: number): Promise<void>--><!--Device-AudioManager-setVolume(volumeType: AudioVolumeType, volume: number): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 是 | 音频音量类型。 |
| volume | number | 是 | 音量等级，可设置范围通过[getMinVolume](arkts-audio-audio-audiomanager-i.md#getminvolume-1)和[getMaxVolume](arkts-audio-audio-audiomanager-i.md#getmaxvolume-1)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

