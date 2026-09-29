# AudioHapticFileDescriptor

```TypeScript
interface AudioHapticFileDescriptor
```

Describes the audio-haptic file descriptor.

> **NOTE:** 
> 
> Ensure that **fd** is an available file descriptor and the values of **offset** and **length** are correct.

**Since:** 20

<!--Device-audioHaptic-interface AudioHapticFileDescriptor--><!--Device-audioHaptic-interface AudioHapticFileDescriptor-End-->

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

## Modules to Import

```TypeScript
import { audioHaptic } from '@kit.AudioKit';
```

## fd

```TypeScript
fd: number
```

File descriptor of the audio-haptic file, which is generally greater than or equal to 0.

**Type:** number

**Since:** 20

<!--Device-AudioHapticFileDescriptor-fd: int--><!--Device-AudioHapticFileDescriptor-fd: int-End-->

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

## length

```TypeScript
length?: number
```

Number of bytes to read. By default, the length is the number of bytes remaining in the file from the offset position.

**Type:** number

**Since:** 20

<!--Device-AudioHapticFileDescriptor-length?: long--><!--Device-AudioHapticFileDescriptor-length?: long-End-->

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

## offset

```TypeScript
offset?: number
```

Offset for reading data from the file, in bytes. By default, the offset is 0.

**Type:** number

**Since:** 20

<!--Device-AudioHapticFileDescriptor-offset?: long--><!--Device-AudioHapticFileDescriptor-offset?: long-End-->

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core
