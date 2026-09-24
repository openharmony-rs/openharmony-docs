# SystemTonePlayer (System API)

```TypeScript
export declare interface SystemTonePlayer
```

The module provides APIs for playing and configuring SMS tones and notification tones and obtaining related information. Before calling any API in SystemTonePlayer, you must use [getSystemTonePlayer](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#getsystemtoneplayer) to create a SystemTonePlayer instance.

**Since:** 11

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

## getAudioVolumeScale

```TypeScript
getAudioVolumeScale(): number
```

Obtains the scale of the audio volume. This API returns the result synchronously.

**Since:** 13

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | Current audio volume. The value range is [0, 1]. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let scale: number = systemTonePlayer.getAudioVolumeScale();
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

Obtains the haptics style of the ringtone. This API returns the result synchronously.

**Since:** 13

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [systemSoundManager.ToneHapticsFeature](arkts-audio-systemsoundmanager-tonehapticsfeature-e-sys.md) | Haptics style. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [20700003](../errorcode-audio-ringtone-sys.md#20700003-operation-not-supported) | Unsupported operation. |

**Examples**

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

Obtains the supported haptics styles. This API uses a promise to return the result.

**Since:** 13

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[systemSoundManager.ToneHapticsFeature](arkts-audio-systemsoundmanager-tonehapticsfeature-e-sys.md)&gt;&gt; | Promise used to return an array of the supported haptics styles. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [20700003](../errorcode-audio-ringtone-sys.md#20700003-operation-not-supported) | Unsupported operation. |

**Examples**

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

Obtains the title of a system tone. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the title obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-io-error) | I/O error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

systemTonePlayer.getTitle().then((value: string) => {
  console.info('Succeeded in doing getTitle.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getTitle. Code: ${err.code}, message: ${err.message}`);
});
```

## off('playFinished')

```TypeScript
off(type: 'playFinished', callback?: Callback<number>): void
```

Unsubscribes from the event indicating that the ringtone playback is finished. This API uses an asynchronous callback to return the result.

**Since:** 18

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'playFinished' | Yes | Event type. The event **'playFinished'** is triggered when the playback is finished. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback used to return the ID of the audio stream. If this parameter is not specified, all the subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [20700002](../errorcode-audio-ringtone-sys.md#20700002-parameter-check-failed) |  |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
systemTonePlayer.off('playFinished');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let playFinishedCallback = (streamId: number) => {
  console.info(`Receive the callback of playFinished, streamId: ${streamId}.`);
};

systemTonePlayer.on('playFinished', 0, playFinishedCallback);

systemTonePlayer.off('playFinished', playFinishedCallback);
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from error events that occur during ringtone playback. This API uses an asynchronous callback to return the result.

**Since:** 18

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. The event **'error'** is triggered when an error occurs during ringtone playback. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to return the error code and error information. If this parameter is not specified, all the subscriptions to the specified event are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [20700002](../errorcode-audio-ringtone-sys.md#20700002-parameter-check-failed) |  |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Cancel all subscriptions to the event.
systemTonePlayer.off('error');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let callback = (err: BusinessError) => {
  console.info(`Succeeded in using on or off function. code: ${err.code}, message: ${err.message}`);
};

systemTonePlayer.on('error', callback);

systemTonePlayer.off('error', callback);
```

## on('playFinished')

```TypeScript
on(type: 'playFinished', streamId: number, callback: Callback<number>): void
```

Subscribes to the event indicating that the ringtone playback is finished. This API uses an asynchronous callback to return the result.

The object to listen for is an audio stream specified by **streamId**. If **streamId** is set to **0**, this API subscribes to the playback complete event of all audio streams of the player.

**Since:** 18

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'playFinished' | Yes | Event type. The event **'playFinished'** is triggered when the playback is finished. |
| streamId | number | Yes | ID of the audio stream. **streamId** is obtained through [start](#start). If **streamId** is set to **0**, the playback complete event of all audio streams of the player is subscribed to. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the stream ID of the audio stream that finishes playing. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [20700002](../errorcode-audio-ringtone-sys.md#20700002-parameter-check-failed) |  |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Subscribe to the playback complete events of all audio streams.
systemTonePlayer.on('playFinished', 0, (streamId: number) => {
  console.info(`Receive the callback of playFinished, streamId: ${streamId}.`);
});

// Subscribe to the playback complete event of a specified audio stream.
systemTonePlayer.start().then((value: number) => {
  systemTonePlayer.on('playFinished', value, (streamId: number) => {
    console.info(`Receive the callback of playFinished, streamId: ${streamId}.`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to start system tone player. ${err}`);
});
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to error events that occur during ringtone playback. This API uses an asynchronous callback to return the result.

**Since:** 18

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. The event **'error'** is triggered when an error occurs during ringtone playback. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to return the error code and error information. For details about the error codes, see [on('error')](../../apis-media-kit/arkts-apis/arkts-media-media-avplayer-i.md#onerror) of the AVPlayer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [20700002](../errorcode-audio-ringtone-sys.md#20700002-parameter-check-failed) |  |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

systemTonePlayer.on('error', (err: BusinessError) => {
  console.info(`Succeeded in using on function. code: ${err.code}, message: ${err.message}`);
});
```

## prepare

```TypeScript
prepare(): Promise<void>
```

Prepares to play a system tone. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-io-error) | I/O error. |

**Examples**

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

Releases the system tone player. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |

**Examples**

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
setAudioVolumeScale(scale: number): void
```

Sets the scale of the audio volume. No result is returned.

**Since:** 13

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | number | Yes | Scale of the audio volume. The value is in the range [0, 1]. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |
| [20700002](../errorcode-audio-ringtone-sys.md#20700002-parameter-check-failed) | Parameter check error. For example, value is outside [0,1]. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let scale: number = 0.5;
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

Sets a haptics style of the ringtone.

Before calling this API, call [getSupportedHapticsFeatures](#getsupportedhapticsfeatures) to obtain the supported haptics styles. The setting fails if the haptics style to set is not supported.

**Since:** 13

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hapticsFeature | [systemSoundManager.ToneHapticsFeature](arkts-audio-systemsoundmanager-tonehapticsfeature-e-sys.md) | Yes | Haptics style. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |
| [20700003](../errorcode-audio-ringtone-sys.md#20700003-operation-not-supported) | Unsupported operation. |

**Examples**

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
start(toneOptions?: SystemToneOptions): Promise<number>
```

Start playing the system tone. By default, the audio and haptic will not be muted. Using tone options to mute audio or haptics. If haptics is needed, caller should have the permission of ohos.permission.VIBRATE.

**Since:** 11

**Required permissions:** ohos.permission.VIBRATE

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| toneOptions | [SystemToneOptions](arkts-audio-systemtoneplayer-systemtoneoptions-i-sys.md) | No | Options of the system tone. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the stream ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

class SystemToneOptions {
  muteAudio: boolean = false;
  muteHaptics: boolean = false;
}
let systemToneOptions: SystemToneOptions = {muteAudio: true, muteHaptics: false};

systemTonePlayer.start(systemToneOptions).then((value: number) => {
  console.info('Succeeded in doing start.');
}).catch((err: BusinessError) => {
  console.error(`Failed to start. Code: ${err.code}, message: ${err.message}`);
});
```

## stop

```TypeScript
stop(id: number): Promise<void>
```

Stops playing a system tone. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Promise used to return the stream ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let streamID: number = 0; // streamID is the stream ID returned by start(). Only initialization is performed here.
systemTonePlayer.stop(streamID).then(() => {
  console.info('Succeeded in doing stop.');
}).catch((err: BusinessError) => {
  console.error(`Failed to stop. Code: ${err.code}, message: ${err.message}`);
});
```
