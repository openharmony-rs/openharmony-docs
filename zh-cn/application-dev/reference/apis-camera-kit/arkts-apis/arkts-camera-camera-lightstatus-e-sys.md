# LightStatus（系统接口）

```TypeScript
enum LightStatus
```

枚举，相机光照状态，通过调用 VideoSessionForSys 的[on('lightStatusChange')](arkts-camera-camera-videosession-i-sys.md#onlightstatuschange)接口获取。

**起始版本：** 18

<!--Device-camera-enum LightStatus--><!--Device-camera-enum LightStatus-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## INSUFFICIENT

```TypeScript
INSUFFICIENT = 1
```

光照不足（过暗）。

**起始版本：** 18

<!--Device-LightStatus-INSUFFICIENT = 1--><!--Device-LightStatus-INSUFFICIENT = 1-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## NORMAL

```TypeScript
NORMAL = 0
```

正常光照条件。

**起始版本：** 18

<!--Device-LightStatus-NORMAL = 0--><!--Device-LightStatus-NORMAL = 0-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
