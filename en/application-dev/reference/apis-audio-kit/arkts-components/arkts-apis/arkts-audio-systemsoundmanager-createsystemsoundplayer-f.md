# createSystemSoundPlayer

## Modules to Import

```TypeScript
import { systemSoundManager } from '@kit.AudioKit';
```

## createSystemSoundPlayer

```TypeScript
function createSystemSoundPlayer(): Promise<SystemSoundPlayer | null>
```

Creates a SystemSoundPlayer instance. This function uses a promise to return the result. This player can be used to play some system sounds for media or camera actions.

**Since:** 23

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SystemSoundPlayer](arkts-audio-systemsoundmanager-systemsoundplayer-t.md) &#124; null&gt; | Promise used to return the result. If the operation is successful, a SystemSoundPlayer instance is returned. Otherwise, null is returned. The instance is used for loading and playback. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400101](../../apis-media-kit/errorcode-media.md#5400101-memory-allocation-failed) | No memory. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let systemSoundPlayer: systemSoundManager.SystemSoundPlayer | null = null;

systemSoundManager.createSystemSoundPlayer().then((systemSoundPlayerInstance) => {
  console.info('Succeeded in creating the system sound player.');
  systemSoundPlayer = systemSoundPlayerInstance;
}).catch((err: BusinessError) => {
  console.error(`Failed to create the system sound player. Code: ${err.code}, message: ${err.message}`);
});
```
