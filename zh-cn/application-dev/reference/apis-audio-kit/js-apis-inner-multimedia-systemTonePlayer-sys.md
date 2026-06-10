# systemTonePlayer (系统提示音播放器)(系统接口)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

系统提示音播放器提供了短信提示音、通知提示音的播放、配置、获取信息等功能。

systemTonePlayer需要和[@ohos.multimedia.systemSoundManager](js-apis-systemSoundManager-sys.md)配合使用，才能完成管理系统提示音的功能。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块接口为系统接口。

## 导入模块

```ts
import { systemSoundManager } from '@kit.AudioKit';
```

## SystemToneOptions

提示音参数选项。

**系统接口：** 该接口为系统接口。

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

| 名称        | 类型    | 只读 | 可选 | 说明                                          |
| ----------- | ------- | ---- | ---- | --------------------------------------------- |
| muteAudio   | boolean | 否   | 是   | 提示音是否静音，true表示静音，false表示不静音。   |
| muteHaptics | boolean | 否   | 是   | 提示音时是否振动，true表示关闭振动，false表示开启振动。 |

## SystemTonePlayer

系统提示音播放器提供了短信提示音、通知提示音的播放、配置、获取信息等功能。在调用SystemTonePlayer的接口前，需要先通过[getSystemTonePlayer](js-apis-systemSoundManager-sys.md#getsystemtoneplayer11)创建实例。

### getTitle

getTitle(): Promise&lt;string&gt;

获取提示音标题。使用Promise异步回调。

**系统接口：** 该接口为系统接口。

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型    | 说明                                  |
| ------- | ------------------------------------- |
| Promise&lt;string&gt; | Promise对象，返回获取的系统提示音标题。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Media错误码](../apis-media-kit/errorcode-media.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 202      | Caller is not a system application. |
| 5400103  | I/O error.                          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemTonePlayer.getTitle().then((value: string) => {
  console.info('Succeeded in doing getTitle.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getTitle. Code: ${err.code}, message: ${err.message}`);
});
```

### prepare

prepare(): Promise&lt;void&gt;

准备播放提示音。使用Promise异步回调。

**系统接口：** 该接口为系统接口。

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型    | 说明                            |
| ------- | ------------------------------- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Media错误码](../apis-media-kit/errorcode-media.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 202      | Caller is not a system application. |
| 5400102  | Operation not allowed.              |
| 5400103  | I/O error.                          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemTonePlayer.prepare().then(() => {
  console.info('Succeeded in doing prepare.');
}).catch((err: BusinessError) => {
  console.error(`Failed to prepare. Code: ${err.code}, message: ${err.message}`);
});
```

### start

ArkTS-Dyn: start(toneOptions?: SystemToneOptions): Promise&lt;number&gt;

ArkTS-Sta: start(toneOptions?: SystemToneOptions): Promise&lt;int&gt;

开始播放提示音。使用Promise异步回调。

**系统接口：** 该接口为系统接口。

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**需要权限：** ohos.permission.VIBRATE

**参数：**

| 参数名      | 类型                                    | 必填 | 说明             |
| ----------- | --------------------------------------- | ---- | ---------------- |
| toneOptions | [SystemToneOptions](#systemtoneoptions) | 否   | 系统提示音选项。 |

**返回值：**

| 类型    | 说明                      |
| ------- | ------------------------- |
| ArkTS-Dyn: Promise&lt;number&gt;<br>ArkTS-Sta: Promise&lt;int&gt; | Promise对象，返回streamID。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Media错误码](../apis-media-kit/errorcode-media.md)。

| 错误码ID | 错误信息                                                                                                    |
| -------- | ----------------------------------------------------------------------------------------------------------- |
| 201      | Permission denied.                                                                                          |
| 202      | Caller is not a system application.                                                                         |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400102  | Operation not allowed.                                                                                      |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class SystemToneOptions {
  muteAudio: boolean = false;
  muteHaptics: boolean = false;
}
let systemToneOptions: SystemToneOptions = {muteAudio: true, muteHaptics: false};

systemTonePlayer.start(systemToneOptions).then((value) => {
  console.info('Succeeded in doing start.');
}).catch((err: BusinessError) => {
  console.error(`Failed to start. Code: ${err.code}, message: ${err.message}`);
});
```

### stop

ArkTS-Dyn: stop(id: number): Promise&lt;void&gt;

ArkTS-Sta: stop(id: int): Promise&lt;void&gt;

停止播放提示音。使用Promise异步回调。

**系统接口：** 该接口为系统接口。

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                      |
| ------ | ------ | ---- | ------------------------- |
| id     | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | Promise对象，返回streamID。 |

**返回值：**

| 类型    | 说明                                |
| ------- | ----------------------------------- |
| Promise&lt;void&gt; | Promise回调返回停止播放成功或失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Media错误码](../apis-media-kit/errorcode-media.md)。

| 错误码ID | 错误信息                                                                                                    |
| -------- | ----------------------------------------------------------------------------------------------------------- |
| 202      | Caller is not a system application.                                                                         |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400102  | Operation not allowed.                                                                                      |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let streamID = 0; // streamID为start方法返回的streamID,此处只做初始化。
systemTonePlayer.stop(streamID).then(() => {
  console.info('Succeeded in doing stop.');
}).catch((err: BusinessError) => {
  console.error(`Failed to stop. Code: ${err.code}, message: ${err.message}`);
});
```

### release

release(): Promise&lt;void&gt;

释放提示音播放器。使用Promise异步回调。

**系统接口：** 该接口为系统接口。

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型    | 说明                            |
| ------- | ------------------------------- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 202      | Caller is not a system application. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemTonePlayer.release().then(() => {
  console.info('Succeeded in doing release.');
}).catch((err: BusinessError) => {
  console.error(`Failed to release. Code: ${err.code}, message: ${err.message}`);
});
```

### setAudioVolumeScale<sup>13+</sup>

ArkTS-Dyn: setAudioVolumeScale(scale: number): void

ArkTS-Sta: setAudioVolumeScale(scale: double): void

设置音频音量大小，无返回结果。

**系统接口：** 该接口为系统接口。

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                                 |
| ------ | ------ | ---- | ------------------------------------ |
| scale  | ArkTS-Dyn: number<br>ArkTS-Sta: double | 是   | 音频音量大小，必须在[0, 1]之间取值。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)、[Media错误码](../apis-media-kit/errorcode-media.md)和[Ringtone错误码](./errorcode-audio-ringtone-sys.md)。

| 错误码ID | 错误信息                                                                                                    |
| -------- | ----------------------------------------------------------------------------------------------------------- |
| 202      | Caller is not a system application.                                                                         |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400102  | Operation not allowed.                                                                                      |
| 20700002 | Parameter check error. For example, value is outside [0,1]. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let scale = 0.5;
try {
  systemTonePlayer.setAudioVolumeScale(scale);
  console.info('Succeeded in doing setAudioVolumeScale.');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to setAudioVolumeScale. Code: ${error.code}, message: ${error.message}`);
}
```

### getAudioVolumeScale<sup>13+</sup>

ArkTS-Dyn: getAudioVolumeScale(): number

ArkTS-Sta: getAudioVolumeScale(): double

获取当前音频音量大小，同步返回当前音量。

**系统接口：** 该接口为系统接口。

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型   | 说明         |
| ------ | ------------ |
| ArkTS-Dyn: number<br>ArkTS-Sta: double | 当前音频音量，音量范围为[0, 1]。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 202      | Caller is not a system application. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let scale = systemTonePlayer.getAudioVolumeScale();
  console.info('Succeeded in doing getAudioVolumeScale.');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getAudioVolumeScale. Code: ${error.code}, message: ${error.message}`);
}
```

### getSupportedHapticsFeatures<sup>13+</sup>

getSupportedHapticsFeatures(): Promise&lt;Array&lt;systemSoundManager.ToneHapticsFeature&gt;&gt;

获取当前支持的振动风格。使用Promise异步回调。

**系统接口：** 该接口为系统接口。

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                                                                                                          | 说明                                                                                                                  |
|-----------------------------------------------------------------------------------------------------------------------------| --------------------------------------------------------------------------------------------------------------------- |
| Promise&lt;Array&lt;[systemSoundManager.ToneHapticsFeature](js-apis-systemSoundManager-sys.md#tonehapticsfeature13)&gt;&gt; | Promise对象，返回当前支持的振动风格。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Ringtone错误码](./errorcode-audio-ringtone-sys.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 202      | Caller is not a system application. |
| 20700003 | Unsupported operation.              |

**示例：**

```ts
systemTonePlayer.getSupportedHapticsFeatures().then((features: Array<systemSoundManager.ToneHapticsFeature>) => {
  console.info('Succeeded in doing getSupportedHapticsFeatures.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getSupportedHapticsFeatures. Code: ${err.code}, message: ${err.message}`);
});
```

### setHapticsFeature<sup>13+</sup>

setHapticsFeature(hapticsFeature: systemSoundManager.ToneHapticsFeature): void

设置播放铃音时的振动风格。

调用本接口前，应该先调用[getSupportedHapticsFeatures](#getsupportedhapticsfeatures13)查询支持的振动风格，如果设置不支持的振动风格，则设置失败。

**系统接口：** 该接口为系统接口。

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名         | 类型                                                                                              | 必填 | 说明             |
| -------------- |-------------------------------------------------------------------------------------------------| ---- | ---------------- |
| hapticsFeature | [systemSoundManager.ToneHapticsFeature](js-apis-systemSoundManager-sys.md#tonehapticsfeature13) | 是   | 振动风格。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)、[Media错误码](../apis-media-kit/errorcode-media.md)和[Ringtone错误码](./errorcode-audio-ringtone-sys.md)。

| 错误码ID | 错误信息                                                                                                    |
| -------- | ----------------------------------------------------------------------------------------------------------- |
| 202      | Caller is not a system application.                                                                         |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400102  | Operation not allowed.                                                                                      |
| 20700003 | Unsupported operation.                                                                                      |

**示例：**

```ts
systemTonePlayer.getSupportedHapticsFeatures().then((features: Array<systemSoundManager.ToneHapticsFeature>) => {
  console.info('Succeeded in doing getSupportedHapticsFeatures.');
  if (features.length > 0) {
    let feature: systemSoundManager.ToneHapticsFeature = features[0];
    systemTonePlayer.setHapticsFeature(feature);
    console.info('Succeeded in doing setHapticsFeature.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to getSupportedHapticsFeatures. Code: ${err.code}, message: ${err.message}`);
});
```

### getHapticsFeature<sup>13+</sup>

getHapticsFeature(): systemSoundManager.ToneHapticsFeature

获取播放铃音时的振动风格，同步返回振动风格枚举值。

**系统接口：** 该接口为系统接口。

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                                                                              | 说明     |
|-------------------------------------------------------------------------------------------------| -------- |
| [systemSoundManager.ToneHapticsFeature](js-apis-systemSoundManager-sys.md#tonehapticsfeature13) | 振动风格。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Ringtone错误码](./errorcode-audio-ringtone-sys.md)。


| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 202      | Caller is not a system application. |
| 20700003 | Unsupported operation.              |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let feature: systemSoundManager.ToneHapticsFeature = systemTonePlayer.getHapticsFeature();
  console.info('Succeeded in doing getHapticsFeature.');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getHapticsFeature. Code: ${error.code}, message: ${error.message}`);
}
```

### on('playFinished')<sup>18+</sup>

on(type: 'playFinished', streamId: number, callback: Callback\<number>): void

监听铃音播放完成事件（当铃音播放完成时触发）。使用callback异步回调。

监听对象为传入的streamId对应音频流。当streamId传入0时，监听本播放器对应的所有音频流。

**系统接口：** 该接口为系统接口。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onPlayFinished](#onplayfinished23)。

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名   | 类型                     | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | --------------------------------------------------------------- |
| type     | string                  | 是   | 事件回调类型，支持的事件为'playFinished'，当铃音播放完成时，触发该事件。 |
| streamId | number                  | 是   | 监听对象为指定streamId对应的音频流，streamId通过[start](#start)获取。当streamId传入0时，可监听当前播放器对应的所有音频流。 |
| callback | Callback\<number>  | 是   | 'playFinished'的回调方法。返回播放完成的音频流的streamId。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Ringtone错误码](./errorcode-audio-ringtone-sys.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202      | Not system App.  |
| 20700002 | Parameter check error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 监听所有音频流的结束事件。
systemTonePlayer.on('playFinished', 0, (streamId: number) => {
  console.info(`Receive the callback of playFinished, streamId: ${streamId}.`);
});

// 监听指定音频流的结束事件。
systemTonePlayer.start().then((value: number) => {
  systemTonePlayer.on('playFinished', value, (streamId: number) => {
    console.info(`Receive the callback of playFinished, streamId: ${streamId}.`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to start system tone player. ${err}`);
});
```

### onPlayFinished<sup>23+</sup>

onPlayFinished(streamId: int, callback: Callback\<int>): void

监听铃音播放完成事件（当铃音播放完成时触发）。使用callback异步回调。

监听对象为传入的streamId对应音频流。当streamId传入0时，监听本播放器对应的所有音频流。

**系统接口：** 该接口为系统接口。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('playFinished')](#onplayfinished18)。

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                     | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | --------------------------------------------------------------- |
| streamId | int                  | 是   | 监听对象为指定streamId对应的音频流，streamId通过[start](#start)获取。当streamId传入0时，可监听当前播放器对应的所有音频流。 |
| callback | Callback\<int>  | 是   | 'playFinished'的回调方法。返回播放完成的音频流的streamId。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Ringtone错误码](./errorcode-audio-ringtone-sys.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202      | Not system App.  |
| 20700002 | Parameter check error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 监听所有音频流的结束事件。
systemTonePlayer.onPlayFinished(0, (streamId) => {
  console.info(`Receive the callback of playFinished, streamId: ${streamId}.`);
});

// 监听指定音频流的结束事件。
systemTonePlayer.start().then((value) => {
  systemTonePlayer.onPlayFinished(value, (streamId) => {
    console.info(`Receive the callback of playFinished, streamId: ${streamId}.`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to start system tone player. ${err}`);
});
```

### off('playFinished')<sup>18+</sup>

off(type: 'playFinished', callback?: Callback\<number>): void

取消监听铃音播放完成事件。使用callback异步回调。

**系统接口：** 该接口为系统接口。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offPlayFinished](#offplayfinished23)。

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名 | 类型   | 必填 | 说明                                              |
| ----- | ----- | ---- | ------------------------------------------------ |
| type   | string | 是   | 事件回调类型，支持的事件为'playFinished'，当取消监听铃音播放完成事件时，触发该事件。 |
| callback | Callback\<number>    | 否   | 回调函数，返回结束事件的音频流的streamId。不填入此参数时，会取消该事件的所有监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Ringtone错误码](./errorcode-audio-ringtone-sys.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202      | Not system App.  |
| 20700002 | Parameter check error. |

**示例：**

```ts
// 取消该事件的所有监听。
systemTonePlayer.off('playFinished');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let playFinishedCallback = (streamId: number) => {
  console.info(`Receive the callback of playFinished, streamId: ${streamId}.`);
};

systemTonePlayer.on('playFinished', 0, playFinishedCallback);

systemTonePlayer.off('playFinished', playFinishedCallback);
```

### offPlayFinished<sup>23+</sup>

offPlayFinished(callback?: Callback\<int>): void

取消监听铃音播放完成事件。

**系统接口：** 该接口为系统接口。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('playFinished')](#offplayfinished18)。

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                     | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | --------------------------------------------------------------- |
| callback | Callback\<int>  | 否   | 'playFinished'的回调方法。不填入此参数时，会取消该事件的所有监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Ringtone错误码](./errorcode-audio-ringtone-sys.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202      | Not system App.  |
| 20700002 | Parameter check error. |

**示例：**

```ts
// 取消该事件的所有监听。
systemTonePlayer.offPlayFinished();

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let playFinishedCallback = (streamId) => {
  console.info(`Receive the callback of playFinished, streamId: ${streamId}.`);
};

systemTonePlayer.onPlayFinished(0, playFinishedCallback);

systemTonePlayer.offPlayFinished(playFinishedCallback);
```

### on('error')<sup>18+</sup>

on(type: 'error', callback: ErrorCallback): void

监听铃音播放过程中的错误事件（当铃音播放过程中发生错误时触发）。使用callback异步回调。

**系统接口：** 该接口为系统接口。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onError](#onerror23)。

**系统能力**：SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名   | 类型          | 必填 | 说明                                 |
| -------- | ------------- | ---- | ------------------------------------ |
| type     | string        | 是   | 事件回调类型，支持的事件为'error'，当铃音播放过程中发生错误时，触发该事件。 |
| callback | ErrorCallback | 是   | 回调函数，返回错误码和错误信息。错误码请参考AVPlayer的[on('error')](../apis-media-kit/arkts-apis-media-AVPlayer.md#onerror9)。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Ringtone错误码](./errorcode-audio-ringtone-sys.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202      | Not system App.  |
| 20700002 | Parameter check error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemTonePlayer.on('error', (err: BusinessError) => {
  console.info(`Succeeded in using on function. code: ${err.code}, message: ${err.message}`);
});
```

### onError<sup>23+</sup>

onError(callback: ErrorCallback): void

监听铃音播放过程中的错误事件（当铃音播放过程中发生错误时触发）。使用callback异步回调。

**系统接口：** 该接口为系统接口。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('error')](#onerror18)。

**系统能力**：SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型          | 必填 | 说明                                 |
| -------- | ------------- | ---- | ------------------------------------ |
| callback | ErrorCallback | 是   | 回调函数，返回错误码和错误信息。错误码请参考AVPlayer的[on('error')](../apis-media-kit/arkts-apis-media-AVPlayer.md#onerror9)。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Ringtone错误码](./errorcode-audio-ringtone-sys.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202      | Not system App.  |
| 20700002 | Parameter check error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemTonePlayer.onError((err: BusinessError) => {
  console.info(`Succeeded in using onError function. code: ${err.code}, message: ${err.message}`);
});
```

### off('error')<sup>18+</sup>

off(type: 'error', callback?: ErrorCallback): void

取消监听铃音播放过程中的错误事件。使用callback异步回调。

**系统接口：** 该接口为系统接口。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offError](#offerror23)。

**系统能力**：SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名   | 类型          | 必填 | 说明                                 |
| -------- | ------------- | ---- | ------------------------------------ |
| type     | string        | 是   | 事件回调类型，支持的事件为'error'，当取消监听铃音播放过程中的错误事件时，触发该事件。 |
| callback | ErrorCallback | 否   | 回调函数，返回错误码和错误信息。不填入此参数时，会取消该事件的所有监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Ringtone错误码](./errorcode-audio-ringtone-sys.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202      | Not system App.  |
| 20700002 | Parameter check error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 取消该事件的所有监听。
systemTonePlayer.off('error');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let callback = (err: BusinessError) => {
  console.info(`Succeeded in using on or off function. code: ${err.code}, message: ${err.message}`);
};

systemTonePlayer.on('error', callback);

systemTonePlayer.off('error', callback);
```

### offError<sup>23+</sup>

offError(callback?: ErrorCallback): void

取消监听铃音播放过程中的错误事件。

**系统接口：** 该接口为系统接口。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('error')](#offerror18)。

**系统能力**：SystemCapability.Multimedia.SystemSound.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型          | 必填 | 说明                                 |
| -------- | ------------- | ---- | ------------------------------------ |
| callback | ErrorCallback | 否   | 回调函数，返回错误码和错误信息。不填入此参数时，会取消该事件的所有监听。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Ringtone错误码](./errorcode-audio-ringtone-sys.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 202      | Not system App.  |
| 20700002 | Parameter check error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 取消该事件的所有监听。
systemTonePlayer.offError();

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let callback = (err: BusinessError) => {
  console.info(`Succeeded in using on or off function. code: ${err.code}, message: ${err.message}`);
};

systemTonePlayer.onError(callback);

systemTonePlayer.offError(callback);
```