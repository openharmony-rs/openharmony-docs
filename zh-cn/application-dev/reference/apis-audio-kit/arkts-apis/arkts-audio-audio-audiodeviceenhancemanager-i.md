# AudioDeviceEnhanceManager

提供增强的音频设备管理能力。

**起始版本：** 26.0.0

<!--Device-audio-interface AudioDeviceEnhanceManager--><!--Device-audio-interface AudioDeviceEnhanceManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.DeviceEnhance

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

<a id="isenhancedroutingsupported"></a>
## isEnhancedRoutingSupported

```TypeScript
isEnhancedRoutingSupported(): boolean
```

查询系统是否支持该管理器提供的增强路由功能。包括为应用程序或音频流选择输入和输出设备。建议您的应用在使用前先调用此API确认系统支持这些增强的路由API。即使对于相同类型的主机设备，某些型号也可能支持这些功能，而其他功能由于硬件限制可能不具备。如果系统不支持这些增强的路由功能，调用它们将不起作用，系统将选择应用程序或音频流的默认输入/输出设备。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioDeviceEnhanceManager-isEnhancedRoutingSupported(): boolean--><!--Device-AudioDeviceEnhanceManager-isEnhancedRoutingSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.DeviceEnhance

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | The value true indicates that the system supports enhanced routing functions. |

<a id="selectinputdevice"></a>
## selectInputDevice

```TypeScript
selectInputDevice(inputDevice: AudioDeviceDescriptor): Promise<void>
```

为您的应用程序选择输入设备。此设置适用于创建的所有录制流在您的应用程序下，除非为特定流指定了特定输入设备{@link AudioDeviceEnhanceManager.selectInputDeviceForAudioCapturer}.当应用程序实现它自己的UX用于输入设备选择，它可以通过{@link AudioRoutingManager.get AvailableDevices}，并使用{@link AudioRoutingManager.getPreferredInputDeviceForCapturerInfo}接口获取当前选择的输入设备。当您的应用程序退出或选择的设备下线。在您的应用程序重新启动或设备重新联机后，您的应用程序必须重新发布选择才能使其生效。如果系统不支持该功能，它将为您的应用程序选择一个默认的输入设备。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioDeviceEnhanceManager-selectInputDevice(inputDevice: AudioDeviceDescriptor): Promise<void>--><!--Device-AudioDeviceEnhanceManager-selectInputDevice(inputDevice: AudioDeviceDescriptor): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.DeviceEnhance

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | {@link AudioRoutingManager.get AvailableDevices}接口返回的音频设备描述数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed, for example,the selected device does not exist. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio service error occurs, such as the service died. |

<a id="selectinputdeviceforaudiocapturer"></a>
## selectInputDeviceForAudioCapturer

```TypeScript
selectInputDeviceForAudioCapturer(capturer: AudioCapturer, inputDevice: AudioDeviceDescriptor): Promise<void>
```

选择目标AudioCapturer的输入设备。您的应用程序必须确保指定的AudioCapturer是有效的。此选择仅适用于指定流；其他录制流您的应用程序将使用您的应用程序的强制选择或系统的默认输入设备。当您的应用程序退出或所选设备脱机时，选择将变为无效。应用程序重新启动或设备重新联机后，您的应用程序必须重新发出选择使其生效。如果系统不支持该功能，系统将选择捕获器的默认输入设备。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioDeviceEnhanceManager-selectInputDeviceForAudioCapturer(capturer: AudioCapturer, inputDevice: AudioDeviceDescriptor): Promise<void>--><!--Device-AudioDeviceEnhanceManager-selectInputDeviceForAudioCapturer(capturer: AudioCapturer, inputDevice: AudioDeviceDescriptor): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.DeviceEnhance

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capturer | [AudioCapturer](arkts-audio-audio-audiocapturer-i.md) | 是 | AudioCapturer的实例。 |
| inputDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | {@link AudioRoutingManager.get AvailableDevices}接口返回的音频设备描述数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed, for example,the selected device does not exist. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio service error occurs, such as the service died. |

<a id="selectoutputdevice"></a>
## selectOutputDevice

```TypeScript
selectOutputDevice(outputDevice: AudioDeviceDescriptor): Promise<void>
```

选择应用程序的输出设备。此设置适用于创建的所有播放流除非为特定流指定了特定的输出设备{@link AudioDeviceEnhanceManager.selectOutputDeviceForAudioRenderer}.当应用程序实现它自己的UX用于输出设备选择，它可以通过{@link AudioRoutingManager.get AvailableDevices}，并使用{@link AudioRoutingManager.getPreferOutputDeviceForRendererInfo}接口获取当前选定的输出设备。当您的应用程序退出或选择的设备下线。在您的应用程序重新启动或设备重新联机后，您的应用程序必须重新发布选择才能使其生效。如果系统不支持该功能，则会为您的应用程序选择一个默认的输出设备。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioDeviceEnhanceManager-selectOutputDevice(outputDevice: AudioDeviceDescriptor): Promise<void>--><!--Device-AudioDeviceEnhanceManager-selectOutputDevice(outputDevice: AudioDeviceDescriptor): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.DeviceEnhance

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| outputDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 通过{@link AudioRoutingManager.getAvailableDevices}接口返回的音频设备描述数组 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed, for example,the selected device does not exist. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio service error occurs, such as the service died. |

<a id="selectoutputdeviceforaudiorenderer"></a>
## selectOutputDeviceForAudioRenderer

```TypeScript
selectOutputDeviceForAudioRenderer(renderer: AudioRenderer, outputDevice: AudioDeviceDescriptor): Promise<void>
```

选择目标AudioRenderer的输出设备。您的应用程序必须确保指定的AudioRenderer是有效的。此选择仅适用于指定流；其他播放流您的应用程序将使用您的应用程序的强制选择或系统的默认输出设备。当您的应用程序退出或所选设备脱机时，选择将变为无效。应用程序重新启动或设备重新联机后，您的应用程序必须重新发出选择使其生效。如果系统不支持该功能，系统将选择渲染器的默认输出设备。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioDeviceEnhanceManager-selectOutputDeviceForAudioRenderer(renderer: AudioRenderer, outputDevice: AudioDeviceDescriptor): Promise<void>--><!--Device-AudioDeviceEnhanceManager-selectOutputDeviceForAudioRenderer(renderer: AudioRenderer, outputDevice: AudioDeviceDescriptor): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.DeviceEnhance

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| renderer | [AudioRenderer](arkts-audio-audio-audiorenderer-i.md) | 是 | AudioRenderer的实例。 |
| outputDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | {@link AudioRoutingManager.get AvailableDevices}接口返回的音频设备描述数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed, for example,the selected device does not exist. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio service error occurs, such as the service died. |

