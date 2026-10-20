# SettingParam（系统接口）

```TypeScript
interface SettingParam
```

定义用于预热图像的效果参数。

**起始版本：** 11

<!--Device-camera-interface SettingParam--><!--Device-camera-interface SettingParam-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## faceSlender

```TypeScript
faceSlender: number
```

瘦脸级别，通过[Beauty.getSupportedBeautyRange](arkts-camera-camera-beautyquery-i-sys.md#getsupportedbeautyrange)获取。例如，值**1**表示1级瘦脸。

**类型：** number

**起始版本：** 11

<!--Device-SettingParam-faceSlender: int--><!--Device-SettingParam-faceSlender: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## skinSmoothLevel

```TypeScript
skinSmoothLevel: number
```

磨皮级别，通过[Beauty.getSupportedBeautyRange](arkts-camera-camera-beautyquery-i-sys.md#getsupportedbeautyrange)获取。例如，值**1**表示1级磨皮。

**类型：** number

**起始版本：** 11

<!--Device-SettingParam-skinSmoothLevel: int--><!--Device-SettingParam-skinSmoothLevel: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## skinTone

```TypeScript
skinTone: number
```

美肤级别，通过[Beauty.getSupportedBeautyRange](arkts-camera-camera-beautyquery-i-sys.md#getsupportedbeautyrange)获取。例如，值**0xBF986C**表示特定颜色。

**类型：** number

**起始版本：** 11

<!--Device-SettingParam-skinTone: int--><!--Device-SettingParam-skinTone: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
