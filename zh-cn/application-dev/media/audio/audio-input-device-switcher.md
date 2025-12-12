# 实现音频输入设备路由切换
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

从API version 21开始，支持音频输入设备路由切换。

当应用进行音频输入时，系统会根据音频流类型选择对应的输入设备（SOURCE_TYPE_MIC：内置MIC录音；SOURCE_TYPE_VOICE_COMMUNICATION：跟随当前输出设备）。若默认输入设备不满足应用需求，应用可通过[setBluetoothAndNearlinkPreferredRecordCategory](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setbluetoothandnearlinkpreferredrecordcategory21)或[selectMediaInputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#selectmediainputdevice21)实现音频输入设备路由切换。

## 选择使用蓝牙或者星闪设备进行录音

应用可使用AudioSessionManager的[setBluetoothAndNearlinkPreferredRecordCategory](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setbluetoothandnearlinkpreferredrecordcategory21)设置应用程序的输入设备选择偏好，当蓝牙或星闪设备上线时生效。

> **说明：**
>
> 通话场景下，如果蓝牙或星闪设备在线，系统默认使用蓝牙或星闪设备作为输入设备。

```ts
import { audio } from '@kit.AudioKit';  // 导入audio模块。
import { BusinessError } from '@kit.BasicServicesKit';

let audioManager = audio.getAudioManager();  // 需要先创建AudioManager实例。

let audioSessionManager = audioManager.getSessionManager();  // 再调用AudioManager的方法创建AudioSessionManager实例。

audioSessionManager.setBluetoothAndNearlinkPreferredRecordCategory(audio.BluetoothAndNearlinkPreferredRecordCategory.PREFERRED_LOW_LATENCY).then(() => {
  console.info('Succeeded in setting bluetooth and nearlink preferred record category.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set bluetooth and nearlink preferred record category. Code: ${err.code}, message: ${err.message}`);
});
```

## 选择任意设备进行录音

应用可使用AudioSessionManager的[selectMediaInputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#selectmediainputdevice21)选择输入设备。

> **说明：**
>
> 通话场景下，输入设备跟随当前输出设备，此时其他与通话并发的录音流也会跟随通话输入设备。

```ts
import { audio } from '@kit.AudioKit';  // 导入audio模块。
import { BusinessError } from '@kit.BasicServicesKit';

let audioManager = audio.getAudioManager();  // 需要先创建AudioManager实例。

let audioSessionManager = audioManager.getSessionManager();  // 再调用AudioManager的方法创建AudioSessionManager实例。

// 监听音频可选输入设备连接状态变化事件，当有输入设备上下线时会收到回调通知。
let availableDeviceChangeCallback = (deviceChanged: audio.DeviceChangeAction) => {
  // 回调返回更新后的可用输入设备列表，应用也可在此处执行选择输入设备操作。
  let data: audio.AudioDeviceDescriptors = deviceChanged.deviceDescriptors;
  console.info(`Succeeded in using on or off function, AudioDeviceDescriptors: ${data}.`);
};
audioSessionManager.on('availableDeviceChange', audio.DeviceUsage.MEDIA_INPUT_DEVICES, availableDeviceChangeCallback);

// 监听当前输入设备变化事件，当选择输入设备成功后会触发该回调。
let currentInputDeviceChangedCallback = (currentInputDeviceChangedEvent: audio.CurrentInputDeviceChangedEvent) => {
  console.info(`Succeeded in using on or off function, CurrentInputDeviceChangedEvent: ${currentInputDeviceChangedEvent}.`);
};
audioSessionManager.on('currentInputDeviceChanged', currentInputDeviceChangedCallback);

try {
  // 获取当前可选的音频输入设备列表。
  let data: audio.AudioDeviceDescriptors = audioSessionManager.getAvailableDevices(audio.DeviceUsage.MEDIA_INPUT_DEVICES);
  console.info(`Succeeded in getting available devices, AudioDeviceDescriptors: ${data}.`);

  // 当前可选音频输入设备列表不为空时，可进行选择。
  if (data[0]) {
    // 选择输入设备。
    await audioSessionManager.selectMediaInputDevice(data[0]).then(() => {
      console.info('Succeeded in selecting media input device.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to select media input device. Code: ${err.code}, message: ${err.message}`);
    });
  }
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get available devices. Code: ${error.code}, message: ${error.message}`);
}

// 可通过该接口查询选择输入设备是否成功。
try {
  let device: audio.AudioDeviceDescriptor = audioSessionManager.getSelectedMediaInputDevice();
  console.info('Succeeded in getting select media input device.');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get selected media input device. Code: ${error.code}, message: ${error.message}`);
}

// 取消监听音频可选输入设备连接状态变化事件。
audioSessionManager.off('availableDeviceChange', availableDeviceChangeCallback);

// 取消监听当前输入设备变化事件。
audioSessionManager.off('currentInputDeviceChanged', currentInputDeviceChangedCallback);

// 清空通过selectMediaInputDevice选择的输入设备。
audioSessionManager.clearSelectedMediaInputDevice().then(() => {
  console.info('Succeeded in clearing selected media input device.');
}).catch((err: BusinessError) => {
  console.error(`Failed to clear selected media input device. Code: ${err.code}, message: ${err.message}`);
});
```