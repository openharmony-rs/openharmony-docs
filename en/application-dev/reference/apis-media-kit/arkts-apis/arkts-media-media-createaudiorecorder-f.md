# createAudioRecorder

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## createAudioRecorder

```TypeScript
function createAudioRecorder(): AudioRecorder
```

Creates an AudioRecorder instance to control audio recording. Only one AudioRecorder instance can be created per device.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [createAVRecorder](arkts-media-media-createavrecorder-f.md)(callback: AsyncCallback&lt;AVRecorder&gt;)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

**Return value:**

| Type | Description |
| --- | --- |
| [AudioRecorder](arkts-media-media-audiorecorder-i.md) | If the operation is successful, an AudioRecorder instance is returned; otherwise, **null** is returned. The instance can be used to record audio. |

**Examples**

```TypeScript
let audioRecorder: media.AudioRecorder = media.createAudioRecorder();
```
