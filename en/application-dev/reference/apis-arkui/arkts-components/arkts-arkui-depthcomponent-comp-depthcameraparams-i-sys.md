# DepthCameraParams (System API)

```TypeScript
declare interface DepthCameraParams
```

Provides camera parameters.

**Since:** 26.0.0

<!--Device-unnamed-declare interface DepthCameraParams--><!--Device-unnamed-declare interface DepthCameraParams-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## cameraBufferCrop

```TypeScript
cameraBufferCrop?: CameraBufferCrop
```

Camera buffer crop parameters. If not set, the component layout size is used as the default image reference size, with a crop offset of (0, 0) and a scale factor of 1.0.

**Type:** [CameraBufferCrop](arkts-arkui-depthcomponent-comp-camerabuffercrop-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DepthCameraParams-cameraBufferCrop?: CameraBufferCrop--><!--Device-DepthCameraParams-cameraBufferCrop?: CameraBufferCrop-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## position

```TypeScript
position: DepthVector3
```

Position of the camera in 3D space, without a unit. The value indicates the coordinates in 3D space.

**Type:** [DepthVector3](arkts-arkui-common-comp-depthvector3-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DepthCameraParams-position: DepthVector3--><!--Device-DepthCameraParams-position: DepthVector3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## quaternion

```TypeScript
quaternion: DepthVector4
```

Rotation quaternion of the camera, represented as (x, y, z, w). There is no unit.

**Type:** [DepthVector4](arkts-arkui-common-comp-depthvector4-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DepthCameraParams-quaternion: DepthVector4--><!--Device-DepthCameraParams-quaternion: DepthVector4-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## yFov

```TypeScript
yFov: number
```

Vertical field of view of the camera, in radians.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DepthCameraParams-yFov: double--><!--Device-DepthCameraParams-yFov: double-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## zFar

```TypeScript
zFar: number
```

Distance to the far clipping plane, without a unit. The value must be a positive number.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DepthCameraParams-zFar: double--><!--Device-DepthCameraParams-zFar: double-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## zNear

```TypeScript
zNear: number
```

Distance to the near clipping plane, without a unit. The value must be a positive number.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DepthCameraParams-zNear: double--><!--Device-DepthCameraParams-zNear: double-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
