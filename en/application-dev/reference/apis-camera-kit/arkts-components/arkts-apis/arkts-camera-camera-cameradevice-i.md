# CameraDevice

Describes the camera device information.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## automotiveCameraPosition

```TypeScript
readonly automotiveCameraPosition?: AutomotiveCameraPosition
```

Automotive camera position attribute.

**Type:** [AutomotiveCameraPosition](arkts-camera-camera-automotivecameraposition-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Camera.Core

## cameraId

```TypeScript
readonly cameraId: string
```

Camera ID.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

## cameraOrientation

```TypeScript
readonly cameraOrientation: number
```

Camera installation angle, which does not change as the screen rotates. The value range is [0, 360], in degrees.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

## cameraPosition

```TypeScript
readonly cameraPosition: CameraPosition
```

Camera position.

**Type:** [CameraPosition](arkts-camera-camera-cameraposition-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

## cameraType

```TypeScript
readonly cameraType: CameraType
```

Camera type.

**Type:** [CameraType](arkts-camera-camera-cameratype-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

## connectionType

```TypeScript
readonly connectionType: ConnectionType
```

Camera connection type.

**Type:** [ConnectionType](arkts-camera-camera-connectiontype-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

## constituentCameraDevices

```TypeScript
readonly constituentCameraDevices?: Array<CameraDevice>
```

List of physical cameras that form the logical camera.

**Type:** Array&lt;[CameraDevice](arkts-camera-camera-cameradevice-i.md)&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

## hostDeviceName

```TypeScript
readonly hostDeviceName: string
```

Remote device name. If no remote device is available, an empty value is returned.

**Type:** string

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

## hostDeviceType

```TypeScript
readonly hostDeviceType: HostDeviceType
```

Remote device type.

**Type:** [HostDeviceType](arkts-camera-camera-hostdevicetype-e.md)

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

## isLogicalCamera

```TypeScript
readonly isLogicalCamera?: boolean
```

Whether a camera is a logical camera (consisting of multiple physical cameras). **true** if the camera is a logical camera, **false** otherwise.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

## lensDistortion

```TypeScript
readonly lensDistortion?: Array<number>
```

Array of lens distortion parameters.

**Type:** Array&lt;number&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

## lensEquivalentFocalLength

```TypeScript
readonly lensEquivalentFocalLength?: Array<number>
```

Equivalent focal length of the camera lens.

**Type:** Array&lt;number&gt;

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

## lensFocalLength

```TypeScript
readonly lensFocalLength?: number
```

Actual focal length of the lens.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

## lensIntrinsicCalibration

```TypeScript
readonly lensIntrinsicCalibration?: Array<number>
```

Array of lens intrinsic calibration parameters.

**Type:** Array&lt;number&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

## minimumFocusDistance

```TypeScript
readonly minimumFocusDistance?: number
```

Minimum focus distance of the camera.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

## sensorColorFilterArrangement

```TypeScript
readonly sensorColorFilterArrangement?: SensorColorFilterArrangement
```

Arrangement mode of the sensor color filter.

**Type:** [SensorColorFilterArrangement](arkts-camera-camera-sensorcolorfilterarrangement-e.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

## sensorPhysicalSize

```TypeScript
readonly sensorPhysicalSize?: Array<number>
```

Physical dimensions (width and height) of the sensor.

**Type:** Array&lt;number&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

## sensorPixelArraySize

```TypeScript
readonly sensorPixelArraySize?: Array<number>
```

Pixel array dimensions (width and height, in pixels) of the sensor.

**Type:** Array&lt;number&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core
