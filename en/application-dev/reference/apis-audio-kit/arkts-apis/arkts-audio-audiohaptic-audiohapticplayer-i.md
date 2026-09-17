# AudioHapticPlayer

Implements audio-haptic playback. Before calling any API in AudioHapticPlayer, you must use [createPlayer](arkts-audio-audiohaptic-audiohapticmanager-i.md#createplayer) to create an AudioHapticPlayer instance.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

## Modules to Import

```TypeScript
import { audioHaptic } from '@kit.AudioKit';
```

## isMuted

```TypeScript
isMuted(type: AudioHapticType): boolean
```

Checks whether an audio-haptic type is muted.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [AudioHapticType](arkts-audio-audiohaptic-audiohaptictype-e.md) | Yes | Audio-haptic type. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the audio-haptic type is muted. **true** if muted, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Parameter verification failed. |

**Examples**

```TypeScript
let audioHapticType: audioHaptic.AudioHapticType = audioHaptic.AudioHapticType.AUDIO_HAPTIC_TYPE_AUDIO;

let result: boolean = audioHapticPlayerInstance.isMuted(audioHapticType);
```

## off('endOfStream')

```TypeScript
off(type: 'endOfStream', callback?: Callback<void>): void
```

Unsubscribes from the EOS event. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'endOfStream' | Yes | Event type. The event **'endOfStream'** is triggered when the audio stream playback ends. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Callback that returns no value. |

## off('audioInterrupt')

```TypeScript
off(type: 'audioInterrupt', callback?: Callback<audio.InterruptEvent>): void
```

Unsubscribes from the audio interruption event. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | Yes | Event type. The event **'audioInterrupt'** is triggered when the audio focus is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[audio.InterruptEvent](arkts-audio-audio-interruptevent-i.md)&gt; | No | Callback used to return the event information. |

## on('endOfStream')

```TypeScript
on(type: 'endOfStream', callback: Callback<void>): void
```

Subscribes to end of stream (EOS) event, which is triggered when the audio stream playback ends. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'endOfStream' | Yes | Event type. The event **'endOfStream'** is triggered when the audio stream playback ends. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

## on('audioInterrupt')

```TypeScript
on(type: 'audioInterrupt', callback: Callback<audio.InterruptEvent>): void
```

Subscribes to the audio interruption event, which is triggered when the audio focus is changed. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | Yes | Event type. The event **'audioInterrupt'** is triggered when the audio focus is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[audio.InterruptEvent](arkts-audio-audio-interruptevent-i.md)&gt; | Yes | Callback used to return the event information. |

## release

```TypeScript
release(): Promise<void>
```

Releases this audio-haptic player. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-play-service-dead) | Service died. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioHapticPlayerInstance.release().then(() => {
  console.info(`Promise returned to indicate that release the audio haptic player successfully.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to release the audio haptic player. ${err}`);
});
```

## setLoop

```TypeScript
setLoop(loop: boolean): Promise<void>
```

Sets this audio-haptic player to play in a loop. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API must be called before the audio-haptic player is released.

**Since:** 20

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| loop | boolean | Yes | Whether to play in a loop. **true** to play in a loop, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operate not permit in current state. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioHapticPlayerInstance.setLoop(true).then(() => {
  console.info('Promise returned to indicate that set player loop successfully.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set player loop. ${err}`);
});
```

## setVolume

```TypeScript
setVolume(volume: number): Promise<void>
```

Sets the volume for this audio-haptic player. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API must be called before the audio-haptic player is released.

**Since:** 20

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volume | number | Yes | Volume, in the range [0.00, 1.00], where 1.00 indicates the maximum volume (100%). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operate not permit in current state. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-play-service-dead) | Service died. |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-parameter-value-out-of-range) | Parameter out of range. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioHapticPlayerInstance.setVolume(0.5).then(() => {
  console.info('Promise returned to indicate that set volume successfully.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set volume. ${err}`);
});
```

## start

```TypeScript
start(): Promise<void>
```

Starts playback. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operate not permit. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-io-error) | IO error. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-play-service-dead) | Service died. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioHapticPlayerInstance.start().then(() => {
  console.info(`Promise returned to indicate that start playing successfully.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to start playing. ${err}`);
});
```

## stop

```TypeScript
stop(): Promise<void>
```

Stops playback. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operate not permit. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-play-service-dead) | Service died. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioHapticPlayerInstance.stop().then(() => {
  console.info(`Promise returned to indicate that stop playing successfully.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to stop playing. ${err}`);
});
```
