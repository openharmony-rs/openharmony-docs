# SettingParam（系统接口）

Defines the effect parameters used to preheat an image.

**起始版本：** 23

<!--Device-camera-interface SettingParam--><!--Device-camera-interface SettingParam-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## faceSlender

```TypeScript
faceSlender: int
```

Face slimming level, which is obtained through [Beauty.getSupportedBeautyRange](arkts-camera-camera-beautyquery-i-sys.md#getsupportedbeautyrange). For example, the value **1** indicates level-1 slimming.

**类型：** int

**起始版本：** 23

<!--Device-SettingParam-faceSlender: int--><!--Device-SettingParam-faceSlender: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## skinSmoothLevel

```TypeScript
skinSmoothLevel: int
```

Skin smoothing level, which is obtained through [Beauty.getSupportedBeautyRange](arkts-camera-camera-beautyquery-i-sys.md#getsupportedbeautyrange). For example, the value **1** indicates level-1 smoothing.

**类型：** int

**起始版本：** 23

<!--Device-SettingParam-skinSmoothLevel: int--><!--Device-SettingParam-skinSmoothLevel: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## skinTone

```TypeScript
skinTone: int
```

Skin tone perfection level, which is obtained through [Beauty.getSupportedBeautyRange](arkts-camera-camera-beautyquery-i-sys.md#getsupportedbeautyrange). For example, the value **0xBF986C** indicates a specific color.

**类型：** int

**起始版本：** 23

<!--Device-SettingParam-skinTone: int--><!--Device-SettingParam-skinTone: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

