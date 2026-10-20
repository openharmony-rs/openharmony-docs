# AudioSeparationEffectAvailableStatus (System API)

```TypeScript
interface AudioSeparationEffectAvailableStatus
```

Indicates the available status of audio separation effect.

**Since:** 26.0.1

<!--Device-audio-interface AudioSeparationEffectAvailableStatus--><!--Device-audio-interface AudioSeparationEffectAvailableStatus-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## appUid

```TypeScript
appUid?: number
```

Application UID corresponding to the availability status. Generally, the value is the application displayed in the playback control application. The value should be an integer.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSeparationEffectAvailableStatus-appUid?: int--><!--Device-AudioSeparationEffectAvailableStatus-appUid?: int-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.

## available

```TypeScript
available: boolean
```

Indicates the availability status. The playback control application can determine whether to display the audio separation switch button based on the status.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSeparationEffectAvailableStatus-available: boolean--><!--Device-AudioSeparationEffectAvailableStatus-available: boolean-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.
