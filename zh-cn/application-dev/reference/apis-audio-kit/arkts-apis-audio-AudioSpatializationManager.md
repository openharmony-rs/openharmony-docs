# Interface (AudioSpatializationManager)

> **说明：**
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 18开始支持。

空间音频管理。

在使用AudioSpatializationManager的接口之前，需先通过[getSpatializationManager](arkts-apis-audio-AudioManager.md#getspatializationmanager18)获取AudioSpatializationManager实例。

## 导入模块

```ts
import { audio } from '@kit.AudioKit';
```

## isSpatializationEnabledForCurrentDevice<sup>18+</sup>

isSpatializationEnabledForCurrentDevice(): boolean

获取当前设备空间音频渲染是否开启。同步返回结果。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                   | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| boolean | 当前设备空间音频渲染是否开启。true表示开启，false表示未开启。 |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

let isSpatializationEnabledForCurrentDevice: boolean = audioSpatializationManager.isSpatializationEnabledForCurrentDevice();
console.info(`AudioSpatializationManager isSpatializationEnabledForCurrentDevice: ${isSpatializationEnabledForCurrentDevice}`);
```

## on('spatializationEnabledChangeForCurrentDevice')<sup>18+</sup>

on(type: 'spatializationEnabledChangeForCurrentDevice', callback: Callback<boolean\>): void

监听当前设备空间音频渲染开关状态变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onSpatializationEnabledChangeForCurrentDevice](#onSpatializationEnabledChangeForCurrentDevice22)。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                                           |
| :------- | :--------------------------------------------------- | :--- |:---------------------------------------------|
| type     | string | 是   | 事件回调类型，支持的事件为'spatializationEnabledChangeForCurrentDevice'，当空间音频渲染开关状态变化时，触发该事件。 |
| callback | Callback<boolean\> | 是   | 回调函数。返回true表示打开空间音频渲染状态；返回false表示关闭空间音频渲染状态。   |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

audioSpatializationManager.on('spatializationEnabledChangeForCurrentDevice', (isSpatializationEnabledForCurrentDevice: boolean) => {
  console.info(`isSpatializationEnabledForCurrentDevice: ${isSpatializationEnabledForCurrentDevice}`);
});
```

## onSpatializationEnabledChangeForCurrentDevice<sup>23+</sup>

onSpatializationEnabledChangeForCurrentDevice(callback: Callback<boolean\>): void

监听当前设备空间音频渲染开关状态变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('spatializationEnabledChangeForCurrentDevice')](#onspatializationEnabledChangeForCurrentDevice18)。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                                           |
| :------- | :--------------------------------------------------- | :--- |:---------------------------------------------|
| callback | Callback<boolean\> | 是   | 回调函数。返回true表示打开空间音频渲染状态；返回false表示关闭空间音频渲染状态。   |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

audioSpatializationManager.onSpatializationEnabledChangeForCurrentDevice((isSpatializationEnabledForCurrentDevice: boolean) => {
  console.info(`isSpatializationEnabledForCurrentDevice: ${isSpatializationEnabledForCurrentDevice}`);
});
```

## off('spatializationEnabledChangeForCurrentDevice')<sup>18+</sup>

off(type: 'spatializationEnabledChangeForCurrentDevice', callback?: Callback<boolean\>): void

取消监听当前设备空间音频渲染开关状态变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offSpatializationEnabledChangeForCurrentDevice](#offSpatializationEnabledChangeForCurrentDevice22)。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名   | 类型                                                | 必填 | 说明                                       |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------ |
| type     | string | 是   | 事件回调类型，支持的事件为'spatializationEnabledChangeForCurrentDevice'，当取消订阅当前设备空间音频渲染开关状态变化事件时，触发该事件。 |
| callback | Callback<boolean\> | 否   | 回调函数。返回true表示打开空间音频渲染状态；返回false表示关闭空间音频渲染状态。   |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';
audioSpatializationManager.off('spatializationEnabledChangeForCurrentDevice');
```

## offSpatializationEnabledChangeForCurrentDevice<sup>23+</sup>

offSpatializationEnabledChangeForCurrentDevice(callback?: Callback<boolean\>): void

取消监听当前设备空间音频渲染开关状态变化事件。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('spatializationEnabledChangeForCurrentDevice')](#offspatializationEnabledChangeForCurrentDevice18)。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                | 必填 | 说明                                       |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------ |
| callback | Callback<boolean\> | 否   | 回调函数。返回true表示打开空间音频渲染状态；返回false表示关闭空间音频渲染状态。   |

**错误码：**

以下错误码的详细介绍请参见[Audio错误码](errorcode-audio.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**示例：**

```ts
import { audio } from '@kit.AudioKit';
audioSpatializationManager.offSpatializationEnabledChangeForCurrentDevice();
```