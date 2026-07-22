# DepthCameraParams（系统接口）

相机参数。

**起始版本：** 26.0.0

<!--Device-unnamed-declare interface DepthCameraParams--><!--Device-unnamed-declare interface DepthCameraParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## cameraBufferCrop

```TypeScript
cameraBufferCrop?: CameraBufferCrop
```

相机移轴裁剪参数。未设置时默认使用组件布局尺寸作为默认图像基准大小，裁剪偏移量为(0, 0)，缩放比例为1.0。

**类型：** CameraBufferCrop

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DepthCameraParams-cameraBufferCrop?: CameraBufferCrop--><!--Device-DepthCameraParams-cameraBufferCrop?: CameraBufferCrop-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## position

```TypeScript
position: DepthVector3
```

相机在三维空间中的位置。无单位，其值表示3D空间中的坐标。

**类型：** DepthVector3

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DepthCameraParams-position: DepthVector3--><!--Device-DepthCameraParams-position: DepthVector3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## quaternion

```TypeScript
quaternion: DepthVector4
```

相机旋转四元数，按(x, y, z, w)表示。无单位。

**类型：** DepthVector4

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DepthCameraParams-quaternion: DepthVector4--><!--Device-DepthCameraParams-quaternion: DepthVector4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## yFov

```TypeScript
yFov: number
```

相机垂直方向视场角，单位为弧度。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DepthCameraParams-yFov: double--><!--Device-DepthCameraParams-yFov: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## zFar

```TypeScript
zFar: number
```

远裁剪面距离。无单位。必须为正数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DepthCameraParams-zFar: double--><!--Device-DepthCameraParams-zFar: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## zNear

```TypeScript
zNear: number
```

近裁剪面距离。无单位。必须为正数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DepthCameraParams-zNear: double--><!--Device-DepthCameraParams-zNear: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

