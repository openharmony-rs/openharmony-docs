# createAudioPlayer

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## createAudioPlayer

```TypeScript
function createAudioPlayer(): AudioPlayer
```

Creates an AudioPlayer instance in synchronous mode.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [createAVPlayer](arkts-media-media-createavplayer-f.md)(callback: AsyncCallback&lt;AVPlayer&gt;)

**System capability:** SystemCapability.Multimedia.Media.AudioPlayer

**Return value:**

| Type | Description |
| --- | --- |
| [AudioPlayer](arkts-media-media-audioplayer-i.md) | If the operation is successful, an AudioPlayer instance is returned; otherwise, **null** is returned. After the instance is created, you can start, pause, or stop audio playback. |

**Examples**

```TypeScript
let audioPlayer: media.AudioPlayer = media.createAudioPlayer();
```
