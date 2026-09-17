# getAudioManager

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getAudioManager

```TypeScript
function getAudioManager(): AudioManager
```

Obtains an AudioManager instance.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Return value:**

| Type | Description |
| --- | --- |
| [AudioManager](arkts-audio-audio-audiomanager-i.md) | AudioManager instance. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

let audioManager = audio.getAudioManager();
```
