# SystemTonePlayer（系统接口）

系统提示音播放器提供了短信提示音、通知提示音的播放、配置、获取信息等功能。在调用SystemTonePlayer的接口前，需要先通过 [getSystemTonePlayer](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#getSystemTonePlayer) 创建实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface SystemTonePlayer--><!--Device-unnamed-export declare interface SystemTonePlayer-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

## getAudioVolumeScale

```TypeScript
getAudioVolumeScale(): double
```

获取当前音频音量大小，同步返回当前音量。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemTonePlayer-getAudioVolumeScale(): double--><!--Device-SystemTonePlayer-getAudioVolumeScale(): double-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 当前音频音量，音量范围为[0, 1]。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let scale = systemTonePlayer.getAudioVolumeScale();
  console.info('Succeeded in doing getAudioVolumeScale.');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getAudioVolumeScale. Code: ${error.code}, message: ${error.message}`);
}
```

## getHapticsFeature

```TypeScript
getHapticsFeature(): systemSoundManager.ToneHapticsFeature
```

获取播放铃音时的振动风格，同步返回振动风格枚举值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemTonePlayer-getHapticsFeature(): systemSoundManager.ToneHapticsFeature--><!--Device-SystemTonePlayer-getHapticsFeature(): systemSoundManager.ToneHapticsFeature-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| systemSoundManager.ToneHapticsFeature | 振动风格。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [20700003](../errorcode-audio-ringtone-sys.md#20700003-操作不支持) | Unsupported operation. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let feature: systemSoundManager.ToneHapticsFeature = systemTonePlayer.getHapticsFeature();
  console.info('Succeeded in doing getHapticsFeature.');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getHapticsFeature. Code: ${error.code}, message: ${error.message}`);
}
```

## getSupportedHapticsFeatures

```TypeScript
getSupportedHapticsFeatures(): Promise<Array<systemSoundManager.ToneHapticsFeature>>
```

获取当前支持的振动风格。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemTonePlayer-getSupportedHapticsFeatures(): Promise<Array<systemSoundManager.ToneHapticsFeature>>--><!--Device-SystemTonePlayer-getSupportedHapticsFeatures(): Promise<Array<systemSoundManager.ToneHapticsFeature>>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;systemSoundManager.ToneHapticsFeature&gt;&gt; | Promise对象，返回当前支持的振动风格。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [20700003](../errorcode-audio-ringtone-sys.md#20700003-操作不支持) | Unsupported operation. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## 示例

```TypeScript
systemTonePlayer.getSupportedHapticsFeatures().then((features: Array<systemSoundManager.ToneHapticsFeature>) => {
  console.info('Succeeded in doing getSupportedHapticsFeatures.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getSupportedHapticsFeatures. Code: ${err.code}, message: ${err.message}`);
});
```

## getTitle

```TypeScript
getTitle(): Promise<string>
```

获取提示音标题。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemTonePlayer-getTitle(): Promise<string>--><!--Device-SystemTonePlayer-getTitle(): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回获取的系统提示音标题。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

systemTonePlayer.getTitle().then((value: string) => {
  console.info('Succeeded in doing getTitle.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getTitle. Code: ${err.code}, message: ${err.message}`);
});
```

## offError

```TypeScript
offError(callback?: ErrorCallback): void
```

取消监听铃音播放过程中的错误事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemTonePlayer-offError(callback?: ErrorCallback): void--><!--Device-SystemTonePlayer-offError(callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 否 | Error callback while receiving the error event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [20700002](../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
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

## offPlayFinished

```TypeScript
offPlayFinished(callback?: Callback<int>): void
```

取消监听铃音播放完成事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemTonePlayer-offPlayFinished(callback?: Callback<int>): void--><!--Device-SystemTonePlayer-offPlayFinished(callback?: Callback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int&gt; | 否 | Callback used to obtain the finished event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [20700002](../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
// 取消该事件的所有监听。
systemTonePlayer.offPlayFinished();

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let playFinishedCallback = (streamId) => {
  console.info(`Receive the callback of playFinished, streamId: ${streamId}.`);
};

systemTonePlayer.onPlayFinished(0, playFinishedCallback);

systemTonePlayer.offPlayFinished(playFinishedCallback);
```

## off_error

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

取消监听铃音播放过程中的错误事件。使用callback异步回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-SystemTonePlayer-off(type: 'error', callback?: ErrorCallback): void--><!--Device-SystemTonePlayer-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 事件回调类型，支持的事件为'error'，当取消监听铃音播放过程中的错误事件时，触发该事件。 |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 否 | 回调函数，返回错误码和错误信息。不填入此参数时，会取消该事件的所有监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [20700002](../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
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

## off_playFinished

```TypeScript
off(type: 'playFinished', callback?: Callback<int>): void
```

取消监听铃音播放完成事件。使用callback异步回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-SystemTonePlayer-off(type: 'playFinished', callback?: Callback<int>): void--><!--Device-SystemTonePlayer-off(type: 'playFinished', callback?: Callback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playFinished' | 是 | 事件回调类型，支持的事件为'playFinished'，当取消监听铃音播放完成事件时，触发该事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int&gt; | 否 | 回调函数，返回结束事件的音频流的streamId。不填入此参数时，会取消该事件的所有监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [20700002](../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
// 取消该事件的所有监听。
systemTonePlayer.off('playFinished');

// 同一监听事件中，on方法和off方法传入callback参数一致，off方法取消对应on方法订阅的监听。
let playFinishedCallback = (streamId: number) => {
  console.info(`Receive the callback of playFinished, streamId: ${streamId}.`);
};

systemTonePlayer.on('playFinished', 0, playFinishedCallback);

systemTonePlayer.off('playFinished', playFinishedCallback);
```

## onError

```TypeScript
onError(callback: ErrorCallback): void
```

监听铃音播放过程中的错误事件（当铃音播放过程中发生错误时触发）。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemTonePlayer-onError(callback: ErrorCallback): void--><!--Device-SystemTonePlayer-onError(callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 是 | Error callback while receiving the error event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [20700002](../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

systemTonePlayer.onError((err: BusinessError) => {
  console.info(`Succeeded in using onError function. code: ${err.code}, message: ${err.message}`);
});
```

## onPlayFinished

```TypeScript
onPlayFinished(streamId: int, callback: Callback<int>): void
```

监听铃音播放完成事件（当铃音播放完成时触发）。使用callback异步回调。 监听对象为传入的streamId对应音频流。当streamId传入0时，监听本播放器对应的所有音频流。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemTonePlayer-onPlayFinished(streamId: int, callback: Callback<int>): void--><!--Device-SystemTonePlayer-onPlayFinished(streamId: int, callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamId | int | 是 | Stream id, received from start(). |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int&gt; | 是 | Callback used to obtain the finished event. The callback info is the stream id that is finished. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [20700002](../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
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

## on_error

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

监听铃音播放过程中的错误事件（当铃音播放过程中发生错误时触发）。使用callback异步回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-SystemTonePlayer-on(type: 'error', callback: ErrorCallback): void--><!--Device-SystemTonePlayer-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 事件回调类型，支持的事件为'error'，当铃音播放过程中发生错误时，触发该事件。 |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 是 | 回调函数，返回错误码和错误信息。错误码请参考AVPlayer的 on('error')。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [20700002](../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

systemTonePlayer.on('error', (err: BusinessError) => {
  console.info(`Succeeded in using on function. code: ${err.code}, message: ${err.message}`);
});
```

## on_playFinished

```TypeScript
on(type: 'playFinished', streamId: int, callback: Callback<int>): void
```

监听铃音播放完成事件（当铃音播放完成时触发）。使用callback异步回调。 监听对象为传入的streamId对应音频流。当streamId传入0时，监听本播放器对应的所有音频流。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-SystemTonePlayer-on(type: 'playFinished', streamId: int, callback: Callback<int>): void--><!--Device-SystemTonePlayer-on(type: 'playFinished', streamId: int, callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playFinished' | 是 | 事件回调类型，支持的事件为'playFinished'，当铃音播放完成时，触发该事件。 |
| streamId | int | 是 | 监听对象为指定streamId对应的音频流，streamId通过[start](#start)获取。 当streamId传入0时，可监听当前播放器对应的所有音频流。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int&gt; | 是 | 'playFinished'的回调方法。返回播放完成的音频流的streamId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [20700002](../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
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

## prepare

```TypeScript
prepare(): Promise<void>
```

准备播放提示音。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemTonePlayer-prepare(): Promise<void>--><!--Device-SystemTonePlayer-prepare(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

systemTonePlayer.prepare().then(() => {
  console.info('Succeeded in doing prepare.');
}).catch((err: BusinessError) => {
  console.error(`Failed to prepare. Code: ${err.code}, message: ${err.message}`);
});
```

## release

```TypeScript
release(): Promise<void>
```

释放提示音播放器。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemTonePlayer-release(): Promise<void>--><!--Device-SystemTonePlayer-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

systemTonePlayer.release().then(() => {
  console.info('Succeeded in doing release.');
}).catch((err: BusinessError) => {
  console.error(`Failed to release. Code: ${err.code}, message: ${err.message}`);
});
```

## setAudioVolumeScale

```TypeScript
setAudioVolumeScale(scale: double): void
```

设置音频音量大小，无返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemTonePlayer-setAudioVolumeScale(scale: double): void--><!--Device-SystemTonePlayer-setAudioVolumeScale(scale: double): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | double | 是 | 音频音量大小，必须在[0, 1]之间取值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [20700002](../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter check error. For example, value is outside [0,1]. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## 示例

```TypeScript
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

## setHapticsFeature

```TypeScript
setHapticsFeature(hapticsFeature: systemSoundManager.ToneHapticsFeature): void
```

设置播放铃音时的振动风格。 调用本接口前，应该先调用[getSupportedHapticsFeatures](#getSupportedHapticsFeatures)查询 支持的振动风格，如果设置不支持的振动风格，则设置失败。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemTonePlayer-setHapticsFeature(hapticsFeature: systemSoundManager.ToneHapticsFeature): void--><!--Device-SystemTonePlayer-setHapticsFeature(hapticsFeature: systemSoundManager.ToneHapticsFeature): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapticsFeature | systemSoundManager.ToneHapticsFeature | 是 | 振动风格。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [20700003](../errorcode-audio-ringtone-sys.md#20700003-操作不支持) | Unsupported operation. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## 示例

```TypeScript
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

## start

```TypeScript
start(toneOptions?: SystemToneOptions): Promise<int>
```

开始播放提示音。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.VIBRATE

<!--Device-SystemTonePlayer-start(toneOptions?: SystemToneOptions): Promise<int>--><!--Device-SystemTonePlayer-start(toneOptions?: SystemToneOptions): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| toneOptions | [SystemToneOptions](arkts-audio-systemtoneplayer-systemtoneoptions-i-sys.md) | 否 | 系统提示音选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回streamID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## 示例

```TypeScript
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

## stop

```TypeScript
stop(id: int): Promise<void>
```

停止播放提示音。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemTonePlayer-stop(id: int): Promise<void>--><!--Device-SystemTonePlayer-stop(id: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | int | 是 | Promise对象，返回streamID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise回调返回停止播放成功或失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let streamID = 0; // streamID为start方法返回的streamID，此处只做初始化。
systemTonePlayer.stop(streamID).then(() => {
  console.info('Succeeded in doing stop.');
}).catch((err: BusinessError) => {
  console.error(`Failed to stop. Code: ${err.code}, message: ${err.message}`);
});
```

