# AudioHapticPlayer

```TypeScript
interface AudioHapticPlayer
```

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

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioHapticPlayerInstance.off('endOfStream');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let endOfStreamCallback = () => {
  console.info(`Receive the callback of endOfStream.`);
};

audioHapticPlayerInstance.on('endOfStream', endOfStreamCallback);

audioHapticPlayerInstance.off('endOfStream', endOfStreamCallback);
```

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

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

// Cancel all subscriptions to the event.
audioHapticPlayerInstance.off('audioInterrupt');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let isPlaying: boolean; // An identifier specifying whether rendering is in progress.
let isDucked: boolean; // An identifier specifying whether the audio volume is reduced.
let audioInterruptCallback = (interruptEvent: audio.InterruptEvent) => {
  // When an audio interruption event occurs, the audioHapticPlayerInstance receives the interruptEvent callback and performs processing based on the content in the callback.
  // 1. (Optional) The AudioRenderer reads the value of interruptEvent.forceType to see whether the system has forcibly performed the operation.
  // Note: In the default focus strategy, INTERRUPT_HINT_RESUME maps to the force type INTERRUPT_SHARE, and others map to INTERRUPT_FORCE. Therefore, the value of forceType does not need to be checked.
  // 2. (Mandatory) The AudioRenderer then reads the value of interruptEvent.hintType and performs corresponding processing.
  if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_FORCE) {
    // The audio focus event has been forcibly executed by the system. The application needs to update its status and displayed content.
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_PAUSE:
        // The audio stream has been paused and temporarily loses the focus. It will receive the interruptEvent corresponding to resume when it is able to regain the focus.
        console.info('Force paused. Update playing status and stop writing');
        isPlaying = false; // A simplified processing indicating several operations for switching the application to the paused state.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_STOP:
        // The audio stream has been stopped and permanently loses the focus. The user must manually trigger the operation to resume rendering.
        console.info('Force stopped. Update playing status and stop writing');
        isPlaying = false; // A simplified processing indicating several operations for switching the application to the paused state.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_DUCK:
        // The audio stream is rendered at a reduced volume.
        console.info('Force ducked. Update volume status');
        isDucked = true; // A simplified processing indicating several operations for updating the volume status.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_UNDUCK:
        // The audio stream is rendered at the normal volume.
        console.info('Force unducked. Update volume status');
        isDucked = false; // A simplified processing indicating several operations for updating the volume status.
        break;
      default:
        break;
    }
  } else if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_SHARE) {
    // The audio focus event needs to be operated by the application, which can choose the processing mode. It is recommended that the application process the event according to the value of InterruptHint.
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_RESUME:
        // It is recommended that the application continue rendering. (The audio stream has been forcibly paused and temporarily lost the focus. It can resume rendering now.)
        // The INTERRUPT_HINT_RESUME operation must be proactively executed by the application and cannot be forcibly executed by the system. Therefore, the INTERRUPT_HINT_RESUME event must map to INTERRUPT_SHARE.
        console.info('Resume force paused renderer or ignore');
        // To continue rendering, the application must perform the required operations.
        break;
      default:
        break;
    }
  }
};

audioHapticPlayerInstance.on('audioInterrupt', audioInterruptCallback);

audioHapticPlayerInstance.off('audioInterrupt', audioInterruptCallback);
```

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

**Examples**

```TypeScript
audioHapticPlayerInstance.on('endOfStream', () => {
  console.info(`Receive the callback of endOfStream.`);
});
```

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

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

let isPlaying: boolean; // An identifier specifying whether rendering is in progress.
let isDucked: boolean; // An identifier specifying whether the audio volume is reduced.

audioHapticPlayerInstance.on('audioInterrupt', (interruptEvent: audio.InterruptEvent) => {
  // When an audio interruption event occurs, the audioHapticPlayerInstance receives the interruptEvent callback and performs processing based on the content in the callback.
  // 1. (Optional) The AudioRenderer reads the value of interruptEvent.forceType to see whether the system has forcibly performed the operation.
  // Note: In the default focus strategy, INTERRUPT_HINT_RESUME maps to the force type INTERRUPT_SHARE, and others map to INTERRUPT_FORCE. Therefore, the value of forceType does not need to be checked.
  // 2. (Mandatory) The AudioRenderer then reads the value of interruptEvent.hintType and performs corresponding processing.
  if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_FORCE) {
    // The audio focus event has been forcibly executed by the system. The application needs to update its status and displayed content.
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_PAUSE:
        // The audio stream has been paused and temporarily loses the focus. It will receive the interruptEvent corresponding to resume when it is able to regain the focus.
        console.info('Force paused. Update playing status and stop writing');
        isPlaying = false; // A simplified processing indicating several operations for switching the application to the paused state.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_STOP:
        // The audio stream has been stopped and permanently loses the focus. The user must manually trigger the operation to resume rendering.
        console.info('Force stopped. Update playing status and stop writing');
        isPlaying = false; // A simplified processing indicating several operations for switching the application to the paused state.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_DUCK:
        // The audio stream is rendered at a reduced volume.
        console.info('Force ducked. Update volume status');
        isDucked = true; // A simplified processing indicating several operations for updating the volume status.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_UNDUCK:
        // The audio stream is rendered at the normal volume.
        console.info('Force unducked. Update volume status');
        isDucked = false; // A simplified processing indicating several operations for updating the volume status.
        break;
      default:
        break;
    }
  } else if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_SHARE) {
    // The audio focus event needs to be operated by the application, which can choose the processing mode. It is recommended that the application process the event according to the value of InterruptHint.
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_RESUME:
        // It is recommended that the application continue rendering. (The audio stream has been forcibly paused and temporarily lost the focus. It can resume rendering now.)
        // The INTERRUPT_HINT_RESUME operation must be proactively executed by the application and cannot be forcibly executed by the system. Therefore, the INTERRUPT_HINT_RESUME event must map to INTERRUPT_SHARE.
        console.info('Resume force paused renderer or ignore');
        // To continue rendering, the application must perform the required operations.
        break;
      default:
        break;
    }
  }
});
```

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
