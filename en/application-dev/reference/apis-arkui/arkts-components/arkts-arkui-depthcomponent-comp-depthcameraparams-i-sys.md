# DepthCameraParams (System API)

```TypeScript
declare interface DepthCameraParams
```

Camera parameters struct.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## cameraBufferCrop

```TypeScript
cameraBufferCrop?: CameraBufferCrop
```

Camera buffer crop parameters.

**Type:** [CameraBufferCrop](arkts-arkui-depthcomponent-comp-camerabuffercrop-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## position

```TypeScript
position: DepthVector3
```

Camera position in 3D space.

**Type:** [DepthVector3](arkts-arkui-common-comp-depthvector3-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## quaternion

```TypeScript
quaternion: DepthVector4
```

Camera rotation as quaternion (x, y, z, w). Represents the orientation of the camera in 3D space.

**Type:** [DepthVector4](arkts-arkui-common-comp-depthvector4-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## yFov

```TypeScript
yFov: number
```

Vertical field of view in radians.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## zFar

```TypeScript
zFar: number
```

Far clipping plane distance.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## zNear

```TypeScript
zNear: number
```

Near clipping plane distance.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
