# AudioDeviceEnhanceManager

```TypeScript
interface AudioDeviceEnhanceManager
```

Provides enhanced audio device management capabilities.

**Since:** 26.0.0

<!--Device-audio-interface AudioDeviceEnhanceManager--><!--Device-audio-interface AudioDeviceEnhanceManager-End-->

**System capability:** SystemCapability.Multimedia.Audio.DeviceEnhance

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getSoundCardInfoList

```TypeScript
getSoundCardInfoList(): Promise<Array<SoundCardInfo>>
```

This interface is used to obtain the audio card information list, including the onboard audio card and USB audio card. Use the Promise asynchronous callback to return the query results. Application scenario: The application needs to obtain information about all audio adapters on the device, including onboard audio adapters and USB audio adapters, for asset management and monitoring.

Restriction:  
- The application must apply for the ohos.permission.GET_AUDIO_ADAPTER_INFO permission.  
- This interface supports only PC devices. When a non-PC device invokes this interface, error code 801 is  
returned.

**Since:** 26.2.0

**Required permissions:** ohos.permission.GET_AUDIO_ADAPTER_INFO

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioDeviceEnhanceManager-getSoundCardInfoList(): Promise<Array<SoundCardInfo>>--><!--Device-AudioDeviceEnhanceManager-getSoundCardInfoList(): Promise<Array<SoundCardInfo>>-End-->

**System capability:** SystemCapability.Multimedia.Audio.DeviceEnhance

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[SoundCardInfo](arkts-audio-audio-soundcardinfo-i-sys.md)&gt;&gt; | Promise used to return the sound card information list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | The current device model does not support this function. |

## isEnhancedRoutingSupported

```TypeScript
isEnhancedRoutingSupported(): boolean
```

Queries whether the system supports the enhanced routing functions provided by this manager, including selecting input and output devices for the application or audio streams. Your application is advised to call this API first to confirm system support before using these enhanced routing APIs. Even for the same type of host device, some models may support these functions while others may not due to hardware limitations. If the system does not support these enhanced routing functions, calling them will have no effect, and the system will select default input/output devices for the application or audio streams instead.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioDeviceEnhanceManager-isEnhancedRoutingSupported(): boolean--><!--Device-AudioDeviceEnhanceManager-isEnhancedRoutingSupported(): boolean-End-->

**System capability:** SystemCapability.Multimedia.Audio.DeviceEnhance

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The value true indicates that the system supports enhanced routing functions. |

## selectInputDevice

```TypeScript
selectInputDevice(inputDevice: AudioDeviceDescriptor): Promise<void>
```

Selects the input device for your application. This setting applies to all recording streams created under your application, unless a specific input device is designated for a particular stream by [selectInputDeviceForAudioCapturer](#selectinputdeviceforaudiocapturer). When application implements its own UX for input device selection, it can obtain the list of available input devices through [getAvailableDevices](arkts-audio-audio-audioroutingmanager-i.md#getavailabledevices), and use the [getPreferredInputDeviceForCapturerInfo](arkts-audio-audio-audioroutingmanager-i.md#getpreferredinputdeviceforcapturerinfo) API to obtain the currently selected input device. The selection will become invalid when your application exits or the selected device goes offline. After your application restarts or the device comes back online, your application must re-issue the selection for it to take effect. If the system does not support this function, it will select a default input device for your application.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioDeviceEnhanceManager-selectInputDevice(inputDevice: AudioDeviceDescriptor): Promise<void>--><!--Device-AudioDeviceEnhanceManager-selectInputDevice(inputDevice: AudioDeviceDescriptor): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Audio.DeviceEnhance

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | Audio device descriptor in the array returned by [getAvailableDevices](arkts-audio-audio-audioroutingmanager-i.md#getavailabledevices). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed, for example, the selected device does not exist. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio service error occurs, such as the service died. |

## selectInputDeviceForAudioCapturer

```TypeScript
selectInputDeviceForAudioCapturer(capturer: AudioCapturer, inputDevice: AudioDeviceDescriptor): Promise<void>
```

Selects the input device for the target AudioCapturer. Your application must ensure that the specified AudioCapturer is valid. This selection only applies to the designated stream; other recording streams in your application will use your application's forced selection or the system's default input device. The selection will become invalid when your application exits or the selected device goes offline. After your application restarts or the device comes back online, your application must re-issue the selection for it to take effect. If the system does not support this function, the system will select a default input device for the capturer.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioDeviceEnhanceManager-selectInputDeviceForAudioCapturer(capturer: AudioCapturer, inputDevice: AudioDeviceDescriptor): Promise<void>--><!--Device-AudioDeviceEnhanceManager-selectInputDeviceForAudioCapturer(capturer: AudioCapturer, inputDevice: AudioDeviceDescriptor): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Audio.DeviceEnhance

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| capturer | [AudioCapturer](arkts-audio-audio-audiocapturer-i.md) | Yes | The instance of AudioCapturer. |
| inputDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | Audio device descriptor in the array returned by [getAvailableDevices](arkts-audio-audio-audioroutingmanager-i.md#getavailabledevices). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed, for example, the selected device does not exist. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio service error occurs, such as the service died. |

## selectOutputDevice

```TypeScript
selectOutputDevice(outputDevice: AudioDeviceDescriptor): Promise<void>
```

Selects the output device for your application. This setting applies to all playback streams created under your application, unless a specific output device is designated for a particular stream by [selectOutputDeviceForAudioRenderer](#selectoutputdeviceforaudiorenderer). When application implements its own UX for output device selection, it can obtain the list of available output devices through [getAvailableDevices](arkts-audio-audio-audioroutingmanager-i.md#getavailabledevices), and use the [getPreferOutputDeviceForRendererInfo](arkts-audio-audio-audioroutingmanager-i.md#getpreferoutputdeviceforrendererinfo) API to obtain the currently selected output device. The selection will become invalid when your application exits or the selected device goes offline. After your application restarts or the device comes back online, your application must re-issue the selection for it to take effect. If the system does not support this function, it will select a default output device for your application.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioDeviceEnhanceManager-selectOutputDevice(outputDevice: AudioDeviceDescriptor): Promise<void>--><!--Device-AudioDeviceEnhanceManager-selectOutputDevice(outputDevice: AudioDeviceDescriptor): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Audio.DeviceEnhance

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| outputDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | Audio device descriptor in the array returned by [getAvailableDevices](arkts-audio-audio-audioroutingmanager-i.md#getavailabledevices). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed, for example, the selected device does not exist. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio service error occurs, such as the service died. |

## selectOutputDeviceForAudioRenderer

```TypeScript
selectOutputDeviceForAudioRenderer(renderer: AudioRenderer, outputDevice: AudioDeviceDescriptor): Promise<void>
```

Selects the output device for the target AudioRenderer. Your application must ensure that the specified AudioRenderer is valid. This selection only applies to the designated stream; other playback streams in your application will use your application's forced selection or the system's default output device. The selection will become invalid when your application exits or the selected device goes offline. After your application restarts or the device comes back online, your application must re-issue the selection for it to take effect. If the system does not support this function, the system will select a default output device for the renderer.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioDeviceEnhanceManager-selectOutputDeviceForAudioRenderer(renderer: AudioRenderer, outputDevice: AudioDeviceDescriptor): Promise<void>--><!--Device-AudioDeviceEnhanceManager-selectOutputDeviceForAudioRenderer(renderer: AudioRenderer, outputDevice: AudioDeviceDescriptor): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Audio.DeviceEnhance

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| renderer | [AudioRenderer](arkts-audio-audio-audiorenderer-i.md) | Yes | The instance of AudioRenderer. |
| outputDevice | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Yes | Audio device descriptor in the array returned by [getAvailableDevices](arkts-audio-audio-audioroutingmanager-i.md#getavailabledevices). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed, for example, the selected device does not exist. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio service error occurs, such as the service died. |
