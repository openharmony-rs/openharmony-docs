# Interface (AudioSessionManager)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

> **说明：**
>
> - 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 12开始支持。

音频会话管理。

在使用AudioSessionManager的接口之前，需先通过[getSessionManager](arkts-apis-audio-AudioManager.md#getsessionmanager12)获取AudioSessionManager实例。

## 导入模块

```ts
import { audio } from '@kit.AudioKit';
```

## activateAudioSession<sup>12+</sup>

activateAudioSession(strategy: AudioSessionStrategy): Promise\<void>

激活音频会话。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型                                              | 必填 | 说明         |
| ------ |-------------------------------------------------| ---- | ------------ |
| strategy | [AudioSessionStrategy](arkts-apis-audio-i.md#audiosessionstrategy12) | 是   | 音频会话策略。 |

**返回值：**

| 类型           | 说明                      |
| -------------- | ------------------------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | ---------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters unspecified. 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed.|
| 6800301 | System error. Returned by promise. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let strategy: audio.AudioSessionStrategy = {
  concurrencyMode: audio.AudioConcurrencyMode.CONCURRENCY_MIX_WITH_OTHERS
};

audioSessionManager.activateAudioSession(strategy).then(() => {
  console.info('activateAudioSession SUCCESS');
}).catch((err: BusinessError) => {
  console.error(`ERROR: ${err}`);
});
```

## deactivateAudioSession<sup>12+</sup>

deactivateAudioSession(): Promise\<void>

停用音频会话。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**返回值：**

| 类型           | 说明                      |
| -------------- | ------------------------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | ---------------------------------------------|
| 6800301 | System error. Returned by promise. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioSessionManager.deactivateAudioSession().then(() => {
  console.info('deactivateAudioSession SUCCESS');
}).catch((err: BusinessError) => {
  console.error(`ERROR: ${err}`);
});
```

## isAudioSessionActivated<sup>12+</sup>

isAudioSessionActivated(): boolean

检查音频会话是否已激活。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**返回值：**

| 类型                                              | 说明                                    |
| ------------------------------------------------- |---------------------------------------|
| boolean | 音频会话是否处于激活状态。true表示已激活，false表示已停用。 |

**示例：**

```ts
let isActivated = audioSessionManager.isAudioSessionActivated();
```

## on('audioSessionDeactivated')<sup>12+</sup>

on(type: 'audioSessionDeactivated', callback: Callback\<AudioSessionDeactivatedEvent>): void

监听音频会话停用事件（当音频会话停用时触发）。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名   | 类型                                                                        | 必填 | 说明                                                         |
| -------- |---------------------------------------------------------------------------| ---- | ------------------------------------------------------------ |
| type     | string | 是   | 事件回调类型，支持的事件为'audioSessionDeactivated'，当音频会话停用时，触发该事件。 |
| callback | Callback<[AudioSessionDeactivatedEvent](arkts-apis-audio-i.md#audiosessiondeactivatedevent12)> | 是   | 回调函数，返回音频会话停用原因。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters unspecified. 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
audioSessionManager.on('audioSessionDeactivated', (audioSessionDeactivatedEvent: audio.AudioSessionDeactivatedEvent) => {
  console.info(`reason of audioSessionDeactivated: ${audioSessionDeactivatedEvent.reason} `);
});
```

## off('audioSessionDeactivated')<sup>12+</sup>

off(type: 'audioSessionDeactivated', callback?: Callback\<AudioSessionDeactivatedEvent>): void

取消监听音频会话停用事件。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名   | 类型                                   | 必填 | 说明                                                         |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string | 是   | 事件回调类型，支持的事件为'audioSessionDeactivated'，当取消监听音频会话停用事件时，触发该事件。 |
| callback |Callback<[AudioSessionDeactivatedEvent](arkts-apis-audio-i.md#audiosessiondeactivatedevent12)> | 否   | 回调函数，返回音频会话停用原因。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
// 取消该事件的所有监听。
audioSessionManager.off('audioSessionDeactivated');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let audioSessionDeactivatedCallback = (audioSessionDeactivatedEvent: audio.AudioSessionDeactivatedEvent) => {
  console.info(`reason of audioSessionDeactivated: ${audioSessionDeactivatedEvent.reason} `);
};

audioSessionManager.on('audioSessionDeactivated', audioSessionDeactivatedCallback);

audioSessionManager.off('audioSessionDeactivated', audioSessionDeactivatedCallback);
```

## setAudioSessionScene<sup>20+</sup>

setAudioSessionScene(scene: AudioSessionScene): void

设置音频会话场景参数。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名   | 类型                                   | 必填 | 说明                                                         |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| scene     | [AudioSessionScene](arkts-apis-audio-e.md#audiosessionscene20) | 是   | 音频会话场景。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | ---------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800103 | Operation not permit at current state.|
| 6800301 | Audio client call audio service error, System error. |

**示例：**

```ts
audioSessionManager.setAudioSessionScene(audio.AudioSessionScene.AUDIO_SESSION_SCENE_MEDIA);
```

## on('audioSessionStateChanged')<sup>20+</sup>

on(type: 'audioSessionStateChanged', callback: Callback\<AudioSessionStateChangedEvent>): void

监听音频会话状态变更事件（当音频会话焦点变更时触发）。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名   | 类型                                                                        | 必填 | 说明                                                         |
| -------- |---------------------------------------------------------------------------| ---- | ------------------------------------------------------------ |
| type     | string | 是   | 事件回调类型，支持的事件为'audioSessionStateChanged'，当音频会话状态变更时，触发该事件。 |
| callback | Callback<[AudioSessionStateChangedEvent](arkts-apis-audio-i.md#audiosessionstatechangedevent20)> | 是   | 回调函数，返回音频会话变更提示信息。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800102 | Allocate memory failed. |
| 6800301 | Audio client call audio service error, System error. |

**示例：**

```ts
audioSessionManager.on('audioSessionStateChanged', (audioSessionStateChangedEvent: audio.AudioSessionStateChangedEvent) => {
  console.info(`hint of audioSessionStateChanged: ${audioSessionStateChangedEvent.stateChangeHint} `);
});
```

## off('audioSessionStateChanged')<sup>20+</sup>

off(type: 'audioSessionStateChanged', callback?: Callback\<AudioSessionStateChangedEvent>): void

取消监听音频会话状态变更事件。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名   | 类型                                                                        | 必填 | 说明                                                         |
| -------- |---------------------------------------------------------------------------| ---- | ------------------------------------------------------------ |
| type     | string | 是   | 事件回调类型，支持的事件为'audioSessionStateChanged'，当音频会话状态变更时，触发该事件。 |
| callback | Callback<[AudioSessionStateChangedEvent](arkts-apis-audio-i.md#audiosessionstatechangedevent20)> | 否 | 回调函数，返回音频会话变更提示信息。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800301 | Audio client call audio service error, System error. |

**示例：**

```ts
// 取消该事件的所有监听。
audioSessionManager.off('audioSessionStateChanged');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let audioSessionStateChangedCallback = (audioSessionStateChangedEvent: audio.AudioSessionStateChangedEvent) => {
  console.info(`hint of audioSessionStateChanged: ${audioSessionStateChangedEvent.stateChangeHint} `);
};

audioSessionManager.on('audioSessionStateChanged', audioSessionStateChangedCallback);

audioSessionManager.off('audioSessionStateChanged', audioSessionStateChangedCallback);
```

## setDefaultOutputDevice<sup>20+</sup>

setDefaultOutputDevice(deviceType: DeviceType): Promise&lt;void&gt;

设置默认发声设备。使用Promise方式进行异步回调。

> **说明：**
>
> - 本接口适用于以下情况：当设置的[AudioSessionScene](arkts-apis-audio-e.md#audiosessionscene20)为VoIP场景时，激活AudioSession后立即生效。若[AudioSessionScene](arkts-apis-audio-e.md#audiosessionscene20)为非VoIP场景，激活AudioSession时不会生效，仅在启动播放的[StreamUsage](arkts-apis-audio-e.md#streamusage)为语音消息、VoIP语音通话或VoIP视频通话时才生效。支持听筒、扬声器和系统默认设备。
>
> - 本接口允许在AudioSessionManager创建后随时调用，系统会记录应用设置的默认本机内置发声设备。但只有激活AudioSession后才能生效。应用启动播放时，若外接设备如蓝牙耳机或有线耳机已接入，系统优先从外接设备发声。否则，系统遵循应用设置的默认本机内置发声设备。
>
> - 本接口优先级低于[AVCastPicker](../apis-avsession-kit/ohos-multimedia-avcastpicker.md#avcastpicker)。如果使用AVCastPicker切换过发声设备，再次调用本接口将不生效。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名     | 类型             | 必填   | 说明                                                      |
| ---------- |----------------| ------ |---------------------------------------------------------|
| deviceType | [DeviceType](arkts-apis-audio-e.md#devicetype) | 是     | 设备类型。<br>仅支持以下设备：EARPIECE（听筒）、SPEAKER（扬声器）和DEFAULT（系统默认设备）。 |

**返回值：**

| 类型                | 说明                          |
| ------------------- | ----------------------------- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. Return by promise. |
| 6800102 | Allocate memory failed. Return by promise. |
| 6800301 | Audio client call audio service error, System error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioSessionManager.setDefaultOutputDevice(audio.DeviceType.SPEAKER).then(() => {
  console.info('setDefaultOutputDevice Success!');
}).catch((err: BusinessError) => {
  console.error(`setDefaultOutputDevice Fail: ${err}`);
});
```

## getDefaultOutputDevice<sup>20+</sup>

getDefaultOutputDevice(): DeviceType

获取通过[setDefaultOutputDevice](#setdefaultoutputdevice20)设置的默认发声设备。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型                                              | 说明                                    |
| ------------------------------------------------- |---------------------------------------|
| DeviceType |设备类型。<br>仅支持以下设备：EARPIECE（听筒）、SPEAKER（扬声器）和DEFAULT（系统默认设备）。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID   | 错误信息 |
|---------| --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800103 | Operation not permit at current state. Return by promise. |

**示例：**

```ts
let deviceType = audioSessionManager.getDefaultOutputDevice();
```

## on('currentOutputDeviceChanged')<sup>20+</sup>

on(type: 'currentOutputDeviceChanged', callback: Callback\<CurrentOutputDeviceChangedEvent>): void

监听当前输出设备变化事件（当前输出设备发生变化时触发）。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                                                      |
| :------- | :--------------------------------------------------- | :--- |:--------------------------------------------------------|
| type     | string | 是   | 事件回调类型，支持的事件为'currentOutputDeviceChanged'，当前输出设备变更时触发。|
| callback | Callback<[CurrentOutputDeviceChangedEvent](arkts-apis-audio-i.md#currentoutputdevicechangedevent20)> | 是   | 回调函数，返回当前输出设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800102 | Allocate memory failed. |
| 6800301 | Audio client call audio service error, System error. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

let currentOutputDeviceChangedCallback = (currentOutputDeviceChangedEvent: audio.CurrentOutputDeviceChangedEvent) => {
  console.info(`reason of audioSessionStateChanged: ${currentOutputDeviceChangedEvent.changeReason} `);
};

audioSessionManager.on('currentOutputDeviceChanged', currentOutputDeviceChangedCallback);
```

## off('currentOutputDeviceChanged')<sup>20+</sup>

off(type: 'currentOutputDeviceChanged', callback?: Callback\<CurrentOutputDeviceChangedEvent>): void

取消监听当前输出设备的变化事件，并使用callback进行异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                                                      |
| :------- | :--------------------------------------------------- | :--- |:--------------------------------------------------------|
| type     | string | 是   | 事件回调类型，支持的事件为'currentOutputDeviceChanged'，当前输出设备发生变化时，触发该事件。|
| callback | Callback<[CurrentOutputDeviceChangedEvent](arkts-apis-audio-i.md#currentoutputdevicechangedevent20)> | 否 | 回调函数，用于返回当前输出设备变化的信息。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800301 | Audio client call audio service error, System error. |

**示例：**

```ts
// 取消该事件的所有监听。
audioSessionManager.off('currentOutputDeviceChanged');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let currentOutputDeviceChangedCallback = (currentOutputDeviceChangedEvent: audio.CurrentOutputDeviceChangedEvent) => {
  console.info(`reason of audioSessionStateChanged: ${currentOutputDeviceChangedEvent.changeReason} `);
};

audioSessionManager.on('currentOutputDeviceChanged', currentOutputDeviceChangedCallback);

audioSessionManager.off('currentOutputDeviceChanged', currentOutputDeviceChangedCallback);
```

## getAvailableDevices<sup>21+</sup>

getAvailableDevices(deviceUsage: DeviceUsage): AudioDeviceDescriptors

获取音频可选设备列表。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                                                      |
| :------- | :--------------------------------------------------- | :--- |:--------------------------------------------------------|
| deviceUsage| [DeviceUsage](arkts-apis-audio-e.md#deviceusage12) | 是   | 音频设备类型（根据用途分类）。 |

**返回值：**

| 类型                                                         | 说明                      |
| ------------------------------------------------------------ | ------------------------- |
| [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors) | 返回设备列表。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800301 | Audio client call audio service error, System error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data: audio.AudioDeviceDescriptors = audioSessionManager.getAvailableDevices(audio.DeviceUsage.MEDIA_OUTPUT_DEVICES);
  console.info('Succeeded in doing getAvailableDevices.');
} catch (err) {
  let error = err as BusinessError;
   console.error(`Failed to getAvailableDevices. Code: ${error.code}, message: ${error.message}`);
}
```

## on('availableDeviceChange')<sup>21+</sup>

on(type: 'availableDeviceChange', deviceUsage: DeviceUsage, callback: Callback\<DeviceChangeAction>): void

监听音频可选设备连接状态变化事件（当音频可选设备连接状态发生变化时触发）。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                                                      |
| :------- | :--------------------------------------------------- | :--- |:--------------------------------------------------------|
| type     | string                                               | 是   | 事件回调类型，支持的事件为'availableDeviceChange'，当音频可选设备连接状态发生变化时，触发该事件。 |
| deviceUsage | [DeviceUsage](arkts-apis-audio-e.md#deviceusage12)                       | 是   | 音频设备类型（根据用途分类）。     |
| callback | Callback<[DeviceChangeAction](arkts-apis-audio-i.md#devicechangeaction)\> | 是   | 回调函数，返回设备更新详情。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800301 | Audio client call audio service error, System error. |

**示例：**

```ts
audioSessionManager.on('availableDeviceChange', audio.DeviceUsage.MEDIA_INPUT_DEVICES, (deviceChanged: audio.DeviceChangeAction) => {
  console.info('device change type : ' + deviceChanged.type);
  console.info('device descriptor size : ' + deviceChanged.deviceDescriptors.length);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceRole);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceType);
});
```

## off('availableDeviceChange')<sup>21+</sup>

off(type: 'availableDeviceChange', callback?: Callback<DeviceChangeAction\>): void

取消监听音频可选设备连接状态变化事件。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                | 必填 | 说明                                       |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------ |
| type     | string                                              | 是   | 事件回调类型，支持的事件为'availableDeviceChange'，当取消监听音频可选设备连接变化事件时，触发该事件。 |
| callback | Callback\<[DeviceChangeAction](arkts-apis-audio-i.md#devicechangeaction)\> | 否   | 回调函数，返回可选设备更新详情。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**示例：**

```ts
// 取消该事件的所有监听。
audioSessionManager.off('availableDeviceChange');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let availableDeviceChangeCallback = (deviceChanged: audio.DeviceChangeAction) => {
  console.info('device change type : ' + deviceChanged.type);
  console.info('device descriptor size : ' + deviceChanged.deviceDescriptors.length);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceRole);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceType);
};

audioSessionManager.on('availableDeviceChange', audio.DeviceUsage.MEDIA_INPUT_DEVICES, availableDeviceChangeCallback);

audioSessionManager.off('availableDeviceChange', availableDeviceChangeCallback);
```

## selectMediaInputDevice<sup>21+</sup>

selectMediaInputDevice(inputAudioDevice: AudioDeviceDescriptor): Promise<void\>

设置媒体输入设备。使用Promise异步回调。

此功能不适用于呼叫录音，即[SourceType](arkts-apis-audio-e.md#sourcetype8)为SOURCE_TYPE_VOICE_COMMUNICATION的场景不适用。
在存在更高优先级的并发录音流的场景中，应用程序实际使用的输入设备可能与所选设备不同。
应用程序可以监听[currentInputDeviceChanged](#oncurrentinputdevicechanged21)事件来获得实际的输入设备。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                                                      |
| :------- | :--------------------------------------------------- | :--- |:--------------------------------------------------------|
| inputAudioDevice| [AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) | 是   | 媒体输入设备。 |

**返回值：**

| 类型           | 说明                      |
| -------------- | ------------------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800301 | Audio client call audio service error, System error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data: audio.AudioDeviceDescriptors = audioSessionManager.getAvailableDevices(audio.DeviceUsage.MEDIA_OUTPUT_DEVICES);
  console.info('Succeeded in doing getAvailableDevices.');

  if (data[0]) {
    audioSessionManager.selectMediaInputDevice(data[0]).then(() => {
      console.info('Succeeded in doing selectMediaInputDevice.');
    }).catch((selectErr: BusinessError) => {
      console.error(`Failed to selectMediaInputDevice. Code: ${selectErr.code}, message: ${selectErr.message}`);
    });
  }
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getAvailableDevices. Code: ${error.code}, message: ${error.message}`);
}
```

## getSelectedMediaInputDevice<sup>21+</sup>

getSelectedMediaInputDevice(): AudioDeviceDescriptor

获得通过[selectMediaInputDevice](#selectmediainputdevice21)设置的媒体输入设备。
如果没有设置，返回一个deviceType属性为INVALID的设备。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型           | 说明                      |
| -------------- | ------------------------- |
| [AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) | 媒体输入设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800301 | Audio client call audio service error, System error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let device: audio.AudioDeviceDescriptor = audioSessionManager.getSelectedMediaInputDevice();
  console.info('Succeeded in doing getSelectedMediaInputDevice.');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getSelectedMediaInputDevice. Code: ${error.code}, message: ${error.message}`);
}
```

## clearSelectedMediaInputDevice<sup>21+</sup>

clearSelectedMediaInputDevice(): Promise<void\>

清空通过[selectMediaInputDevice](#selectmediainputdevice21)设置的媒体输入设备。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型           | 说明                      |
| -------------- | ------------------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800301 | Audio client call audio service error, System error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioSessionManager.clearSelectedMediaInputDevice().then(() => {
  console.info('Succeeded in doing clearSelectedMediaInputDevice.');
}).catch((err: BusinessError) => {
  console.error(`Failed to clearSelectedMediaInputDevice. Code: ${err.code}, message: ${err.message}`);
});
```

## setBluetoothAndNearlinkPreferredRecordCategory<sup>21+</sup>

setBluetoothAndNearlinkPreferredRecordCategory(category: BluetoothAndNearlinkPreferredRecordCategory): Promise<void\>

设置在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。使用Promise异步回调。

应用程序可以在蓝牙或星闪连接之前设置此分类，系统将在设备连接时优先使用蓝牙或星闪进行录音。
在更高优先级的并发录音流的场景中，应用程序实际使用的输入设备可能与当前设置的偏好设备不同。
应用程序可以监听[currentInputDeviceChanged](#oncurrentinputdevicechanged21)事件来获得实际的输入设备。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                                                      |
| :------- | :--------------------------------------------------- | :--- |:--------------------------------------------------------|
| category| [BluetoothAndNearlinkPreferredRecordCategory](arkts-apis-audio-e.md#bluetoothandnearlinkpreferredrecordcategory21) | 是   | 在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。 |

**返回值：**

| 类型           | 说明                      |
| -------------- | ------------------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800301 | Audio client call audio service error, System error. |

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const category = audio.BluetoothAndNearlinkPreferredRecordCategory.PREFERRED_LOW_LATENCY;
audioSessionManager.setBluetoothAndNearlinkPreferredRecordCategory(category).then(() => {
  console.info('Succeeded in doing setBluetoothAndNearlinkPreferredRecordCategory.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setBluetoothAndNearlinkPreferredRecordCategory. Code: ${err.code}, message: ${err.message}`);
});
```

## getBluetoothAndNearlinkPreferredRecordCategory<sup>21+</sup>

getBluetoothAndNearlinkPreferredRecordCategory(): BluetoothAndNearlinkPreferredRecordCategory

获取通过[setBluetoothAndNearlinkPreferredRecordCategory](#setbluetoothandnearlinkpreferredrecordcategory21)设置的在使用蓝牙或星闪进行录音时的设备偏好分类。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型           | 说明                      |
| -------------- | ------------------------- |
| [BluetoothAndNearlinkPreferredRecordCategory](arkts-apis-audio-e.md#bluetoothandnearlinkpreferredrecordcategory21) | 在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800301 | Audio client call audio service error, System error. |

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let category: audio.BluetoothAndNearlinkPreferredRecordCategory = audioSessionManager.getBluetoothAndNearlinkPreferredRecordCategory();
  console.info('Succeeded in doing getBluetoothAndNearlinkPreferredRecordCategory.');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getBluetoothAndNearlinkPreferredRecordCategory. Code: ${error.code}, message: ${error.message}`);
}
```

## on('currentInputDeviceChanged')<sup>21+</sup>

on(type: 'currentInputDeviceChanged', callback: Callback<CurrentInputDeviceChangedEvent\>): void

监听当前输入设备变化事件（当前输入设备发生变化时触发）。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                                       |
| :------- | :--------------------------------------------------- | :--- | :----------------------------------------- |
| type     | string | 是   | 事件回调类型，支持的事件为'currentInputDeviceChanged'，当前输入设备发生变化时，触发该事件。 |
| callback | Callback\<[CurrentInputDeviceChangedEvent](arkts-apis-audio-i.md#currentinputdevicechangedevent21)\> | 是   | 回调函数，返回当前输入设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800301 | Audio client call audio service error, System error. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

let currentInputDeviceChangedCallback = (currentInputDeviceChangedEvent: audio.CurrentInputDeviceChangedEvent) => {
  console.info(`reason of currentInputDeviceChanged: ${currentInputDeviceChangedEvent.changeReason} `);
};

audioSessionManager.on('currentInputDeviceChanged', currentInputDeviceChangedCallback);
```

## off('currentInputDeviceChanged')<sup>21+</sup>

off(type: 'currentInputDeviceChanged', callback?: Callback<CurrentInputDeviceChangedEvent\>): void

取消监听当前输入设备的变化事件。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                                                      |
| :------- | :--------------------------------------------------- | :--- |:--------------------------------------------------------|
| type     | string | 是   | 事件回调类型，支持的事件为'currentInputDeviceChanged'，当前输入设备发生变化时，触发该事件。|
| callback | Callback<[CurrentInputDeviceChangedEvent](arkts-apis-audio-i.md#currentinputdevicechangedevent21)> | 否 | 回调函数，用于返回当前输入设备变化的信息。 |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800301 | Audio client call audio service error, System error. |

**示例：**

```ts
// 取消该事件的所有监听。
audioSessionManager.off('currentInputDeviceChanged');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let currentInputDeviceChangedCallback = (currentInputDeviceChangedEvent: audio.CurrentInputDeviceChangedEvent) => {
  console.info(`reason of currentInputDeviceChanged: ${currentInputDeviceChangedEvent.changeReason} `);
};

audioSessionManager.on('currentInputDeviceChanged', currentInputDeviceChangedCallback);

audioSessionManager.off('currentInputDeviceChanged', currentInputDeviceChangedCallback);
```