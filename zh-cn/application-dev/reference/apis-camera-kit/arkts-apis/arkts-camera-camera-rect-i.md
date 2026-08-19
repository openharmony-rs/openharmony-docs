# Rect

相机矩形。用于各类检测对象的矩形框绘制。返回的检测点坐标系以设备充电口在右侧时的横向设备方向为基准。该坐标系左上角为（0，0），右下角为（1，1），其中（topLeftX，topLeftY）表示矩形区域的左上角坐标，width和 height分别表示矩形区域的宽和高。因此在实际使用中根据业务诉求需要裁剪或者选择人脸区域时，必须将矩形区域的x坐标和y坐标分别乘以实际相机预览输出流的宽和高，即可得到裁剪后的人脸矩形区域。 实际预览流的宽高指的是相机输出流的分辨率，请参考[profile](arkts-camera-camera-profile-i.md)中的size。 预览流的数据获取请参考[双路预览(ArkTs)](../../../media/camera/camera-dual-channel-preview.md)。

**起始版本：** 23

<!--Device-camera-interface Rect--><!--Device-camera-interface Rect-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## height

```TypeScript
height: double
```

矩形高，范围[0, 1]。

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Rect-height: double--><!--Device-Rect-height: double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## topLeftX

```TypeScript
topLeftX: double
```

矩形区域左上角x坐标，范围[0, 1]。

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Rect-topLeftX: double--><!--Device-Rect-topLeftX: double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## topLeftY

```TypeScript
topLeftY: double
```

矩形区域左上角y坐标，范围[0, 1]。

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Rect-topLeftY: double--><!--Device-Rect-topLeftY: double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## width

```TypeScript
width: double
```

矩形宽，范围[0, 1]。

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Rect-width: double--><!--Device-Rect-width: double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

