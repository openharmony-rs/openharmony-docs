# Interface (AudioDeviceEnhanceManager)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

音频设备增强管理功能，用于应用级音频设备选择及流维度音频设备选择。

在使用AudioDeviceEnhanceManager的接口之前，需要先通过[getDeviceEnhanceManager](arkts-apis-audio-AudioManager.md#getdeviceenhancemanager)获取AudioDeviceEnhanceManager实例。

> **说明：**
>
> 应用在使用前应先调用[isEnhancedRoutingSupported](#isenhancedroutingsupported)，确认系统是否支持音频设备增强管理功能。

**起始版本：** 26.0.0

## 导入模块

```ts
import { audio } from '@kit.AudioKit';
```

## isEnhancedRoutingSupported()

isEnhancedRoutingSupported(): boolean

查询系统是否支持当前管理器提供的增强路由能力。

> **说明：**
>
> - 增强路由能力包括为应用或音频流选择输入输出设备。
> - 应用在调用增强路由相关接口前，先调用本接口确认系统是否支持。即使是同一类型设备，不同机型也会因硬件限制而支持情况不同。
> - 当系统不支持增强路由能力时，调用相关接口不会生效，并会为应用或音频流选择默认的输入输出设备。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.DeviceEnhance

**返回值：**

| 类型 | 说明 |
| ---------------------- | ------------------------------------------------------------ |
| boolean | 表示系统是否支持增强路由能力。true表示支持，false表示不支持。 |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

let audioManager = audio.getAudioManager();
let audioDeviceEnhanceManager: audio.AudioDeviceEnhanceManager = audioManager.getDeviceEnhanceManager();
let isSupported: boolean = audioDeviceEnhanceManager.isEnhancedRoutingSupported();
console.info(`Succeeded in querying whether enhanced routing is supported. Result: ${isSupported}.`);
```

## selectOutputDevice()

selectOutputDevice(outputDevice: AudioDeviceDescriptor): Promise&lt;void&gt;

为应用选择输出设备。使用Promise异步回调。

> **说明：**
>
> - 此设置对应用下创建的所有播放流生效，除非特定流已经通过[selectOutputDeviceForAudioRenderer](#selectoutputdeviceforaudiorenderer)指定了专属输出设备。
> - 当应用实现输出设备选择功能时，可以通过[AudioRoutingManager.getAvailableDevices](arkts-apis-audio-AudioRoutingManager.md#getavailabledevices12)获取可用输出设备列表，并通过[AudioRoutingManager.getPreferOutputDeviceForRendererInfo](arkts-apis-audio-AudioRoutingManager.md#getpreferoutputdeviceforrendererinfo10)获取当前首选输出设备。
> - 当应用退出或所选设备离线时，此选择将失效。应用重启或设备重新上线后，需要重新设置才会生效。
> - 当系统不支持此功能时，会为应用选择默认输出设备。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.DeviceEnhance

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| outputDevice | [AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) | 是 | 输出设备描述，需从[AudioRoutingManager.getAvailableDevices](arkts-apis-audio-AudioRoutingManager.md#getavailabledevices12)返回的设备数组中获取。 |

**返回值：**

| 类型 | 说明 |
| ------------------- | ------------------------------ |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------------------- |
| 6800101 | Parameter verification failed, for example, the selected device does not exist. |
| 6800301 | Audio service error occurs, such as the service died. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioManager = audio.getAudioManager();
let audioSessionManager: audio.AudioSessionManager = audioManager.getSessionManager();
let audioDeviceEnhanceManager: audio.AudioDeviceEnhanceManager = audioManager.getDeviceEnhanceManager();
let outputDevice: audio.AudioDeviceDescriptor = audioSessionManager.getAvailableDevices(audio.DeviceUsage.MEDIA_OUTPUT_DEVICES)[0];
audioDeviceEnhanceManager.selectOutputDevice(outputDevice).then(() => {
  console.info('Succeeded in selecting output device.');
}).catch((err: BusinessError) => {
  console.error(`Failed to select output device. Code: ${err.code}, message: ${err.message}`);
});
```

## selectInputDevice()

selectInputDevice(inputDevice: AudioDeviceDescriptor): Promise&lt;void&gt;

为应用选择输入设备。使用Promise异步回调。

> **说明：**
>
> - 此设置对应用下创建的所有录音流生效，除非特定流已经通过[selectInputDeviceForAudioCapturer](#selectinputdeviceforaudiocapturer)指定了专属输入设备。
> - 当应用实现输入设备选择功能时，可以通过[AudioRoutingManager.getAvailableDevices](arkts-apis-audio-AudioRoutingManager.md#getavailabledevices12)获取可用输入设备列表，并通过[AudioRoutingManager.getPreferredInputDeviceForCapturerInfo](arkts-apis-audio-AudioRoutingManager.md#getpreferredinputdeviceforcapturerinfo10)获取当前首选输入设备。
> - 当应用退出或所选设备离线时，此选择将失效。应用重启或设备重新上线后，需要重新设置才会生效。
> - 当系统不支持此功能时，会为应用选择默认输入设备。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.DeviceEnhance

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| inputDevice | [AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) | 是 | 输入设备描述，需从[AudioRoutingManager.getAvailableDevices](arkts-apis-audio-AudioRoutingManager.md#getavailabledevices12)返回的设备数组中获取。 |

**返回值：**

| 类型 | 说明 |
| ------------------- | ------------------------------ |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------------------- |
| 6800101 | Parameter verification failed, for example, the selected device does not exist. |
| 6800301 | Audio service error occurs, such as the service died. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioManager = audio.getAudioManager();
let audioSessionManager: audio.AudioSessionManager = audioManager.getSessionManager();
let audioDeviceEnhanceManager: audio.AudioDeviceEnhanceManager = audioManager.getDeviceEnhanceManager();
let inputDevice: audio.AudioDeviceDescriptor = audioSessionManager.getAvailableDevices(audio.DeviceUsage.MEDIA_INPUT_DEVICES)[0];
audioDeviceEnhanceManager.selectInputDevice(inputDevice).then(() => {
  console.info('Succeeded in selecting input device.');
}).catch((err: BusinessError) => {
  console.error(`Failed to select input device. Code: ${err.code}, message: ${err.message}`);
});
```

## selectOutputDeviceForAudioRenderer()

selectOutputDeviceForAudioRenderer(renderer: AudioRenderer, outputDevice: AudioDeviceDescriptor): Promise&lt;void&gt;

为指定音频播放流设置首选输出设备。使用Promise异步回调。

> **说明：**
>
> - 应用需要确保指定的AudioRenderer实例有效。
> - 此选择仅对指定音频流生效，应用内其他播放流会继续使用应用级选择的设备或系统默认输出设备。
> - 当应用退出或所选设备离线时，此选择将失效。应用重启或设备重新上线后，需要重新设置才会生效。
> - 当系统不支持此功能时，会为该音频播放流选择默认输出设备。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.DeviceEnhance

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| renderer | [AudioRenderer](arkts-apis-audio-AudioRenderer.md) | 是 | AudioRenderer实例。 |
| outputDevice | [AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) | 是 | 输出设备描述，需从[AudioRoutingManager.getAvailableDevices](arkts-apis-audio-AudioRoutingManager.md#getavailabledevices12)返回的设备数组中获取。 |

**返回值：**

| 类型 | 说明 |
| ------------------- | ------------------------------ |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------------------- |
| 6800101 | Parameter verification failed, for example, the selected device does not exist. |
| 6800301 | Audio service error occurs, such as the service died. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioManager = audio.getAudioManager();
let audioSessionManager: audio.AudioSessionManager = audioManager.getSessionManager();
let audioDeviceEnhanceManager: audio.AudioDeviceEnhanceManager = audioManager.getDeviceEnhanceManager();
// audioRenderer需提前通过audio.createAudioRenderer创建。
let audioRenderer: audio.AudioRenderer;
let outputDevice: audio.AudioDeviceDescriptor = audioSessionManager.getAvailableDevices(audio.DeviceUsage.MEDIA_OUTPUT_DEVICES)[0];
audioDeviceEnhanceManager.selectOutputDeviceForAudioRenderer(audioRenderer, outputDevice).then(() => {
  console.info('Succeeded in selecting output device for audio renderer.');
}).catch((err: BusinessError) => {
  console.error(`Failed to select output device for audio renderer. Code: ${err.code}, message: ${err.message}`);
});
```

## selectInputDeviceForAudioCapturer()

selectInputDeviceForAudioCapturer(capturer: AudioCapturer, inputDevice: AudioDeviceDescriptor): Promise&lt;void&gt;

为指定音频录制流设置首选输入设备。使用Promise异步回调。

> **说明：**
>
> - 应用需要确保指定的AudioCapturer实例有效。
> - 此选择仅对指定音频流生效，应用内其他录音流会继续使用应用级选择的设备或系统默认输入设备。
> - 当应用退出或所选设备离线时，此选择将失效。应用重启或设备重新上线后，需要重新设置才会生效。
> - 当系统不支持此功能时，会为该音频录制流选择默认输入设备。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.DeviceEnhance

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| capturer | [AudioCapturer](arkts-apis-audio-AudioCapturer.md) | 是 | AudioCapturer实例。 |
| inputDevice | [AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) | 是 | 输入设备描述，需从[AudioRoutingManager.getAvailableDevices](arkts-apis-audio-AudioRoutingManager.md#getavailabledevices12)返回的设备数组中获取。 |

**返回值：**

| 类型 | 说明 |
| ------------------- | ------------------------------ |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------------------- |
| 6800101 | Parameter verification failed, for example, the selected device does not exist. |
| 6800301 | Audio service error occurs, such as the service died. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioManager = audio.getAudioManager();
let audioSessionManager: audio.AudioSessionManager = audioManager.getSessionManager();
let audioDeviceEnhanceManager: audio.AudioDeviceEnhanceManager = audioManager.getDeviceEnhanceManager();
// audioCapturer需提前通过audio.createAudioCapturer创建。
let audioCapturer: audio.AudioCapturer;
let inputDevice: audio.AudioDeviceDescriptor = audioSessionManager.getAvailableDevices(audio.DeviceUsage.MEDIA_INPUT_DEVICES)[0];
audioDeviceEnhanceManager.selectInputDeviceForAudioCapturer(audioCapturer, inputDevice).then(() => {
  console.info('Succeeded in selecting input device for audio capturer.');
}).catch((err: BusinessError) => {
  console.error(`Failed to select input device for audio capturer. Code: ${err.code}, message: ${err.message}`);
});
```
