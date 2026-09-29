# ToneHapticsSettings (System API)

```TypeScript
interface ToneHapticsSettings
```

Haptics settings in tone scenario.

**Since:** 14

<!--Device-systemSoundManager-interface ToneHapticsSettings--><!--Device-systemSoundManager-interface ToneHapticsSettings-End-->

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

<!--Device-ToneHapticsSettings-hapticsUri?: string--><!--Device-ToneHapticsSettings-hapticsUri?: string-End-->

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.

## mode

```TypeScript
mode: ToneHapticsMode
```

Haptics mode.

**Type:** [ToneHapticsMode](arkts-audio-systemsoundmanager-tonehapticsmode-e-sys.md)

**Since:** 14

<!--Device-ToneHapticsSettings-mode: ToneHapticsMode--><!--Device-ToneHapticsSettings-mode: ToneHapticsMode-End-->

**System capability:** SystemCapability.Multimedia.SystemSound.Core

**System API:** This is a system API.
