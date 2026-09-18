# ToneHapticsSettings (System API)

Haptics settings in tone scenario.

**Since:** 14

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { systemSoundManager } from '@kit.AudioKit';
```

## hapticsUri

```TypeScript
hapticsUri?: string
```

Haptics uri. Users can set/get this parameter when [mode](#mode) is NON_SYC. In other cases, this uri is useless and should be ignored.

**Type:** string

**Since:** 14

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

## mode

```TypeScript
mode: ToneHapticsMode
```

Haptics mode.

**Type:** [ToneHapticsMode](arkts-audio-systemsoundmanager-tonehapticsmode-e-sys.md)

**Since:** 14

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.
