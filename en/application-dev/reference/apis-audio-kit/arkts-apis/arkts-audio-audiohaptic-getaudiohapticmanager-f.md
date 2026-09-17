# getAudioHapticManager

## Modules to Import

```TypeScript
import { audioHaptic } from '@kit.AudioKit';
```

## getAudioHapticManager

```TypeScript
function getAudioHapticManager(): AudioHapticManager
```

Obtains an [AudioHapticManager](arkts-audio-audiohaptic-audiohapticmanager-i.md) instance. This object is singleton in one process.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

**Return value:**

| Type | Description |
| --- | --- |
| [AudioHapticManager](arkts-audio-audiohaptic-audiohapticmanager-i.md) | AudioHapticManager instance. |

**Examples**

```TypeScript
let audioHapticManagerInstance: audioHaptic.AudioHapticManager = audioHaptic.getAudioHapticManager();
```
