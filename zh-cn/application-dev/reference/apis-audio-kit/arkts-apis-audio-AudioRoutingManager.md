# Interface (AudioRoutingManager)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--SE: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--TSE: @Filger-->

> **说明：**
>
> - 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 9开始支持。

音频路由管理。

在使用AudioRoutingManager的接口之前，需先通过[getRoutingManager](arkts-apis-audio-AudioManager.md#getroutingmanager9)获取AudioRoutingManager实例。

## 导入模块

```ts
import { audio } from '@kit.AudioKit';
```

## getDevices<sup>9+</sup>

getDevices(deviceFlag: DeviceFlag, callback: AsyncCallback&lt;AudioDeviceDescriptors&gt;): void

获取音频设备列表。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明                 |
| ---------- | ------------------------------------------------------------ | ---- | -------------------- |
| deviceFlag | [DeviceFlag](arkts-apis-audio-e.md#deviceflag)                                    | 是   | 音频设备类型。     |
| callback   | AsyncCallback&lt;[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)&gt; | 是   | 回调函数。当获取音频设备列表成功，err为undefined，data为获取到的音频设备列表；否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioRoutingManager.getDevices(audio.DeviceFlag.OUTPUT_DEVICES_FLAG, (err: BusinessError, value: audio.AudioDeviceDescriptors) => {
  if (err) {
    console.error(`Failed to obtain the device list. ${err}`);
    return;
  }
  console.info('Callback invoked to indicate that the device list is obtained.');
});
```

## getDevices<sup>9+</sup>

getDevices(deviceFlag: DeviceFlag): Promise&lt;AudioDeviceDescriptors&gt;

获取音频设备列表。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名     | 类型                      | 必填 | 说明             |
| ---------- | ------------------------- | ---- | ---------------- |
| deviceFlag | [DeviceFlag](arkts-apis-audio-e.md#deviceflag) | 是   | 音频设备类型。 |

**返回值：**

| 类型                                                         | 说明                      |
| ------------------------------------------------------------ | ------------------------- |
| Promise&lt;[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)&gt; | Promise对象，返回设备列表。 |

**示例：**

```ts
audioRoutingManager.getDevices(audio.DeviceFlag.OUTPUT_DEVICES_FLAG).then((data: audio.AudioDeviceDescriptors) => {
  console.info('Promise returned to indicate that the device list is obtained.');
});
```

## getDevicesSync<sup>10+</sup>

getDevicesSync(deviceFlag: DeviceFlag): AudioDeviceDescriptors

获取音频设备列表。同步返回结果。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名     | 类型                      | 必填 | 说明             |
| ---------- | ------------------------- | ---- | ---------------- |
| deviceFlag | [DeviceFlag](arkts-apis-audio-e.md#deviceflag) | 是   | 音频设备类型。 |

**返回值：**

| 类型                                                         | 说明                      |
| ------------------------------------------------------------ | ------------------------- |
| [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors) | 返回设备列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data: audio.AudioDeviceDescriptors = audioRoutingManager.getDevicesSync(audio.DeviceFlag.OUTPUT_DEVICES_FLAG);
  console.info(`Indicate that the device list is obtained ${data}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the device list. ${error}`);
}
```

## isMicBlockDetectionSupported<sup>13+</sup>

isMicBlockDetectionSupported(): Promise&lt;boolean&gt;

获取当前设备是否支持麦克风状态检测。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**返回值：**

| 类型                   | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise对象。返回true表示支持；返回false表示不支持。 |

**示例：**

```ts
audioRoutingManager.isMicBlockDetectionSupported().then((value: boolean) => {
  console.info(`Query whether microphone block detection is supported on current device result is ${value}.`);
});
```

## on('micBlockStatusChanged')<sup>13+</sup>

on(type: 'micBlockStatusChanged', callback: Callback<DeviceBlockStatusInfo\>): void

监听麦克风堵塞状态变化事件。使用callback异步回调。

使用此功能前，请查询设备是否支持检测。应用在使用麦克风录音时，若麦克风堵塞状态发生变化，将触发该事件。目前此检测功能仅支持麦克风位于本地设备上。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                                       |
| :------- | :--------------------------------------------------- | :--- | :----------------------------------------- |
| type     | string                                               | 是   | 事件回调类型，支持的事件为'micBlockStatusChanged'，当麦克风堵塞状态发生变化时，触发该事件。 |
| callback | Callback<[DeviceBlockStatusInfo](arkts-apis-audio-i.md#deviceblockstatusinfo13)\> | 是   | 回调函数，返回麦克风被堵塞状态和设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
// 在使用此功能之前，应先查询当前设备是否支持检测。
audioRoutingManager.isMicBlockDetectionSupported().then((value: boolean) => {
  console.info(`Query whether microphone block detection is supported on current device result is ${value}.`);
  if (value) {
    audioRoutingManager.on('micBlockStatusChanged', (micBlockStatusChanged: audio.DeviceBlockStatusInfo) => {
      console.info(`block status : ${micBlockStatusChanged.blockStatus} `);
    });
  }
});
```

## off('micBlockStatusChanged')<sup>13+</sup>

off(type: 'micBlockStatusChanged', callback?: Callback<DeviceBlockStatusInfo\>): void

取消监听麦克风堵塞状态变化事件。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                | 必填 | 说明                                       |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------ |
| type     | string                                              | 是   | 事件回调类型，支持的事件为'micBlockStatusChanged'，当取消监听音频麦克风是否被堵塞变化事件时，触发该事件。 |
| callback | Callback<[DeviceBlockStatusInfo](arkts-apis-audio-i.md#deviceblockstatusinfo13)\> | 否   | 回调函数，返回麦克风被堵塞状态和设备信息。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
// 取消该事件的所有监听。
audioRoutingManager.off('micBlockStatusChanged');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let micBlockStatusCallback = (micBlockStatusChanged: audio.DeviceBlockStatusInfo) => {
  console.info(`block status : ${micBlockStatusChanged.blockStatus} `);
};

audioRoutingManager.on('micBlockStatusChanged', micBlockStatusCallback);

audioRoutingManager.off('micBlockStatusChanged', micBlockStatusCallback);
```

## on('deviceChange')<sup>9+</sup>

on(type: 'deviceChange', deviceFlag: DeviceFlag, callback: Callback<DeviceChangeAction\>): void

监听音频设备连接状态变化事件（当音频设备连接状态发生变化时触发）。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                      |
| :------- | :--------------------------------------------------- | :--- |:------------------------|
| type     | string                                               | 是   | 事件回调类型，支持的事件为'deviceChange'，当音频设备连接状态发生变化时，触发该事件。 |
| deviceFlag | [DeviceFlag](arkts-apis-audio-e.md#deviceflag)                                    | 是   | 音频设备类型。              |
| callback | Callback<[DeviceChangeAction](arkts-apis-audio-i.md#devicechangeaction)\> | 是   | 回调函数，返回设备更新详情。          |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
audioRoutingManager.on('deviceChange', audio.DeviceFlag.OUTPUT_DEVICES_FLAG, (deviceChanged: audio.DeviceChangeAction) => {
  console.info('device change type : ' + deviceChanged.type);
  console.info('device descriptor size : ' + deviceChanged.deviceDescriptors.length);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceRole);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceType);
});
```

## off('deviceChange')<sup>9+</sup>

off(type: 'deviceChange', callback?: Callback<DeviceChangeAction\>): void

取消监听音频设备连接状态变化事件。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                | 必填 | 说明                                       |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------ |
| type     | string                                              | 是   | 事件回调类型，支持的事件为'deviceChange'，当取消监听音频设备连接变化事件时，触发该事件。 |
| callback | Callback<[DeviceChangeAction](arkts-apis-audio-i.md#devicechangeaction)> | 否   | 回调函数，返回设备更新详情。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
// 取消该事件的所有监听。
audioRoutingManager.off('deviceChange');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let deviceChangeCallback = (deviceChanged: audio.DeviceChangeAction) => {
  console.info('device change type : ' + deviceChanged.type);
  console.info('device descriptor size : ' + deviceChanged.deviceDescriptors.length);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceRole);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceType);
};

audioRoutingManager.on('deviceChange', audio.DeviceFlag.OUTPUT_DEVICES_FLAG, deviceChangeCallback);

audioRoutingManager.off('deviceChange', deviceChangeCallback);
```

## setCommunicationDevice<sup>9+</sup>

setCommunicationDevice(deviceType: CommunicationDeviceType, active: boolean, callback: AsyncCallback&lt;void&gt;): void

设置通信设备激活状态。使用callback异步回调。

该接口由于功能设计变化，将在后续版本废弃，不建议开发者使用。

推荐使用AVSession提供的[设备切换组件](../../media/avsession/using-switch-call-devices.md)，实现通话设备切换。

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名     | 类型                                  | 必填 | 说明                      |
| ---------- | ------------------------------------- | ---- |-------------------------|
| deviceType | [CommunicationDeviceType](arkts-apis-audio-e.md#communicationdevicetype9) | 是   | 音频设备类型。                 |
| active     | boolean                               | 是   | 是否设置设备为激活状态。true表示激活，false表示未激活。 |
| callback   | AsyncCallback&lt;void&gt;             | 是   | 回调函数。当设置通信设备激活状态成功，err为undefined，否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioRoutingManager.setCommunicationDevice(audio.CommunicationDeviceType.SPEAKER, true, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set the active status of the device. ${err}`);
    return;
  }
  console.info('Callback invoked to indicate that the device is set to the active status.');
});
```

## getAvailableDevices<sup>12+</sup>

getAvailableDevices(deviceUsage: DeviceUsage): AudioDeviceDescriptors

获取音频可选设备列表。同步返回结果。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名     | 类型                      | 必填 | 说明             |
| ---------- | ------------------------- | ---- | ---------------- |
| deviceUsage| [DeviceUsage](arkts-apis-audio-e.md#deviceusage12) | 是   | 音频设备类型（根据用途分类）。 |

**返回值：**

| 类型                                                         | 说明                      |
| ------------------------------------------------------------ | ------------------------- |
| [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors) | 返回设备列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data: audio.AudioDeviceDescriptors = audioRoutingManager.getAvailableDevices(audio.DeviceUsage.MEDIA_OUTPUT_DEVICES);
  console.info(`Indicate that the device list is obtained ${data}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the device list. ${error}`);
}
```

## on('availableDeviceChange')<sup>12+</sup>

on(type: 'availableDeviceChange', deviceUsage: DeviceUsage, callback: Callback<DeviceChangeAction\>): void

监听音频可选设备连接状态变化事件（当音频可选设备连接状态发生变化时触发）。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                                       |
| :------- | :--------------------------------------------------- | :--- | :----------------------------------------- |
| type     | string                                               | 是   | 事件回调类型，支持的事件为'availableDeviceChange'，当音频可选设备连接状态发生变化时，触发该事件。 |
| deviceUsage | [DeviceUsage](arkts-apis-audio-e.md#deviceusage12)                       | 是   | 音频设备类型（根据用途分类）。     |
| callback | Callback<[DeviceChangeAction](arkts-apis-audio-i.md#devicechangeaction)\> | 是   | 回调函数，返回设备更新详情。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
audioRoutingManager.on('availableDeviceChange', audio.DeviceUsage.MEDIA_OUTPUT_DEVICES, (deviceChanged: audio.DeviceChangeAction) => {
  console.info('device change type : ' + deviceChanged.type);
  console.info('device descriptor size : ' + deviceChanged.deviceDescriptors.length);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceRole);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceType);
});
```

## off('availableDeviceChange')<sup>12+</sup>

off(type: 'availableDeviceChange', callback?: Callback<DeviceChangeAction\>): void

取消监听音频可选设备连接状态变化事件。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                | 必填 | 说明                                       |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------ |
| type     | string                                              | 是   | 事件回调类型，支持的事件为'availableDeviceChange'，当取消监听音频可选设备连接变化事件时，触发该事件。 |
| callback | Callback<[DeviceChangeAction](arkts-apis-audio-i.md#devicechangeaction)> | 否   | 回调函数，返回可选设备更新详情。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
// 取消该事件的所有监听。
audioRoutingManager.off('availableDeviceChange');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let availableDeviceChangeCallback = (deviceChanged: audio.DeviceChangeAction) => {
  console.info('device change type : ' + deviceChanged.type);
  console.info('device descriptor size : ' + deviceChanged.deviceDescriptors.length);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceRole);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceType);
};

audioRoutingManager.on('availableDeviceChange', audio.DeviceUsage.MEDIA_OUTPUT_DEVICES, availableDeviceChangeCallback);

audioRoutingManager.off('availableDeviceChange', availableDeviceChangeCallback);
```

## setCommunicationDevice<sup>9+</sup>

setCommunicationDevice(deviceType: CommunicationDeviceType, active: boolean): Promise&lt;void&gt;

设置通信设备激活状态。使用Promise异步回调。

该接口由于功能设计变化，将在后续版本废弃，不建议开发者使用。

推荐开发者使用AVSession提供的[设备切换组件](../../media/avsession/using-switch-call-devices.md)，实现通话设备切换。

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名     | 类型                                                   | 必填 | 说明               |
| ---------- | ----------------------------------------------------- | ---- | ------------------ |
| deviceType | [CommunicationDeviceType](arkts-apis-audio-e.md#communicationdevicetype9)  | 是   | 活跃音频设备类型。 |
| active     | boolean                                               | 是   | 是否设置设备为激活状态。true表示激活，false表示未激活。     |

**返回值：**

| 类型                | 说明                            |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例：**

```ts
audioRoutingManager.setCommunicationDevice(audio.CommunicationDeviceType.SPEAKER, true).then(() => {
  console.info('Promise returned to indicate that the device is set to the active status.');
});
```

## isCommunicationDeviceActive<sup>9+</sup>

isCommunicationDeviceActive(deviceType: CommunicationDeviceType, callback: AsyncCallback&lt;boolean&gt;): void

获取指定通信设备的激活状态。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名     | 类型                                                  | 必填 | 说明                     |
| ---------- | ---------------------------------------------------- | ---- | ------------------------ |
| deviceType | [CommunicationDeviceType](arkts-apis-audio-e.md#communicationdevicetype9) | 是   | 活跃音频设备类型。       |
| callback   | AsyncCallback&lt;boolean&gt;                         | 是   | 回调函数。当获取指定通信设备的激活状态成功，err为undefined，data为true表示激活，false表示未激活；否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioRoutingManager.isCommunicationDeviceActive(audio.CommunicationDeviceType.SPEAKER, (err: BusinessError, value: boolean) => {
  if (err) {
    console.error(`Failed to obtain the active status of the device. ${err}`);
    return;
  }
  console.info('Callback invoked to indicate that the active status of the device is obtained.');
});
```

## isCommunicationDeviceActive<sup>9+</sup>

isCommunicationDeviceActive(deviceType: CommunicationDeviceType): Promise&lt;boolean&gt;

获取指定通信设备的激活状态。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名     | 类型                                                  | 必填 | 说明               |
| ---------- | ---------------------------------------------------- | ---- | ------------------ |
| deviceType | [CommunicationDeviceType](arkts-apis-audio-e.md#communicationdevicetype9) | 是   | 活跃音频设备类型。 |

**返回值：**

| 类型                   | 说明                             |
| ---------------------- | ------------------------------- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示设备已激活；返回false表示设备未激活。 |

**示例：**

```ts
audioRoutingManager.isCommunicationDeviceActive(audio.CommunicationDeviceType.SPEAKER).then((value: boolean) => {
  console.info(`Promise returned to indicate that the active status of the device is obtained ${value}.`);
});
```

## isCommunicationDeviceActiveSync<sup>10+</sup>

isCommunicationDeviceActiveSync(deviceType: CommunicationDeviceType): boolean

获取指定通信设备的激活状态。同步返回结果。

**系统能力：** SystemCapability.Multimedia.Audio.Communication

**参数：**

| 参数名     | 类型                                                  | 必填 | 说明               |
| ---------- | ---------------------------------------------------- | ---- | ------------------ |
| deviceType | [CommunicationDeviceType](arkts-apis-audio-e.md#communicationdevicetype9) | 是   | 活跃音频设备类型。 |

**返回值：**

| 类型                   | 说明                             |
| ---------------------- | ------------------------------- |
| boolean | 设备是否处于激活状态。true表示处于激活状态，false表示处于未激活状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let value: boolean = audioRoutingManager.isCommunicationDeviceActiveSync(audio.CommunicationDeviceType.SPEAKER);
  console.info(`Indicate that the active status of the device is obtained ${value}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the active status of the device ${error}.`);
}
```

## getPreferOutputDeviceForRendererInfo<sup>10+</sup>

getPreferOutputDeviceForRendererInfo(rendererInfo: AudioRendererInfo, callback: AsyncCallback&lt;AudioDeviceDescriptors&gt;): void

根据音频信息，返回优先级最高的输出设备。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名                       | 类型                                                         | 必填 | 说明                      |
| --------------------------- | ------------------------------------------------------------ | ---- | ------------------------- |
| rendererInfo                | [AudioRendererInfo](arkts-apis-audio-i.md#audiorendererinfo8)                     | 是   | 音频渲染器信息。             |
| callback                    | AsyncCallback&lt;[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)&gt;  | 是   | 回调函数。当获取优先级最高的输出设备成功，err为undefined，data为获取到的优先级最高的输出设备信息；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息                                           |
| ------- |--------------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. Return by callback. |
| 6800301 | System error. Return by callback.                |

**示例：**
```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // 音频流使用类型：音乐。根据业务场景配置，参考StreamUsage。
  rendererFlags: 0 // 音频渲染器标志。
};

audioRoutingManager.getPreferOutputDeviceForRendererInfo(rendererInfo, (err: BusinessError, desc: audio.AudioDeviceDescriptors) => {
  if (err) {
    console.error(`Failed to getPreferOutputDeviceForRendererInfo. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`device descriptor: ${desc}`);
  }
});
```

## getPreferOutputDeviceForRendererInfo<sup>10+</sup>
getPreferOutputDeviceForRendererInfo(rendererInfo: AudioRendererInfo): Promise&lt;AudioDeviceDescriptors&gt;

根据音频信息，返回优先级最高的输出设备。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名                 | 类型                                                         | 必填 | 说明                      |
| ----------------------| ------------------------------------------------------------ | ---- | ------------------------- |
| rendererInfo          | [AudioRendererInfo](arkts-apis-audio-i.md#audiorendererinfo8)                     | 是   | 音频渲染器信息。            |

**返回值：**

| 类型                  | 说明                         |
| --------------------- | --------------------------- |
| Promise&lt;[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)&gt;   | Promise对象，返回优先级最高的输出设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息                                          |
| ------- |-------------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. Return by promise. |
| 6800301 | System error. Return by promise.                |

**示例：**

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // 音频流使用类型：音乐。根据业务场景配置，参考StreamUsage。
  rendererFlags: 0 // 音频渲染器标志。
};

audioRoutingManager.getPreferOutputDeviceForRendererInfo(rendererInfo).then((desc: audio.AudioDeviceDescriptors) => {
  console.info(`device descriptor: ${desc}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getPreferOutputDeviceForRendererInfo. Code: ${err.code}, message: ${err.message}`);
})
```

## getPreferredOutputDeviceForRendererInfoSync<sup>10+</sup>
getPreferredOutputDeviceForRendererInfoSync(rendererInfo: AudioRendererInfo): AudioDeviceDescriptors

根据音频信息，返回优先级最高的输出设备。同步返回结果。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名                 | 类型                                                         | 必填 | 说明                      |
| ----------------------| ------------------------------------------------------------ | ---- | ------------------------- |
| rendererInfo          | [AudioRendererInfo](arkts-apis-audio-i.md#audiorendererinfo8)                     | 是   | 音频渲染器信息。            |

**返回值：**

| 类型                  | 说明                         |
| --------------------- | --------------------------- |
| [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)   | 返回优先级最高的输出设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息                     |
| ------- |--------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // 音频流使用类型：音乐。根据业务场景配置，参考StreamUsage。
  rendererFlags: 0 // 音频渲染器标志。
};

try {
  let desc: audio.AudioDeviceDescriptors = audioRoutingManager.getPreferredOutputDeviceForRendererInfoSync(rendererInfo);
  console.info(`device descriptor: ${desc}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Result ERROR: ${error}`);
}
```

## on('preferOutputDeviceChangeForRendererInfo')<sup>10+</sup>

on(type: 'preferOutputDeviceChangeForRendererInfo', rendererInfo: AudioRendererInfo, callback: Callback<AudioDeviceDescriptors\>): void

监听最高优先级输出设备变化事件（当最高优先级输出设备发生变化时触发）。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                                                      |
| :------- | :--------------------------------------------------- | :--- |:--------------------------------------------------------|
| type     | string | 是   | 事件回调类型，支持的事件为'preferOutputDeviceChangeForRendererInfo'，当最高优先级输出设备发生变化时，触发该事件。|
| rendererInfo  | [AudioRendererInfo](arkts-apis-audio-i.md#audiorendererinfo8)        | 是   | 音频渲染器信息。                                                |
| callback | Callback<[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)\> | 是   | 回调函数，返回优先级最高的输出设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

let rendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // 音频流使用类型：音乐。根据业务场景配置，参考StreamUsage。
  rendererFlags: 0 // 音频渲染器标志。
};

audioRoutingManager.on('preferOutputDeviceChangeForRendererInfo', rendererInfo, (desc: audio.AudioDeviceDescriptors) => {
  console.info(`device descriptor: ${desc}`);
});
```

## off('preferOutputDeviceChangeForRendererInfo')<sup>10+</sup>

off(type: 'preferOutputDeviceChangeForRendererInfo', callback?: Callback<AudioDeviceDescriptors\>): void

取消监听最高优先级输出音频设备变化事件。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                | 必填 | 说明                                       |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------ |
| type     | string | 是   | 事件回调类型，支持的事件为'preferOutputDeviceChangeForRendererInfo'，当取消监听最高优先级输出音频设备变化事件时，触发该事件。 |
| callback | Callback<[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)> | 否   | 回调函数，返回优先级最高的输出设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
// 取消该事件的所有监听。
audioRoutingManager.off('preferOutputDeviceChangeForRendererInfo');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let preferOutputDeviceChangeForRendererInfoCallback = (desc: audio.AudioDeviceDescriptors) => {
  console.info(`device descriptor: ${desc}`);
};
let rendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // 音频流使用类型：音乐。根据业务场景配置，参考StreamUsage。
  rendererFlags: 0 // 音频渲染器标志。
};

audioRoutingManager.on('preferOutputDeviceChangeForRendererInfo', rendererInfo, preferOutputDeviceChangeForRendererInfoCallback);

audioRoutingManager.off('preferOutputDeviceChangeForRendererInfo', preferOutputDeviceChangeForRendererInfoCallback);
```

## getPreferredInputDeviceForCapturerInfo<sup>10+</sup>

getPreferredInputDeviceForCapturerInfo(capturerInfo: AudioCapturerInfo, callback: AsyncCallback&lt;AudioDeviceDescriptors&gt;): void

根据音频信息，返回优先级最高的输入设备。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名                       | 类型                                                         | 必填 | 说明                      |
| --------------------------- | ------------------------------------------------------------ | ---- | ------------------------- |
| capturerInfo                | [AudioCapturerInfo](arkts-apis-audio-i.md#audiocapturerinfo8)                     | 是   | 音频采集器信息。             |
| callback                    | AsyncCallback&lt;[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)&gt;  | 是   | 回调函数。当获取优先级最高的输入设备成功，err为undefined，data为获取到的优先级最高的输入设备信息；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. Return by callback.|
| 6800301 | System error. Return by callback. |

**示例：**
```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let capturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // 音源类型：Mic音频源。根据业务场景配置，参考SourceType。
  capturerFlags: 0 // 音频采集器标志。
};

audioRoutingManager.getPreferredInputDeviceForCapturerInfo(capturerInfo, (err: BusinessError, desc: audio.AudioDeviceDescriptors) => {
  if (err) {
    console.error(`Result ERROR: ${err}`);
  } else {
    console.info(`device descriptor: ${desc}`);
  }
});
```

## getPreferredInputDeviceForCapturerInfo<sup>10+</sup>

getPreferredInputDeviceForCapturerInfo(capturerInfo: AudioCapturerInfo): Promise&lt;AudioDeviceDescriptors&gt;

根据音频信息，返回优先级最高的输入设备。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名                 | 类型                                                         | 必填 | 说明                      |
| ----------------------| ------------------------------------------------------------ | ---- | ------------------------- |
| capturerInfo          | [AudioCapturerInfo](arkts-apis-audio-i.md#audiocapturerinfo8)                     | 是   | 音频采集器信息。            |

**返回值：**

| 类型                  | 说明                         |
| --------------------- | --------------------------- |
| Promise&lt;[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)&gt;   | Promise对象，返回优先级最高的输入设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. Return by promise. |
| 6800301 | System error. Return by promise. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let capturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // 音源类型：Mic音频源。根据业务场景配置，参考SourceType。
  capturerFlags: 0 // 音频采集器标志。
};

audioRoutingManager.getPreferredInputDeviceForCapturerInfo(capturerInfo).then((desc: audio.AudioDeviceDescriptors) => {
  console.info(`device descriptor: ${desc}`);
}).catch((err: BusinessError) => {
  console.error(`Result ERROR: ${err}`);
});
```

## getPreferredInputDeviceForCapturerInfoSync<sup>10+</sup>

getPreferredInputDeviceForCapturerInfoSync(capturerInfo: AudioCapturerInfo): AudioDeviceDescriptors

根据音频信息，返回优先级最高的输入设备。同步返回结果。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名                 | 类型                                                         | 必填 | 说明                      |
| ----------------------| ------------------------------------------------------------ | ---- | ------------------------- |
| capturerInfo          | [AudioCapturerInfo](arkts-apis-audio-i.md#audiocapturerinfo8)                     | 是   | 音频采集器信息。            |

**返回值：**

| 类型                  | 说明                         |
| --------------------- | --------------------------- |
| [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)   | 返回优先级最高的输入设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let capturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // 音源类型：Mic音频源。根据业务场景配置，参考SourceType。
  capturerFlags: 0 // 音频采集器标志。
};

try {
  let desc: audio.AudioDeviceDescriptors = audioRoutingManager.getPreferredInputDeviceForCapturerInfoSync(capturerInfo);
  console.info(`device descriptor: ${desc}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Result ERROR: ${error}`);
}
```

## on('preferredInputDeviceChangeForCapturerInfo')<sup>10+</sup>

on(type: 'preferredInputDeviceChangeForCapturerInfo', capturerInfo: AudioCapturerInfo, callback: Callback<AudioDeviceDescriptors\>): void

监听最高优先级输入设备变化事件（当最高优先级输入设备发生变化时触发）。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                                       |
| :------- | :--------------------------------------------------- | :--- | :----------------------------------------- |
| type     | string | 是   | 事件回调类型，支持的事件为'preferredInputDeviceChangeForCapturerInfo'，当最高优先级输入设备发生变化时，触发该事件。 |
| capturerInfo  | [AudioCapturerInfo](arkts-apis-audio-i.md#audiocapturerinfo8)        | 是   | 音频采集器信息。              |
| callback | Callback<[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)\> | 是   | 回调函数，返回优先级最高的输入设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

let capturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // 音源类型：Mic音频源。根据业务场景配置，参考SourceType。
  capturerFlags: 0 // 音频采集器标志。
};

audioRoutingManager.on('preferredInputDeviceChangeForCapturerInfo', capturerInfo, (desc: audio.AudioDeviceDescriptors) => {
  console.info(`device descriptor: ${desc}`);
});
```

## off('preferredInputDeviceChangeForCapturerInfo')<sup>10+</sup>

off(type: 'preferredInputDeviceChangeForCapturerInfo', callback?: Callback<AudioDeviceDescriptors\>): void

取消监听最高优先级输入音频设备变化事件。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**参数：**

| 参数名   | 类型                                                | 必填 | 说明                                       |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------ |
| type     | string | 是   | 事件回调类型，支持的事件为'preferredInputDeviceChangeForCapturerInfo'，当取消监听最高优先级输入音频设备变化事件时，触发该事件。 |
| callback | Callback<[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)> | 否   | 回调函数，返回优先级最高的输入设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**示例：**

```ts
// 取消该事件的所有监听。
audioRoutingManager.off('preferredInputDeviceChangeForCapturerInfo');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let preferredInputDeviceChangeForCapturerInfoCallback = (desc: audio.AudioDeviceDescriptors) => {
  console.info(`device descriptor: ${desc}`);
};
let capturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // 音源类型：Mic音频源。根据业务场景配置，参考SourceType。
  capturerFlags: 0 // 音频采集器标志。
};

audioRoutingManager.on('preferredInputDeviceChangeForCapturerInfo', capturerInfo, preferredInputDeviceChangeForCapturerInfoCallback);

audioRoutingManager.off('preferredInputDeviceChangeForCapturerInfo', preferredInputDeviceChangeForCapturerInfoCallback);
```
