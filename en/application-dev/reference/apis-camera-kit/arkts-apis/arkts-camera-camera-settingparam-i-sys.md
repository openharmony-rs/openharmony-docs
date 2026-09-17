# SettingParam (System API)

Defines the effect parameters used to preheat an image.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## faceSlender

```TypeScript
faceSlender: number
```

Face slimming level, which is obtained through [Beauty.getSupportedBeautyRange](arkts-camera-camera-beautyquery-i-sys.md#getsupportedbeautyrange). For example, the value **1** indicates level-1 slimming.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## skinSmoothLevel

```TypeScript
skinSmoothLevel: number
```

Skin smoothing level, which is obtained through [Beauty.getSupportedBeautyRange](arkts-camera-camera-beautyquery-i-sys.md#getsupportedbeautyrange). For example, the value **1** indicates level-1 smoothing.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## skinTone

```TypeScript
skinTone: number
```

Skin tone perfection level, which is obtained through [Beauty.getSupportedBeautyRange](arkts-camera-camera-beautyquery-i-sys.md#getsupportedbeautyrange). For example, the value **0xBF986C** indicates a specific color.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.
