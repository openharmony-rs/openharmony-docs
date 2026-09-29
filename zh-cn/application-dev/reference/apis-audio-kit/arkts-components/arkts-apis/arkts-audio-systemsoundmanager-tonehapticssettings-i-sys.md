# ToneHapticsSettings（系统接口）

```TypeScript
interface ToneHapticsSettings
```

系统铃音的振动设置。

**起始版本：** 14

<!--Device-systemSoundManager-interface ToneHapticsSettings--><!--Device-systemSoundManager-interface ToneHapticsSettings-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { systemSoundManager } from '@kit.AudioKit';
```

## hapticsUri

```TypeScript
hapticsUri?: string
```

振动 URI。当 [mode](#mode) 为 NON_SYC 时，用户可以设置或获取此参数；在其他情况下，该 URI 无效，应予以忽略。

**类型：** string

**起始版本：** 14

<!--Device-ToneHapticsSettings-hapticsUri?: string--><!--Device-ToneHapticsSettings-hapticsUri?: string-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

## mode

```TypeScript
mode: ToneHapticsMode
```

振动模式。

**类型：** [ToneHapticsMode](arkts-audio-systemsoundmanager-tonehapticsmode-e-sys.md)

**起始版本：** 14

<!--Device-ToneHapticsSettings-mode: ToneHapticsMode--><!--Device-ToneHapticsSettings-mode: ToneHapticsMode-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。
