# SystemSoundPlayer

Implements a system sound player that provides functions for loading, unloading, playing system sounds. Before using these functions, application must call [createSystemSoundPlayer](arkts-audio-systemsoundmanager-createsystemsoundplayer-f.md) to create a SystemSoundPlayer instance first.

**Since:** 23

**System capability:** SystemCapability.Multimedia.SystemSound.Core

## load

```TypeScript
load(soundType: systemSoundManager.SystemSoundType): Promise<void>
```

Loads a system sound.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| soundType | [systemSoundManager.SystemSoundType](arkts-audio-systemsoundmanager-systemsoundtype-e.md) | Yes | type of sound to preload. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-io-error) | I/O error. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-play-service-dead) | Crash or blocking occurs in system process. |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-parameter-value-out-of-range) | Parameter check failed. Returned by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

systemSoundPlayer?.load(systemSoundManager.SystemSoundType.PHOTO_SHUTTER).then(() => {
  console.info('Succeeded in calling the load method.');
}).catch((err: BusinessError) => {
  console.error(`Failed to call the load method. Code: ${err.code}, message: ${err.message}`);
});
```

## play

```TypeScript
play(soundType: systemSoundManager.SystemSoundType): Promise<void>
```

Plays a system sound.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| soundType | [systemSoundManager.SystemSoundType](arkts-audio-systemsoundmanager-systemsoundtype-e.md) | Yes | type of sound to play. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-io-error) | I/O error. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-play-service-dead) | Crash or blocking occurs in system process. |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-parameter-value-out-of-range) | Parameter check failed. Returned by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

systemSoundPlayer?.play(systemSoundManager.SystemSoundType.PHOTO_SHUTTER).then(() => {
  console.info('Succeeded in calling the play method.');
}).catch((err: BusinessError) => {
  console.error(`Failed to call the play method. Code: ${err.code}, message: ${err.message}`);
});
```

## release

```TypeScript
release(): Promise<void>
```

Releases this system sound player instance.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-play-service-dead) | Crash or blocking occurs in system process. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

systemSoundPlayer?.release().then(() => {
  console.info('Succeeded in calling the release method.');
}).catch((err: BusinessError) => {
  console.error(`Failed to call the release method. Code: ${err.code}, message: ${err.message}`);
});
```

## unload

```TypeScript
unload(soundType: systemSoundManager.SystemSoundType): Promise<void>
```

Unloads a system sound that has been loaded before.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| soundType | [systemSoundManager.SystemSoundType](arkts-audio-systemsoundmanager-systemsoundtype-e.md) | Yes | type of sound to unload. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-play-service-dead) | Crash or blocking occurs in system process. |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-parameter-value-out-of-range) | Parameter check failed. Returned by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

systemSoundPlayer?.unload(systemSoundManager.SystemSoundType.PHOTO_SHUTTER).then(() => {
  console.info('Succeeded in calling the unload method.');
}).catch((err: BusinessError) => {
  console.error(`Failed to call the unload method. Code: ${err.code}, message: ${err.message}`);
});
```
