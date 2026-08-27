# 空间音频管理（仅对系统应用开放）
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @tom_guo-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

空间音频管理主要包含空间音频相关状态和能力的查询、设置与监听。

空间音频管理仅开放给系统级应用，主要包括空间音频相关状态（空间音频渲染的开启与关闭、自适应空间音频渲染的开启与关闭、头动跟踪的开启与关闭）的查询、设置与监听，空间音频相关能力（空间音频渲染能力、头动跟踪能力）的查询，空间化设备状态的更新，以及空间音频渲染场景类型的查询与设置。

其中，自适应空间音频渲染是由系统根据音频内容自动判断是否进行空间音频渲染的能力。开启后，空间音频渲染需要多声道内容才能生效，对单声道、双声道（立体声）内容不生效；关闭后，不影响空间音频渲染。

对于播放音频类的系统级应用，开发者可以查询空间音频渲染与头动跟踪的开关状态，系统/指定设备是否支持空间音频渲染与头动跟踪能力，以及当前使用的空间音频渲染场景类型。

对于空间音频控制类的系统级应用（比如空间音频UX等），开发者在查询上述状态和能力之外，还可以对空间音频渲染开关、自适应空间音频渲染开关、头动跟踪开关以及空间音频渲染场景类型进行设置，以及更新空间化设备的状态，指明特定空间化设备是否支持空间音频渲染和头动跟踪能力。

在使用此功能前，应用需要先申请权限`ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS`，申请方式请参考：system_basic等级应用申请权限的方式。

## 获取空间音频管理接口

在使用AudioSpatializationManager的接口前，需要先调用getSpatializationManager创建AudioSpatializationManager实例。

  ```ts
  import { audio } from '@kit.AudioKit';

  let audioManager = audio.getAudioManager();
  let audioSpatializationManager = audioManager.getSpatializationManager();
  ```

## 查询系统是否支持空间音频渲染能力

系统应用开发者可以通过isSpatializationSupported接口查询当前系统是否具有空间音频渲染的能力。

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    let isSpatializationSupported: boolean = audioSpatializationManager.isSpatializationSupported();
    console.info(`AudioSpatializationManager isSpatializationSupported: ${isSpatializationSupported}`);
  } catch (err) {
    let error = err as BusinessError;
    console.error(`ERROR: ${error}`);
  }
  ```

## 查询指定设备是否支持空间音频渲染能力

系统应用开发者可以通过isSpatializationSupportedForDevice接口查询指定设备是否具有空间音频渲染的能力，该接口需要使用AudioDeviceDescriptor作为入参来指定设备，建议通过音频框架中其他接口来获取当前已连接设备或当前发声设备的AudioDeviceDescriptor。

  ```ts
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let deviceDescriptor: audio.AudioDeviceDescriptor = {
    deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
    deviceType : audio.DeviceType.BLUETOOTH_A2DP,
    id : 1,
    name : "",
    address : "00:11:22:33:FF:EE",
    sampleRates : [44100],
    channelCounts : [2],
    channelMasks : [0],
    networkId : audio.LOCAL_NETWORK_ID,
    interruptGroupId : 1,
    volumeGroupId : 1,
    displayName : ""
  };
  try {
    let isSpatializationSupportedForDevice: boolean = audioSpatializationManager.isSpatializationSupportedForDevice(deviceDescriptor);
    console.info(`AudioSpatializationManager isSpatializationSupportedForDevice: ${isSpatializationSupportedForDevice}`);
  } catch (err) {
    let error = err as BusinessError;
    console.error(`ERROR: ${error}`);
  }
  ```

## 查询系统是否支持头动跟踪能力

系统应用开发者可以通过isHeadTrackingSupported接口查询当前系统是否具有头动跟踪的能力。

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    let isHeadTrackingSupported: boolean = audioSpatializationManager.isHeadTrackingSupported();
    console.info(`AudioSpatializationManager isHeadTrackingSupported: ${isHeadTrackingSupported}`);
  } catch (err) {
    let error = err as BusinessError;
    console.error(`ERROR: ${error}`);
  }
  ```

## 查询指定设备是否支持头动跟踪能力

系统应用开发者可以通过isHeadTrackingSupportedForDevice接口查询指定设备是否具有头动跟踪的能力，该接口需要使用AudioDeviceDescriptor作为入参来指定设备，建议通过音频框架中其他接口来获取当前已连接设备或当前发声设备的AudioDeviceDescriptor。

  ```ts
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let deviceDescriptor: audio.AudioDeviceDescriptor = {
    deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
    deviceType : audio.DeviceType.BLUETOOTH_A2DP,
    id : 1,
    name : "",
    address : "00:11:22:33:FF:EE",
    sampleRates : [44100],
    channelCounts : [2],
    channelMasks : [0],
    networkId : audio.LOCAL_NETWORK_ID,
    interruptGroupId : 1,
    volumeGroupId : 1,
    displayName : ""
  };

  try {
    let isHeadTrackingSupportedForDevice: boolean = audioSpatializationManager.isHeadTrackingSupportedForDevice(deviceDescriptor);
    console.info(`AudioSpatializationManager isHeadTrackingSupportedForDevice: ${isHeadTrackingSupportedForDevice}`);
  } catch (err) {
    let error = err as BusinessError;
    console.error(`ERROR: ${error}`);
  }
  ```

## 开启/关闭指定设备的空间音频渲染效果

系统应用开发者可以通过setSpatializationEnabled接口开启/关闭指定设备的空间音频渲染效果，该接口需要传递两个参数：AudioDeviceDescriptor和enabled。

AudioDeviceDescriptor：用于指定音频设备。建议通过音频框架中其他接口来获取当前已连接设备或当前发声设备的AudioDeviceDescriptor。

enabled：布尔值类型，用于控制指定设备的空间音频渲染开关。入参为true时为开启空间音频渲染，入参为false时为关闭空间音频渲染。

在使用此功能前，应用需要先申请权限`ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS`，申请方式请参考：system_basic等级应用申请权限的方式。

在开启空间音频渲染时，需要先确保系统和指定设备都具有空间音频渲染的能力。

  ```ts
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let deviceDescriptor: audio.AudioDeviceDescriptor = {
    deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
    deviceType : audio.DeviceType.BLUETOOTH_A2DP,
    id : 1,
    name : "",
    address : "00:11:22:33:FF:EE",
    sampleRates : [44100],
    channelCounts : [2],
    channelMasks : [0],
    networkId : audio.LOCAL_NETWORK_ID,
    interruptGroupId : 1,
    volumeGroupId : 1,
    displayName : ""
  };
  let enabled: boolean = true;

  audioSpatializationManager.setSpatializationEnabled(deviceDescriptor, enabled).then(() => {
    console.info('Succeeded in setting spatialization enabled');
  }).catch((err: BusinessError) => {
    console.error(`Result ERROR: ${err}`);
  });
  ```

## 查询指定设备的空间音频渲染效果开关状态

系统应用开发者可以通过isSpatializationEnabled接口查询指定设备的空间音频渲染效果开关状态，该接口需要使用AudioDeviceDescriptor作为入参来指定设备，建议通过音频框架中其他接口来获取当前已连接设备或当前发声设备的AudioDeviceDescriptor。该接口返回为true表示空间音频渲染开启，false表示空间音频渲染关闭。返回值为setSpatializationEnabled接口中成功设置的指定设备空间音频渲染开关状态，默认为关闭。此状态仅表示开关状态，实际是否生效还需依赖系统和指定设备是否支持空间音频渲染。

  ```ts
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let deviceDescriptor: audio.AudioDeviceDescriptor = {
    deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
    deviceType : audio.DeviceType.BLUETOOTH_A2DP,
    id : 1,
    name : "",
    address : "00:11:22:33:FF:EE",
    sampleRates : [44100],
    channelCounts : [2],
    channelMasks : [0],
    networkId : audio.LOCAL_NETWORK_ID,
    interruptGroupId : 1,
    volumeGroupId : 1,
    displayName : ""
  }

  try {
    let isSpatializationEnabled: boolean = audioSpatializationManager.isSpatializationEnabled(deviceDescriptor);
    console.info(`AudioSpatializationManager isSpatializationEnabled: ${isSpatializationEnabled}`);
  } catch (err) {
    let error = err as BusinessError;
    console.error(`ERROR: ${error}`);
  }
  ```

## 订阅空间音频渲染效果的开关状态变化事件

系统应用开发者可以通过on('spatializationEnabledChangeForAnyDevice')接口订阅空间音频渲染效果的开关状态变化事件，回调包含AudioSpatialEnabledStateForDevice参数，AudioSpatialEnabledStateForDevice包含deviceDescriptor和enabled属性，其中deviceDescriptor为被改变设备的描述信息，enabled为true表示空间音频渲染被开启，false表示空间音频渲染被关闭。当通过setSpatializationEnabled接口成功地改变了任一设备的空间音频渲染开关状态时，回调将被触发。

  ```ts
  import { audio } from '@kit.AudioKit';

  audioSpatializationManager.on('spatializationEnabledChangeForAnyDevice', (audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
    console.info(`deviceDescriptor: ${audioSpatialEnabledStateForDevice.deviceDescriptor}`);
    console.info(`isSpatializationEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
  });
  ```

## 取消订阅空间音频渲染效果的开关状态变化事件

系统应用开发者可以通过off('spatializationEnabledChangeForAnyDevice')接口取消订阅空间音频渲染效果的开关状态变化事件。

  ```ts
  import { audio } from '@kit.AudioKit';
  audioSpatializationManager.off('spatializationEnabledChangeForAnyDevice');
  ```

## 开启/关闭指定设备的头动跟踪效果

系统应用开发者可以通过setHeadTrackingEnabled接口开启/关闭指定设备的头动跟踪效果，该接口需要传递两个参数：AudioDeviceDescriptor和enabled。

AudioDeviceDescriptor：用于指定音频设备。建议通过音频框架中其他接口来获取当前已连接设备或当前发声设备的AudioDeviceDescriptor。

enabled：布尔值类型，用于控制指定设备的头动跟踪开关。入参为true时为开启头动跟踪，入参为false时为关闭头动跟踪。

在使用此功能前，应用需要先申请权限`ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS`，申请方式请参考：system_basic等级应用申请权限的方式。

在开启头动跟踪时，需要先确保系统和指定设备都具有头动跟踪的能力，同时头动跟踪效果的生效依赖于空间音频渲染开关打开。

  ```ts
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let deviceDescriptor: audio.AudioDeviceDescriptor = {
    deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
    deviceType : audio.DeviceType.BLUETOOTH_A2DP,
    id : 1,
    name : "",
    address : "00:11:22:33:FF:EE",
    sampleRates : [44100],
    channelCounts : [2],
    channelMasks : [0],
    networkId : audio.LOCAL_NETWORK_ID,
    interruptGroupId : 1,
    volumeGroupId : 1,
    displayName : ""
  };
  let enable: boolean = true;

  audioSpatializationManager.setHeadTrackingEnabled(deviceDescriptor, enable).then(() => {
    console.info('Succeeded in setting head tracking enabled');
  }).catch((err: BusinessError) => {
    console.error(`Result ERROR: ${err}`);
  });
  ```

## 查询指定设备的头动跟踪效果开关状态

系统应用开发者可以通过isHeadTrackingEnabled接口查询指定设备的头动跟踪效果开关状态，该接口需要使用AudioDeviceDescriptor作为入参来指定设备，建议通过音频框架中其他接口来获取当前已连接设备或当前发声设备的AudioDeviceDescriptor。该接口返回为true表示头动跟踪开启，false表示头动跟踪关闭。返回值为setHeadTrackingEnabled接口中成功设置的指定设备头动跟踪开关状态，默认为关闭。此状态仅表示开关状态，实际是否生效还需依赖系统和指定设备是否支持头动跟踪，以及指定设备空间音频渲染开关是否打开。

  ```ts
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let deviceDescriptor: audio.AudioDeviceDescriptor = {
    deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
    deviceType : audio.DeviceType.BLUETOOTH_A2DP,
    id : 1,
    name : "",
    address : "00:11:22:33:FF:EE",
    sampleRates : [44100],
    channelCounts : [2],
    channelMasks : [0],
    networkId : audio.LOCAL_NETWORK_ID,
    interruptGroupId : 1,
    volumeGroupId : 1,
    displayName : ""
  };

  try {
    let isHeadTrackingEnabled: boolean = audioSpatializationManager.isHeadTrackingEnabled(deviceDescriptor);
    console.info(`AudioSpatializationManager isHeadTrackingEnabled: ${isHeadTrackingEnabled}`);
  } catch (err) {
    let error = err as BusinessError;
    console.error(`ERROR: ${error}`);
  }
  ```

## 订阅头动跟踪效果的开关状态变化事件

系统应用开发者可以通过on('headTrackingEnabledChangeForAnyDevice')接口订阅头动跟踪效果的开关状态变化事件，回调包含AudioSpatialEnabledStateForDevice参数，AudioSpatialEnabledStateForDevice包含deviceDescriptor和enabled属性，其中deviceDescriptor为被改变设备的描述信息，enabled为true表示头动跟踪被开启，false表示头动跟踪被关闭。当通过setHeadTrackingEnabled接口成功地改变了任一设备的头动跟踪开关状态时，回调将被触发。

  ```ts
  import { audio } from '@kit.AudioKit';

  audioSpatializationManager.on('headTrackingEnabledChangeForAnyDevice', (audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
    console.info(`deviceDescriptor: ${audioSpatialEnabledStateForDevice.deviceDescriptor}`);
    console.info(`isHeadTrackingEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
  });
  ```

## 取消订阅头动跟踪效果的开关状态变化事件

系统应用开发者可以通过off('headTrackingEnabledChangeForAnyDevice')接口取消订阅头动跟踪效果的开关状态变化事件。

  ```ts
  import { audio } from '@kit.AudioKit';
  audioSpatializationManager.off('headTrackingEnabledChangeForAnyDevice');
  ```

## 更新空间化设备状态

系统应用开发者可以通过updateSpatialDeviceState接口更新空间化设备状态，空间化设备状态包含设备的地址、是否具有空间音频渲染的能力、是否具有头动跟踪的能力和设备的形态类型。

在使用此功能前，应用需要先申请权限`ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS`，申请方式请参考：system_basic等级应用申请权限的方式。

空间化设备状态的具体信息可以参考AudioSpatialDeviceState。

  ```ts
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let spatialDeviceState: audio.AudioSpatialDeviceState = {
    address: "00:11:22:33:FF:EE",
    isSpatializationSupported: true,
    isHeadTrackingSupported: true,
    spatialDeviceType: audio.AudioSpatialDeviceType.SPATIAL_DEVICE_TYPE_IN_EAR_HEADPHONE
  };

  try {
    audioSpatializationManager.updateSpatialDeviceState(spatialDeviceState);
    console.info(`AudioSpatializationManager updateSpatialDeviceState success`);
  } catch (err) {
    let error = err as BusinessError;
    console.error(`ERROR: ${error}`);
  }
  ```

## 设置空间音频渲染场景类型

系统应用开发者可以通过setSpatializationSceneType接口设置空间音频渲染场景类型，可以选择默认场景、音乐场景、电影场景或有声读物场景，默认为默认场景。空间音频渲染场景类型的生效依赖空间音频渲染开关的打开。

在使用此功能前，应用需要先申请权限`ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS`，申请方式请参考：system_basic等级应用申请权限的方式。

空间音频渲染场景类型的具体信息可以参考AudioSpatializationSceneType。

  ```ts
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    audioSpatializationManager.setSpatializationSceneType(audio.AudioSpatializationSceneType.DEFAULT);
    console.info(`AudioSpatializationManager setSpatializationSceneType success`);
  } catch (err) {
    let error = err as BusinessError;
    console.error(`ERROR: ${error}`);
  }
  ```

## 查询空间音频渲染场景类型

系统应用开发者可以通过getSpatializationSceneType接口查询当前空间音频渲染场景类型。该接口将返回setSpatializationSceneType()接口中成功设置的值，默认为默认场景。

空间音频渲染场景类型AudioSpatializationSceneType的具体信息可以参考AudioSpatializationSceneType。

  ```ts
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    let spatializationSceneType: audio.AudioSpatializationSceneType = audioSpatializationManager.getSpatializationSceneType();
    console.info(`AudioSpatializationManager spatializationSceneType: ${spatializationSceneType}`);
  } catch (err) {
    let error = err as BusinessError;
    console.error(`ERROR: ${error}`);
  }
  ```

## 查询指定设备的自适应空间音频渲染效果开关状态

从API版本24开始，系统应用开发者可以通过isAdaptiveSpatialRenderingEnabled接口查询指定设备的自适应空间音频渲染效果开关状态。

入参需要使用AudioDeviceDescriptor来指定设备，建议通过音频框架的getActiveOutputDeviceDescriptors接口获取当前发声设备的AudioDeviceDescriptor。

返回值表示指定设备的自适应空间音频渲染开关状态：返回true表示自适应空间音频渲染已开启，返回false表示已关闭（默认为关闭）。该状态可通过setAdaptiveSpatialRenderingEnabled接口设置。

  ```ts
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  // 设备描述符，用于指定要查询的设备。实际使用时应通过音频框架接口获取真实设备信息，address等字段应使用真实值。
  let deviceDescriptor: audio.AudioDeviceDescriptor = {
    deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
    deviceType : audio.DeviceType.BLUETOOTH_A2DP,
    id : 1,
    name : "",
    address : "00:11:22:33:FF:EE",
    sampleRates : [44100],
    channelCounts : [2],
    channelMasks : [0],
    networkId : audio.LOCAL_NETWORK_ID,
    interruptGroupId : 1,
    volumeGroupId : 1,
    displayName : ""
  };

  try {
    // 查询指定设备的自适应空间音频渲染效果开关状态。
    let isAdaptiveSpatialRenderingEnabled: boolean = audioSpatializationManager.isAdaptiveSpatialRenderingEnabled(deviceDescriptor);
    console.info(`AudioSpatializationManager isAdaptiveSpatialRenderingEnabled: ${isAdaptiveSpatialRenderingEnabled}`);
  } catch (err) {
    let error = err as BusinessError;
    console.error(`ERROR: ${error}`);
  }
  ```

## 开启/关闭指定设备的自适应空间音频渲染效果

从API版本24开始，系统应用开发者可以通过setAdaptiveSpatialRenderingEnabled接口开启/关闭指定设备的自适应空间音频渲染效果。

在使用此功能前，应用需要先申请权限`ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS`，申请方式请参考：system_basic等级应用申请权限的方式。

在开启自适应空间音频渲染时，需要先确保系统和指定设备都具有空间音频渲染的能力。

  ```ts
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  // 设备描述符，用于指定要设置的设备。
  let deviceDescriptor: audio.AudioDeviceDescriptor = {
    deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
    deviceType : audio.DeviceType.BLUETOOTH_A2DP,
    id : 1,
    name : "",
    address : "00:11:22:33:FF:EE",
    sampleRates : [44100],
    channelCounts : [2],
    channelMasks : [0],
    networkId : audio.LOCAL_NETWORK_ID,
    interruptGroupId : 1,
    volumeGroupId : 1,
    displayName : ""
  };
  // 自适应空间音频渲染开关状态，true表示开启，false表示关闭。
  let enabled: boolean = true;

  // 开启指定设备的自适应空间音频渲染效果。
  audioSpatializationManager.setAdaptiveSpatialRenderingEnabled(deviceDescriptor, enabled).then(() => {
    console.info('Succeeded in setting adaptive spatial rendering enabled');
  }).catch((err: BusinessError) => {
    console.error(`Result ERROR: ${err}`);
  });
  ```

## 订阅自适应空间音频渲染效果的开关状态变化事件

从API版本24开始，系统应用开发者可以通过onAdaptiveSpatialRenderingEnabledChangeForAnyDevice接口订阅自适应空间音频渲染效果的开关状态变化事件。

回调包含AudioSpatialEnabledStateForDevice参数，其中deviceDescriptor为被改变设备的描述信息，enabled为true表示自适应空间音频渲染被开启，false表示自适应空间音频渲染被关闭。

当通过setAdaptiveSpatialRenderingEnabled接口成功地改变了任一设备的自适应空间音频渲染开关状态时，回调将被触发。

  ```ts
  import { audio } from '@kit.AudioKit';

  // 订阅自适应空间音频渲染效果的开关状态变化事件。
  audioSpatializationManager.onAdaptiveSpatialRenderingEnabledChangeForAnyDevice((audioSpatialEnabledStateForDevice: audio.AudioSpatialEnabledStateForDevice) => {
    console.info(`deviceDescriptor: ${audioSpatialEnabledStateForDevice.deviceDescriptor}`);
    console.info(`isAdaptiveSpatialRenderingEnabled: ${audioSpatialEnabledStateForDevice.enabled}`);
  });
  ```

## 取消订阅自适应空间音频渲染效果的开关状态变化事件

从API版本24开始，系统应用开发者可以通过offAdaptiveSpatialRenderingEnabledChangeForAnyDevice接口取消订阅自适应空间音频渲染效果的开关状态变化事件。

  ```ts
  import { audio } from '@kit.AudioKit';
  // 取消订阅自适应空间音频渲染效果的开关状态变化事件。
  audioSpatializationManager.offAdaptiveSpatialRenderingEnabledChangeForAnyDevice();
  ```

## 获取当前空间音频源类型

从API版本24开始，系统应用开发者可以通过getCurrentSpatialAudioSourceType接口获取当前空间音频源类型。该接口返回当前播放的音频流类型，包括立体声、Audio Vivid或多声道。

空间音频源类型的具体信息可以参考SpatialAudioSourceType。

  ```ts
  import { audio } from '@kit.AudioKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    // 获取当前空间音频源类型，返回当前播放的音频流类型。
    let spatialAudioSourceType: audio.SpatialAudioSourceType = audioSpatializationManager.getCurrentSpatialAudioSourceType();
    console.info(`AudioSpatializationManager spatialAudioSourceType: ${spatialAudioSourceType}`);
  } catch (err) {
    let error = err as BusinessError;
    console.error(`ERROR: ${error}`);
  }
  ```

## 订阅空间音频源类型变化事件

从API版本24开始，系统应用开发者可以通过onSpatialAudioSourceTypeChange接口订阅空间音频源类型变化事件，回调包含SpatialAudioSourceType参数，表示变化后的空间音频源类型。当开始播放不同类型的音频流时，空间音频源类型会自动更新并触发回调。

  ```ts
  import { audio } from '@kit.AudioKit';

  // 订阅空间音频源类型变化事件。
  audioSpatializationManager.onSpatialAudioSourceTypeChange((spatialAudioSourceType: audio.SpatialAudioSourceType) => {
    console.info(`spatialAudioSourceType: ${spatialAudioSourceType}`);
  });
  ```

## 取消订阅空间音频源类型变化事件

从API版本24开始，系统应用开发者可以通过offSpatialAudioSourceTypeChange接口取消订阅空间音频源类型变化事件。

  ```ts
  import { audio } from '@kit.AudioKit';

  // 取消订阅空间音频源类型变化事件。
  audioSpatializationManager.offSpatialAudioSourceTypeChange();
  ```