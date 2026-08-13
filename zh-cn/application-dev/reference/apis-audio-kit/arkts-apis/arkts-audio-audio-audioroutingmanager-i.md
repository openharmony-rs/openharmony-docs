# AudioRoutingManager

音频路由管理。 在使用AudioRoutingManager的接口之前，需先通过[getRoutingManager](arkts-audio-audio-audiomanager-i.md#getRoutingManager)获取 AudioRoutingManager实例。 > **说明：** > > - 本Interface首批接口从API version 9开始支持。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-audio-interface AudioRoutingManager--><!--Device-audio-interface AudioRoutingManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## declareDeviceTypesCompatibility

```TypeScript
declareDeviceTypesCompatibility(deviceTypes: DeviceTypeArray): void
```

声明应用需要兼容的设备类型。 > **说明：** > > 对于API version 20及以上版本新增的设备类型，应用调用获取设备的相关接口时（例如 > [getAvailableDevices](arkts-audio-audio-audiosessionmanager-i.md#getAvailableDevices)），默认返回的设备类型为匿名类型。如需获取具体设备类型，需先调用该方法进行 > 设备类型兼容声明。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioRoutingManager-declareDeviceTypesCompatibility(deviceTypes: DeviceTypeArray): void--><!--Device-AudioRoutingManager-declareDeviceTypesCompatibility(deviceTypes: DeviceTypeArray): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceTypes | [DeviceTypeArray](arkts-audio-audio-devicetypearray-t.md) | 是 | [DeviceType](arkts-audio-audio-devicetype-e.md#DeviceType)数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed, the param deviceTypes contains value that is invalid enum or is not a device type introduced in API 20 onwards. |

## getAvailableDevices

```TypeScript
getAvailableDevices(deviceUsage: DeviceUsage): AudioDeviceDescriptors
```

获取音频可选设备列表。同步返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-getAvailableDevices(deviceUsage: DeviceUsage): AudioDeviceDescriptors--><!--Device-AudioRoutingManager-getAvailableDevices(deviceUsage: DeviceUsage): AudioDeviceDescriptors-End-->

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## getDevices

```TypeScript
getDevices(deviceFlag: DeviceFlag, callback: AsyncCallback<AudioDeviceDescriptors>): void
```

获取音频设备列表。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-getDevices(deviceFlag: DeviceFlag, callback: AsyncCallback<AudioDeviceDescriptors>): void--><!--Device-AudioRoutingManager-getDevices(deviceFlag: DeviceFlag, callback: AsyncCallback<AudioDeviceDescriptors>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceFlag | DeviceFlag | 是 | 音频设备类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | 是 | 回调函数。当获取音频设备列表成功，err为undefined，data为获取到的音频设备列表；否则为错误对 象。 |

## getDevices

```TypeScript
getDevices(deviceFlag: DeviceFlag): Promise<AudioDeviceDescriptors>
```

获取音频设备列表。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-getDevices(deviceFlag: DeviceFlag): Promise<AudioDeviceDescriptors>--><!--Device-AudioRoutingManager-getDevices(deviceFlag: DeviceFlag): Promise<AudioDeviceDescriptors>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceFlag | DeviceFlag | 是 | 音频设备类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | Promise对象，返回设备列表。 |

## getDevicesSync

```TypeScript
getDevicesSync(deviceFlag: DeviceFlag): AudioDeviceDescriptors
```

获取音频设备列表。同步返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-getDevicesSync(deviceFlag: DeviceFlag): AudioDeviceDescriptors--><!--Device-AudioRoutingManager-getDevicesSync(deviceFlag: DeviceFlag): AudioDeviceDescriptors-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceFlag | DeviceFlag | 是 | 音频设备类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | 返回设备列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## getPreferOutputDeviceForRendererInfo

```TypeScript
getPreferOutputDeviceForRendererInfo(rendererInfo: AudioRendererInfo, callback: AsyncCallback<AudioDeviceDescriptors>): void
```

根据音频信息，返回优先级最高的输出设备。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-getPreferOutputDeviceForRendererInfo(rendererInfo: AudioRendererInfo, callback: AsyncCallback<AudioDeviceDescriptors>): void--><!--Device-AudioRoutingManager-getPreferOutputDeviceForRendererInfo(rendererInfo: AudioRendererInfo, callback: AsyncCallback<AudioDeviceDescriptors>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rendererInfo | [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md) | 是 | 音频渲染器信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | 是 | 回调函数。当获取优先级最高的输出设备成功，err为undefined，data为获取到的优先级最高的输出设 备信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by callback. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Return by callback. |

## getPreferOutputDeviceForRendererInfo

```TypeScript
getPreferOutputDeviceForRendererInfo(rendererInfo: AudioRendererInfo): Promise<AudioDeviceDescriptors>
```

根据音频信息，返回优先级最高的输出设备。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-getPreferOutputDeviceForRendererInfo(rendererInfo: AudioRendererInfo): Promise<AudioDeviceDescriptors>--><!--Device-AudioRoutingManager-getPreferOutputDeviceForRendererInfo(rendererInfo: AudioRendererInfo): Promise<AudioDeviceDescriptors>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rendererInfo | [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md) | 是 | 音频渲染器信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | Promise对象，返回优先级最高的输出设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by promise. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Return by promise. |

## getPreferredInputDeviceForCapturerInfo

```TypeScript
getPreferredInputDeviceForCapturerInfo(capturerInfo: AudioCapturerInfo, callback: AsyncCallback<AudioDeviceDescriptors>): void
```

根据音频信息，返回优先级最高的输入设备。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-getPreferredInputDeviceForCapturerInfo(capturerInfo: AudioCapturerInfo, callback: AsyncCallback<AudioDeviceDescriptors>): void--><!--Device-AudioRoutingManager-getPreferredInputDeviceForCapturerInfo(capturerInfo: AudioCapturerInfo, callback: AsyncCallback<AudioDeviceDescriptors>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capturerInfo | [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md) | 是 | 音频采集器信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | 是 | 回调函数。当获取优先级最高的输入设备成功，err为undefined，data为获取到的优先级最高的输入设 备信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by callback. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Return by callback. |

## getPreferredInputDeviceForCapturerInfo

```TypeScript
getPreferredInputDeviceForCapturerInfo(capturerInfo: AudioCapturerInfo): Promise<AudioDeviceDescriptors>
```

根据音频信息，返回优先级最高的输入设备。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-getPreferredInputDeviceForCapturerInfo(capturerInfo: AudioCapturerInfo): Promise<AudioDeviceDescriptors>--><!--Device-AudioRoutingManager-getPreferredInputDeviceForCapturerInfo(capturerInfo: AudioCapturerInfo): Promise<AudioDeviceDescriptors>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capturerInfo | [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md) | 是 | 音频采集器信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | Promise对象，返回优先级最高的输入设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Return by promise. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. Return by promise. |

## getPreferredInputDeviceForCapturerInfoSync

```TypeScript
getPreferredInputDeviceForCapturerInfoSync(capturerInfo: AudioCapturerInfo): AudioDeviceDescriptors
```

根据音频信息，返回优先级最高的输入设备。同步返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-getPreferredInputDeviceForCapturerInfoSync(capturerInfo: AudioCapturerInfo): AudioDeviceDescriptors--><!--Device-AudioRoutingManager-getPreferredInputDeviceForCapturerInfoSync(capturerInfo: AudioCapturerInfo): AudioDeviceDescriptors-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capturerInfo | [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md) | 是 | 音频采集器信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | 返回优先级最高的输入设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## getPreferredOutputDeviceForRendererInfoSync

```TypeScript
getPreferredOutputDeviceForRendererInfoSync(rendererInfo: AudioRendererInfo): AudioDeviceDescriptors
```

根据音频信息，返回优先级最高的输出设备。同步返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-getPreferredOutputDeviceForRendererInfoSync(rendererInfo: AudioRendererInfo): AudioDeviceDescriptors--><!--Device-AudioRoutingManager-getPreferredOutputDeviceForRendererInfoSync(rendererInfo: AudioRendererInfo): AudioDeviceDescriptors-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rendererInfo | [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md) | 是 | 音频渲染器信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | 返回优先级最高的输出设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## isCommunicationDeviceActive

```TypeScript
isCommunicationDeviceActive(deviceType: CommunicationDeviceType, callback: AsyncCallback<boolean>): void
```

获取指定通信设备的激活状态。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-isCommunicationDeviceActive(deviceType: CommunicationDeviceType, callback: AsyncCallback<boolean>): void--><!--Device-AudioRoutingManager-isCommunicationDeviceActive(deviceType: CommunicationDeviceType, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | [CommunicationDeviceType](arkts-audio-audio-communicationdevicetype-e.md) | 是 | 活跃音频设备类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。当获取指定通信设备的激活状态成功，err为undefined，data为true表示激活，false表示未激活；否则为错误对 象。 |

## isCommunicationDeviceActive

```TypeScript
isCommunicationDeviceActive(deviceType: CommunicationDeviceType): Promise<boolean>
```

获取指定通信设备的激活状态。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-isCommunicationDeviceActive(deviceType: CommunicationDeviceType): Promise<boolean>--><!--Device-AudioRoutingManager-isCommunicationDeviceActive(deviceType: CommunicationDeviceType): Promise<boolean>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | [CommunicationDeviceType](arkts-audio-audio-communicationdevicetype-e.md) | 是 | 活跃音频设备类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示设备已激活；返回false表示设备未激活。 |

## isCommunicationDeviceActiveSync

```TypeScript
isCommunicationDeviceActiveSync(deviceType: CommunicationDeviceType): boolean
```

获取指定通信设备的激活状态。同步返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-isCommunicationDeviceActiveSync(deviceType: CommunicationDeviceType): boolean--><!--Device-AudioRoutingManager-isCommunicationDeviceActiveSync(deviceType: CommunicationDeviceType): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | [CommunicationDeviceType](arkts-audio-audio-communicationdevicetype-e.md) | 是 | 活跃音频设备类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 设备是否处于激活状态。true表示处于激活状态，false表示处于未激活状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## isMicBlockDetectionSupported

```TypeScript
isMicBlockDetectionSupported():Promise<boolean>
```

获取当前设备是否支持麦克风状态检测。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-isMicBlockDetectionSupported():Promise<boolean>--><!--Device-AudioRoutingManager-isMicBlockDetectionSupported():Promise<boolean>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示支持；返回false表示不支持。 |

## offAvailableDeviceChange

```TypeScript
offAvailableDeviceChange(callback?: Callback<DeviceChangeAction>): void
```

Unsubscribes to available device change events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-offAvailableDeviceChange(callback?: Callback<DeviceChangeAction>): void--><!--Device-AudioRoutingManager-offAvailableDeviceChange(callback?: Callback<DeviceChangeAction>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DeviceChangeAction](arkts-audio-audio-devicechangeaction-i.md)&gt; | 否 | Callback used to obtain the device update details. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## offDeviceChange

```TypeScript
offDeviceChange(callback?: Callback<DeviceChangeAction>): void
```

UnSubscribes to device change events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-offDeviceChange(callback?: Callback<DeviceChangeAction>): void--><!--Device-AudioRoutingManager-offDeviceChange(callback?: Callback<DeviceChangeAction>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DeviceChangeAction](arkts-audio-audio-devicechangeaction-i.md)&gt; | 否 | Callback used to obtain the device update details. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## offMicBlockStatusChanged

```TypeScript
offMicBlockStatusChanged(callback?: Callback<DeviceBlockStatusInfo>): void
```

Unsubscribes microphone blocked events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-offMicBlockStatusChanged(callback?: Callback<DeviceBlockStatusInfo>): void--><!--Device-AudioRoutingManager-offMicBlockStatusChanged(callback?: Callback<DeviceBlockStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DeviceBlockStatusInfo](arkts-audio-audio-deviceblockstatusinfo-i.md)&gt; | 否 | Callback used to obtain the microphone block status. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## offPreferOutputDeviceChangeForRendererInfo

```TypeScript
offPreferOutputDeviceChangeForRendererInfo(callback?: Callback<AudioDeviceDescriptors>): void
```

Unsubscribes to prefer output device change events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-offPreferOutputDeviceChangeForRendererInfo(callback?: Callback<AudioDeviceDescriptors>): void--><!--Device-AudioRoutingManager-offPreferOutputDeviceChangeForRendererInfo(callback?: Callback<AudioDeviceDescriptors>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | 否 | Callback used to obtain the changed prefer devices in subscribe. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## offPreferredInputDeviceChangeForCapturerInfo

```TypeScript
offPreferredInputDeviceChangeForCapturerInfo(callback?: Callback<AudioDeviceDescriptors>): void
```

Unsubscribes to preferred input device change events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-offPreferredInputDeviceChangeForCapturerInfo(callback?: Callback<AudioDeviceDescriptors>): void--><!--Device-AudioRoutingManager-offPreferredInputDeviceChangeForCapturerInfo(callback?: Callback<AudioDeviceDescriptors>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | 否 | Callback used to obtain the changed preferred devices in subscribe. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off_availableDeviceChange

```TypeScript
off(type: 'availableDeviceChange', callback?: Callback<DeviceChangeAction>): void
```

取消监听音频可选设备连接状态变化事件。使用callback异步回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-AudioRoutingManager-off(type: 'availableDeviceChange', callback?: Callback<DeviceChangeAction>): void--><!--Device-AudioRoutingManager-off(type: 'availableDeviceChange', callback?: Callback<DeviceChangeAction>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'availableDeviceChange' | 是 | 事件回调类型，支持的事件为'availableDeviceChange'，当取消监听音频可选设备连接变化事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DeviceChangeAction](arkts-audio-audio-devicechangeaction-i.md)&gt; | 否 | 回调函数，返回可选设备更新详情。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off_deviceChange

```TypeScript
off(type: 'deviceChange', callback?: Callback<DeviceChangeAction>): void
```

取消监听音频设备连接状态变化事件。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-AudioRoutingManager-off(type: 'deviceChange', callback?: Callback<DeviceChangeAction>): void--><!--Device-AudioRoutingManager-off(type: 'deviceChange', callback?: Callback<DeviceChangeAction>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceChange' | 是 | 事件回调类型，支持的事件为'deviceChange'，当取消监听音频设备连接变化事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DeviceChangeAction](arkts-audio-audio-devicechangeaction-i.md)&gt; | 否 | 回调函数，返回设备更新详情。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off_micBlockStatusChanged

```TypeScript
off(type: 'micBlockStatusChanged', callback?: Callback<DeviceBlockStatusInfo>): void
```

取消监听麦克风堵塞状态变化事件。使用callback异步回调。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**废弃版本：** -1

<!--Device-AudioRoutingManager-off(type: 'micBlockStatusChanged', callback?: Callback<DeviceBlockStatusInfo>): void--><!--Device-AudioRoutingManager-off(type: 'micBlockStatusChanged', callback?: Callback<DeviceBlockStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'micBlockStatusChanged' | 是 | 事件回调类型，支持的事件为'micBlockStatusChanged'，当取消监听音频麦克风是否被堵塞变化事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DeviceBlockStatusInfo](arkts-audio-audio-deviceblockstatusinfo-i.md)&gt; | 否 | 回调函数，返回麦克风被堵塞状态和设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off_preferOutputDeviceChangeForRendererInfo

```TypeScript
off(type: 'preferOutputDeviceChangeForRendererInfo', callback?: Callback<AudioDeviceDescriptors>): void
```

取消监听最高优先级输出音频设备变化事件。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-AudioRoutingManager-off(type: 'preferOutputDeviceChangeForRendererInfo', callback?: Callback<AudioDeviceDescriptors>): void--><!--Device-AudioRoutingManager-off(type: 'preferOutputDeviceChangeForRendererInfo', callback?: Callback<AudioDeviceDescriptors>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'preferOutputDeviceChangeForRendererInfo' | 是 | 事件回调类型，支持的事件为'preferOutputDeviceChangeForRendererInfo '，当取消监听最高优先级输出音频设备变化事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | 否 | 回调函数，返回优先级最高的输出设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## off_preferredInputDeviceChangeForCapturerInfo

```TypeScript
off(type: 'preferredInputDeviceChangeForCapturerInfo', callback?: Callback<AudioDeviceDescriptors>): void
```

取消监听最高优先级输入音频设备变化事件。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-AudioRoutingManager-off(type: 'preferredInputDeviceChangeForCapturerInfo', callback?: Callback<AudioDeviceDescriptors>): void--><!--Device-AudioRoutingManager-off(type: 'preferredInputDeviceChangeForCapturerInfo', callback?: Callback<AudioDeviceDescriptors>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'preferredInputDeviceChangeForCapturerInfo' | 是 | 事件回调类型，支持的事件为' preferredInputDeviceChangeForCapturerInfo'，当取消监听最高优先级输入音频设备变化事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | 否 | 回调函数，返回优先级最高的输入设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## onAvailableDeviceChange

```TypeScript
onAvailableDeviceChange(deviceUsage: DeviceUsage, callback: Callback<DeviceChangeAction>): void
```

Subscribes to available device change events. When a device is connected/disconnected, registered clients will receive the callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-onAvailableDeviceChange(deviceUsage: DeviceUsage, callback: Callback<DeviceChangeAction>): void--><!--Device-AudioRoutingManager-onAvailableDeviceChange(deviceUsage: DeviceUsage, callback: Callback<DeviceChangeAction>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceUsage | [DeviceUsage](arkts-audio-audio-deviceusage-e.md) | 是 | Audio device usage. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DeviceChangeAction](arkts-audio-audio-devicechangeaction-i.md)&gt; | 是 | Callback used to obtain the device update details. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## onDeviceChange

```TypeScript
onDeviceChange(deviceFlag: DeviceFlag, callback: Callback<DeviceChangeAction>): void
```

Subscribes to device change events. When a device is connected/disconnected, registered clients will receive the callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-onDeviceChange(deviceFlag: DeviceFlag, callback: Callback<DeviceChangeAction>): void--><!--Device-AudioRoutingManager-onDeviceChange(deviceFlag: DeviceFlag, callback: Callback<DeviceChangeAction>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceFlag | DeviceFlag | 是 | Audio device flag. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DeviceChangeAction](arkts-audio-audio-devicechangeaction-i.md)&gt; | 是 | Callback used to obtain the device update details. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## onMicBlockStatusChanged

```TypeScript
onMicBlockStatusChanged(callback: Callback<DeviceBlockStatusInfo>): void
```

Subscribes microphone blocked events. Before subscribing, users should query whether block detection is supported on current device. The caller will receive the callback only when it is recording and the used microphones' block status have changed. Currently, block detecting is only support for microphones located on the local device.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-onMicBlockStatusChanged(callback: Callback<DeviceBlockStatusInfo>): void--><!--Device-AudioRoutingManager-onMicBlockStatusChanged(callback: Callback<DeviceBlockStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DeviceBlockStatusInfo](arkts-audio-audio-deviceblockstatusinfo-i.md)&gt; | 是 | Callback used to obtain the microphone block status. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## onPreferOutputDeviceChangeForRendererInfo

```TypeScript
onPreferOutputDeviceChangeForRendererInfo(rendererInfo: AudioRendererInfo, callback: Callback<AudioDeviceDescriptors>): void
```

Subscribes to prefer output device change events. When prefer device for target audio renderer info changes, registered clients will receive the callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-onPreferOutputDeviceChangeForRendererInfo(rendererInfo: AudioRendererInfo, callback: Callback<AudioDeviceDescriptors>): void--><!--Device-AudioRoutingManager-onPreferOutputDeviceChangeForRendererInfo(rendererInfo: AudioRendererInfo, callback: Callback<AudioDeviceDescriptors>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rendererInfo | [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md) | 是 | Audio renderer information. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | 是 | Callback used to obtain the changed prefer devices information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## onPreferredInputDeviceChangeForCapturerInfo

```TypeScript
onPreferredInputDeviceChangeForCapturerInfo(capturerInfo: AudioCapturerInfo, callback: Callback<AudioDeviceDescriptors>): void
```

Subscribes to preferred input device change events. When preferred device for target audio capturer info changes, registered clients will receive the callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-onPreferredInputDeviceChangeForCapturerInfo(capturerInfo: AudioCapturerInfo, callback: Callback<AudioDeviceDescriptors>): void--><!--Device-AudioRoutingManager-onPreferredInputDeviceChangeForCapturerInfo(capturerInfo: AudioCapturerInfo, callback: Callback<AudioDeviceDescriptors>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capturerInfo | [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md) | 是 | Audio capturer information. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | 是 | Callback used to obtain the changed preferred devices information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on_availableDeviceChange

```TypeScript
on(type: 'availableDeviceChange', deviceUsage: DeviceUsage, callback: Callback<DeviceChangeAction>): void
```

监听音频可选设备连接状态变化事件（当音频可选设备连接状态发生变化时触发）。使用callback异步回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-AudioRoutingManager-on(type: 'availableDeviceChange', deviceUsage: DeviceUsage, callback: Callback<DeviceChangeAction>): void--><!--Device-AudioRoutingManager-on(type: 'availableDeviceChange', deviceUsage: DeviceUsage, callback: Callback<DeviceChangeAction>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'availableDeviceChange' | 是 | 事件回调类型，支持的事件为'availableDeviceChange'，当音频可选设备连接状态发生变化时，触发该事件。 |
| deviceUsage | [DeviceUsage](arkts-audio-audio-deviceusage-e.md) | 是 | 音频设备类型（根据用途分类）。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DeviceChangeAction](arkts-audio-audio-devicechangeaction-i.md)&gt; | 是 | 回调函数，返回设备更新详情。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on_deviceChange

```TypeScript
on(type: 'deviceChange', deviceFlag: DeviceFlag, callback: Callback<DeviceChangeAction>): void
```

监听音频设备连接状态变化事件（当音频设备连接状态发生变化时触发）。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-AudioRoutingManager-on(type: 'deviceChange', deviceFlag: DeviceFlag, callback: Callback<DeviceChangeAction>): void--><!--Device-AudioRoutingManager-on(type: 'deviceChange', deviceFlag: DeviceFlag, callback: Callback<DeviceChangeAction>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceChange' | 是 | 事件回调类型，支持的事件为'deviceChange'，当音频设备连接状态发生变化时，触发该事件。 |
| deviceFlag | DeviceFlag | 是 | 音频设备类型。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DeviceChangeAction](arkts-audio-audio-devicechangeaction-i.md)&gt; | 是 | 回调函数，返回设备更新详情。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on_micBlockStatusChanged

```TypeScript
on(type: 'micBlockStatusChanged', callback: Callback<DeviceBlockStatusInfo>): void
```

监听麦克风堵塞状态变化事件。使用callback异步回调。 使用此功能前，请使用[isMicBlockDetectionSupported](#isMicBlockDetectionSupported)查询设备是否支持检测。 应用在使用麦克风录音时，若麦克风堵塞状态发生变化，将触发该事件。目前此检测功能仅支持麦克风位于本地设备上。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**废弃版本：** -1

<!--Device-AudioRoutingManager-on(type: 'micBlockStatusChanged', callback: Callback<DeviceBlockStatusInfo>): void--><!--Device-AudioRoutingManager-on(type: 'micBlockStatusChanged', callback: Callback<DeviceBlockStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'micBlockStatusChanged' | 是 | 事件回调类型，支持的事件为'micBlockStatusChanged'，当麦克风堵塞状态发生变化时，触发该事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DeviceBlockStatusInfo](arkts-audio-audio-deviceblockstatusinfo-i.md)&gt; | 是 | 回调函数，返回麦克风被堵塞状态和设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on_preferOutputDeviceChangeForRendererInfo

```TypeScript
on(type: 'preferOutputDeviceChangeForRendererInfo', rendererInfo: AudioRendererInfo, callback: Callback<AudioDeviceDescriptors>): void
```

监听最高优先级输出设备变化事件（当最高优先级输出设备发生变化时触发）。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-AudioRoutingManager-on(type: 'preferOutputDeviceChangeForRendererInfo', rendererInfo: AudioRendererInfo, callback: Callback<AudioDeviceDescriptors>): void--><!--Device-AudioRoutingManager-on(type: 'preferOutputDeviceChangeForRendererInfo', rendererInfo: AudioRendererInfo, callback: Callback<AudioDeviceDescriptors>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'preferOutputDeviceChangeForRendererInfo' | 是 | 事件回调类型，支持的事件为'preferOutputDeviceChangeForRendererInfo '，当最高优先级输出设备发生变化时，触发该事件。 |
| rendererInfo | [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md) | 是 | 音频渲染器信息。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | 是 | 回调函数，返回优先级最高的输出设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on_preferredInputDeviceChangeForCapturerInfo

```TypeScript
on(type: 'preferredInputDeviceChangeForCapturerInfo', capturerInfo: AudioCapturerInfo, callback: Callback<AudioDeviceDescriptors>): void
```

监听最高优先级输入设备变化事件（当最高优先级输入设备发生变化时触发）。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-AudioRoutingManager-on(type: 'preferredInputDeviceChangeForCapturerInfo', capturerInfo: AudioCapturerInfo, callback: Callback<AudioDeviceDescriptors>): void--><!--Device-AudioRoutingManager-on(type: 'preferredInputDeviceChangeForCapturerInfo', capturerInfo: AudioCapturerInfo, callback: Callback<AudioDeviceDescriptors>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'preferredInputDeviceChangeForCapturerInfo' | 是 | 事件回调类型，支持的事件为' preferredInputDeviceChangeForCapturerInfo'，当最高优先级输入设备发生变化时，触发该事件。 |
| capturerInfo | [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md) | 是 | 音频采集器信息。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | 是 | 回调函数，返回优先级最高的输入设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## setCommunicationDevice

```TypeScript
setCommunicationDevice(deviceType: CommunicationDeviceType, active: boolean, callback: AsyncCallback<void>): void
```

设置通信设备激活状态。使用callback异步回调。 该接口由于功能设计变化，将在后续版本废弃，不建议开发者使用。 推荐使用AVSession提供的[设备切换组件](../../../media/avsession/using-switch-call-devices.md)，实现通话设备切换。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-setCommunicationDevice(deviceType: CommunicationDeviceType, active: boolean, callback: AsyncCallback<void>): void--><!--Device-AudioRoutingManager-setCommunicationDevice(deviceType: CommunicationDeviceType, active: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | [CommunicationDeviceType](arkts-audio-audio-communicationdevicetype-e.md) | 是 | 音频设备类型。 |
| active | boolean | 是 | 是否设置设备为激活状态。true表示激活，false表示未激活。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当设置通信设备激活状态成功，err为undefined，否则为错误对象。 |

## setCommunicationDevice

```TypeScript
setCommunicationDevice(deviceType: CommunicationDeviceType, active: boolean): Promise<void>
```

设置通信设备激活状态。使用Promise异步回调。 该接口由于功能设计变化，将在后续版本废弃，不建议开发者使用。 推荐开发者使用AVSession提供的[设备切换组件](../../../media/avsession/using-switch-call-devices.md)，实现通话设备切换。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AudioRoutingManager-setCommunicationDevice(deviceType: CommunicationDeviceType, active: boolean): Promise<void>--><!--Device-AudioRoutingManager-setCommunicationDevice(deviceType: CommunicationDeviceType, active: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | [CommunicationDeviceType](arkts-audio-audio-communicationdevicetype-e.md) | 是 | 活跃音频设备类型。 |
| active | boolean | 是 | 是否设置设备为激活状态。true表示激活，false表示未激活。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

