# AudioHRTFAnonymousDescriptor (System API)

```TypeScript
interface AudioHRTFAnonymousDescriptor
```

Anonymous personalzied HRTF file descriptor for cross-process transfer.

**Since:** 26.0.0

<!--Device-audio-interface AudioHRTFAnonymousDescriptor--><!--Device-audio-interface AudioHRTFAnonymousDescriptor-End-->

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## fd

```TypeScript
fd: number
```

The file descriptor of personalzied HRTF.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioHRTFAnonymousDescriptor-fd: int--><!--Device-AudioHRTFAnonymousDescriptor-fd: int-End-->

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

## length

```TypeScript
length: number
```

Total size of personalzied HRTF data in bytes.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioHRTFAnonymousDescriptor-length: long--><!--Device-AudioHRTFAnonymousDescriptor-length: long-End-->

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.
