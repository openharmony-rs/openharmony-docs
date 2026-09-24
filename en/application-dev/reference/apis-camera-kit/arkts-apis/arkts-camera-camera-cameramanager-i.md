# CameraManager

```TypeScript
interface CameraManager
```

**CameraManager** implements camera management. Before calling any API in **CameraManager**, you must use [getCameraManager](arkts-camera-camera-getcameramanager-f.md) to obtain a **CameraManager** instance.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## createCameraInput

```TypeScript
createCameraInput(camera: CameraDevice): CameraInput
```

Creates a **CameraInput** instance with the specified **CameraDevice** instance. This API returns the result synchronously.

Before calling this API, call [getSupportedCameras](#getsupportedcameras) to obtain the list of supported camera devices, select the camera device that meets the requirements based on the actual usage scenario, and then create the **CameraInput** instance.

**Since:** 10

**Required permissions:** ohos.permission.CAMERA

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| camera | [CameraDevice](arkts-camera-camera-cameradevice-i.md) | Yes | **CameraDevice** instance, which is obtained through [getSupportedCameras](#getsupportedcameras). |

**Return value:**

| Type | Description |
| --- | --- |
| [CameraInput](arkts-camera-camera-camerainput-i.md) | **CameraInput** instance created. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed.<br>**Applicable version:** 12 and later |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createCameraInput(camera: camera.CameraDevice, cameraManager: camera.CameraManager): camera.CameraInput | undefined {
  let cameraInput: camera.CameraInput | undefined = undefined;
  try {
    cameraInput = cameraManager.createCameraInput(camera);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The createCameraInput call failed. error code: ${err.code}`);
  }
  return cameraInput;
}
```

<a id="createcamerainput-1"></a>

## createCameraInput

```TypeScript
createCameraInput(position: CameraPosition, type: CameraType): CameraInput
```

Creates a **CameraInput** instance with the specified camera position and type. This API returns the result synchronously.

Before calling this API, specify the camera position and type based on the usage scenario. For example, open the front camera for the selfie feature

**Since:** 10

**Required permissions:** ohos.permission.CAMERA

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | [CameraPosition](arkts-camera-camera-cameraposition-e.md) | Yes | Camera position. You need to obtain the supported camera object by calling [getSupportedCameras](#getsupportedcameras) and then obtain the device position information based on the returned camera object. |
| type | [CameraType](arkts-camera-camera-cameratype-e.md) | Yes | Camera type. You need to obtain the supported camera object by calling [getSupportedCameras](#getsupportedcameras) and then obtain the camera type based on the returned camera object. |

**Return value:**

| Type | Description |
| --- | --- |
| [CameraInput](arkts-camera-camera-camerainput-i.md) | **CameraInput** instance created. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed.<br>**Applicable version:** 12 and later |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createCameraInput(camera: camera.CameraDevice, cameraManager: camera.CameraManager): camera.CameraInput | undefined {
  let position: camera.CameraPosition = camera.cameraPosition;
  let type: camera.CameraType = camera.cameraType;
  let cameraInput: camera.CameraInput | undefined = undefined;
  try {
    cameraInput = cameraManager.createCameraInput(position, type);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The createCameraInput call failed. error code: ${err.code}`);
  }
  return cameraInput;
}
```

## createCaptureSession

```TypeScript
createCaptureSession(): CaptureSession
```

Creates a **CaptureSession** instance. This API returns the result synchronously.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [createSession](#createsession)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| [CaptureSession](arkts-camera-camera-capturesession-i.md) | **CaptureSession** instance created. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createCaptureSession(cameraManager: camera.CameraManager): camera.CaptureSession | undefined {
  let captureSession: camera.CaptureSession | undefined = undefined;
  try {
    captureSession = cameraManager.createCaptureSession();
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`createCaptureSession error. error code: ${err.code}`);
  }
  return captureSession;
}
```

## createDeferredPreviewOutput

```TypeScript
createDeferredPreviewOutput(profile: Profile): PreviewOutput
```

Creates a deferred **PreviewOutput** instance and adds it, instead of a common **PreviewOutput** instance, to the data stream during stream configuration.

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| profile | [Profile](arkts-camera-camera-profile-i.md) | Yes | Supported preview profile, which is obtained through [getSupportedOutputCapability](#getsupportedoutputcapability-1). |

**Return value:**

| Type | Description |
| --- | --- |
| [PreviewOutput](arkts-camera-camera-previewoutput-i.md) | **PreviewOutput** instance created. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application.<br>**Applicable version:** 12 - 23 |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error.<br>**Applicable version:** 24 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPreviewOutput(cameraOutputCapability: camera.CameraOutputCapability, cameraManager: camera.CameraManager): camera.PreviewOutput | undefined {
  let profile: camera.Profile = cameraOutputCapability.previewProfiles[0];
  let previewOutput: camera.PreviewOutput | undefined = undefined;
  try {
    previewOutput = cameraManager.createDeferredPreviewOutput(profile);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The createPreviewOutput call failed. error code: ${err.code}`);
  }
  return previewOutput;
}
```

## createMetadataOutput

```TypeScript
createMetadataOutput(metadataObjectTypes: Array<MetadataObjectType>): MetadataOutput
```

Creates a **MetadataOutput** instance. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| metadataObjectTypes | Array&lt;[MetadataObjectType](arkts-camera-camera-metadataobjecttype-e.md)&gt; | Yes | Metadata object types, which are obtained through [getSupportedOutputCapability](#getsupportedoutputcapability-1). |

**Return value:**

| Type | Description |
| --- | --- |
| [MetadataOutput](arkts-camera-camera-metadataoutput-i.md) | **MetadataOutput** instance created. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createMetadataOutput(cameraManager: camera.CameraManager, cameraOutputCapability: camera.CameraOutputCapability): void {
  let metadataObjectTypes: Array<camera.MetadataObjectType> = cameraOutputCapability.supportedMetadataObjectTypes;
  let metadataOutput: camera.MetadataOutput | undefined = undefined;
  try {
    metadataOutput = cameraManager.createMetadataOutput(metadataObjectTypes);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`createMetadataOutput error. error code: ${err.code}`);
  }
}
```

## createPhotoOutput

```TypeScript
createPhotoOutput(profile: Profile, surfaceId: string): PhotoOutput
```

Creates a **PhotoOutput** instance. This API returns the result synchronously.

> **NOTE:** 
> 
> - This API can only be used to create a **PhotoOutput** object in JPEG format.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [createPhotoOutput](#createphotooutput-1)(profile?: Profile)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| profile | [Profile](arkts-camera-camera-profile-i.md) | Yes | Supported photo profile, which is obtained through [getSupportedOutputCapability](#getsupportedoutputcapability-1). |
| surfaceId | string | Yes | Surface ID, which is obtained from [ImageReceiver](../../apis-image-kit/arkts-apis/arkts-image-image-imagereceiver-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [PhotoOutput](arkts-camera-camera-photooutput-i.md) | **PhotoOutput** instance created. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPhotoOutput(cameraOutputCapability: camera.CameraOutputCapability, cameraManager: camera.CameraManager): camera.PhotoOutput | undefined {
  let profile: camera.Profile = cameraOutputCapability.photoProfiles[0];
  let photoOutput: camera.PhotoOutput | undefined = undefined;
  try {
    photoOutput = cameraManager.createPhotoOutput(profile);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The createPhotoOutput call failed. error code: ${err.code}`);
  }
  return photoOutput;
}
```

<a id="createphotooutput-1"></a>

## createPhotoOutput

```TypeScript
createPhotoOutput(profile?: Profile): PhotoOutput
```

Creates a **PhotoOutput** instance. This API returns the result synchronously.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| profile | [Profile](arkts-camera-camera-profile-i.md) | No | Supported photo profile, which is obtained through [getSupportedOutputCapability](#getsupportedoutputcapability-1). <br>In API version 11, this parameter is mandatory. Starting from API version 12, it will overwrite the preconfigured parameters passed in through [preconfig](arkts-camera-camera-photosession-i.md#preconfig). |

**Return value:**

| Type | Description |
| --- | --- |
| [PhotoOutput](arkts-camera-camera-photooutput-i.md) | **PhotoOutput** instance created. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error.<br>**Applicable version:** 12 and later |

**Examples**

See [createPhotoOutput](#createphotooutput)

## createPreviewOutput

```TypeScript
createPreviewOutput(profile: Profile, surfaceId: string): PreviewOutput
```

Creates a **PreviewOutput** instance. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| profile | [Profile](arkts-camera-camera-profile-i.md) | Yes | Supported preview profile, which is obtained through [getSupportedOutputCapability](#getsupportedoutputcapability-1). |
| surfaceId | string | Yes | Surface ID, which is obtained from XComponent or [ImageReceiver](../../apis-image-kit/arkts-apis/arkts-image-image-imagereceiver-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [PreviewOutput](arkts-camera-camera-previewoutput-i.md) | **PreviewOutput** instance created. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPreviewOutput(cameraOutputCapability: camera.CameraOutputCapability, cameraManager: camera.CameraManager, surfaceId: string): camera.PreviewOutput | undefined {
  let profile: camera.Profile = cameraOutputCapability.previewProfiles[0];
  let previewOutput: camera.PreviewOutput | undefined = undefined;
  try {
    previewOutput = cameraManager.createPreviewOutput(profile, surfaceId);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The createPreviewOutput call failed. error code: ${err.code}`);
  }
  return previewOutput;
}
```

<a id="createpreviewoutput-1"></a>

## createPreviewOutput

```TypeScript
createPreviewOutput(surfaceId: string): PreviewOutput
```

Creates a **PreviewOutput** instance without configuration. This API returns the result synchronously. It must be used with [preconfig](arkts-camera-camera-photosession-i.md#preconfig).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| surfaceId | string | Yes | Surface ID, which is obtained from XComponent or [ImageReceiver](../../apis-image-kit/arkts-apis/arkts-image-image-imagereceiver-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [PreviewOutput](arkts-camera-camera-previewoutput-i.md) | **PreviewOutput** instance created. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPreviewOutput(cameraManager: camera.CameraManager, surfaceId: string): camera.PreviewOutput | undefined {
  let previewOutput: camera.PreviewOutput | undefined = undefined;
  try {
    previewOutput = cameraManager.createPreviewOutput(surfaceId);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The createPreviewOutput call failed. error code: ${err.code}`);
  }
  return previewOutput;
}
```

## createSession

```TypeScript
createSession<T extends Session>(mode: SceneMode): T
```

Creates a **Session** instance with a given scene mode. This API returns the result synchronously.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [SceneMode](arkts-camera-camera-scenemode-e.md) | Yes | Scene mode. The API does not take effect if the input parameter is invalid (for example, the value is out of range, null, or undefined). |

**Return value:**

| Type | Description |
| --- | --- |
| T | **Session** instance created. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.<br>**Applicable version:** 19 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createSession(cameraManager: camera.CameraManager, mode: camera.SceneMode): camera.Session | undefined {
  let photoSession: camera.PhotoSession | undefined = undefined;
  try {
    photoSession = cameraManager.createSession(mode) as camera.PhotoSession;
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`createCaptureSession error. error code: ${err.code}`);
  }
  return photoSession;
}
```

## createVideoOutput

```TypeScript
createVideoOutput(profile: VideoProfile, surfaceId: string): VideoOutput
```

Creates a **VideoOutput** instance. This API returns the result synchronously.

In video recording mode, if SDR or HDR VIVID is enabled, the camera format and color space must be configured according to the relationships specified in the table below. Configurations that do not match the table will cause issues such as preview exceptions.

| SDR/HDR Photo Capture | CameraFormat | ColorSpace |  
|--------------------|--------------------------|------------------|  
| SDR | [CAMERA_FORMAT_YUV_420_SP](arkts-camera-camera-cameraformat-e.md) | [BT709_LIMIT](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspace-e.md) |
| HDR_VIVID | [CAMERA_FORMAT_YCRCB_P010](arkts-camera-camera-cameraformat-e.md)<br>CAMERA_FORMAT_YCBCR_P010 | [BT2020_HLG_LIMIT](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspace-e.md)<br>BT2020_HLG_FULL |

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| profile | [VideoProfile](arkts-camera-camera-videoprofile-i.md) | Yes | Supported video profile, which is obtained through [getSupportedOutputCapability](#getsupportedoutputcapability-1). |
| surfaceId | string | Yes | Surface ID, which is obtained from [AVRecorder](../../apis-media-kit/arkts-apis/arkts-media-media-avrecorder-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [VideoOutput](arkts-camera-camera-videooutput-i.md) | **VideoOutput** instance created. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createVideoOutput(cameraOutputCapability: camera.CameraOutputCapability, cameraManager: camera.CameraManager, surfaceId: string): camera.VideoOutput | undefined {
  let profile: camera.VideoProfile = cameraOutputCapability.videoProfiles[0];
  let videoOutput: camera.VideoOutput | undefined = undefined;
  try {
    videoOutput = cameraManager.createVideoOutput(profile, surfaceId);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The createVideoOutput call failed. error code: ${err.code}`);
  }
  return videoOutput;
}
```

<a id="createvideooutput-1"></a>

## createVideoOutput

```TypeScript
createVideoOutput(surfaceId: string): VideoOutput
```

Creates a **VideoOutput** instance without configuration. This API returns the result synchronously. It must be used with [preconfig](arkts-camera-camera-videosession-i.md#preconfig).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| surfaceId | string | Yes | Surface ID, which is obtained from [AVRecorder](../../apis-media-kit/arkts-apis/arkts-media-media-avrecorder-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [VideoOutput](arkts-camera-camera-videooutput-i.md) | **VideoOutput** instance created. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createVideoOutput(cameraManager: camera.CameraManager, surfaceId: string): camera.VideoOutput | undefined {
  let videoOutput: camera.VideoOutput | undefined = undefined;
  try {
    videoOutput = cameraManager.createVideoOutput(surfaceId);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The createVideoOutput call failed. error code: ${err.code}`);
  }
  return videoOutput;
}
```

## getCameraConcurrentInfos

```TypeScript
getCameraConcurrentInfos(cameras: Array<CameraDevice>): Array<CameraConcurrentInfo>
```

Obtains the concurrency information of the specified cameras. If the return value is an empty array, concurrency is not supported.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cameras | Array&lt;[CameraDevice](arkts-camera-camera-cameradevice-i.md)&gt; | Yes | Array of **CameraDevice** objects. You are advised to use the front and rear cameras obtained by calling [getCameraDevice](#getcameradevice). |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[CameraConcurrentInfo](arkts-camera-camera-cameraconcurrentinfo-i.md)&gt; | Array of concurrency information corresponding to the provided CameraDevice objects, with a one-to-one mapping. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { camera } from '@kit.CameraKit';
import { BusinessError } from '@kit.BasicServicesKit';

function getCameraConcurrentInfos(cameraManager: camera.CameraManager,
  cameraDeviceArray: Array<camera.CameraDevice>): Array<camera.CameraConcurrentInfo> {
  let cameraConcurrentInfos: Array<camera.CameraConcurrentInfo> = [];
  try {
    cameraConcurrentInfos = cameraManager.getCameraConcurrentInfos(cameraDeviceArray);
  } catch (error) {
    // If the operation fails, an error code is returned and processed.
    let err = error as BusinessError;
    console.error(`The getCameraConcurrentInfos call failed. error code: ${err.code}`);
  }
  return cameraConcurrentInfos;
}
```

## getCameraDevice

```TypeScript
getCameraDevice(position: CameraPosition, type: CameraType): CameraDevice
```

Obtains the specified camera based on the camera position and type.

Obtains the camera lens of the specified [CameraPosition](arkts-camera-camera-cameraposition-e.md) and [CameraType](arkts-camera-camera-cameratype-e.md). If the returned result is undefined, the camera lens is not found on the current device.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | [CameraPosition](arkts-camera-camera-cameraposition-e.md) | Yes | Camera position. |
| type | [CameraType](arkts-camera-camera-cameratype-e.md) | Yes | Camera type. |

**Return value:**

| Type | Description |
| --- | --- |
| [CameraDevice](arkts-camera-camera-cameradevice-i.md) | Camera obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { camera } from '@kit.CameraKit';
import { BusinessError } from '@kit.BasicServicesKit';

function getCameraDevice(cameraManager: camera.CameraManager, position: camera.CameraPosition, type: camera.CameraType): void {
  try {
    let curCameraDev: camera.CameraDevice | undefined = undefined;
    curCameraDev = cameraManager.getCameraDevice(position, type);
  } catch (error) {
    // If the operation fails, an error code is returned and processed.
    let err = error as BusinessError;
    console.error(`The getCameraDevice call failed. error code: ${err.code}`);
  }
}
```

## getCameraDevices

```TypeScript
getCameraDevices(position: CameraPosition, types: Array<CameraType>, connectType: ConnectionType): Array<CameraDevice>
```

Obtains the list of cameras that meet the search criteria based on the camera position, camera types, and connection type.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | [CameraPosition](arkts-camera-camera-cameraposition-e.md) | Yes | Camera position. |
| types | Array&lt;[CameraType](arkts-camera-camera-cameratype-e.md)&gt; | Yes | Array of camera types. |
| connectType | [ConnectionType](arkts-camera-camera-connectiontype-e.md) | Yes | Camera connection type. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[CameraDevice](arkts-camera-camera-cameradevice-i.md)&gt; | Array of cameras that meet the search criteria. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { camera } from '@kit.CameraKit';
import { BusinessError } from '@kit.BasicServicesKit';

function getCameraDevices(cameraManager: camera.CameraManager, position: camera.CameraPosition, types: Array<camera.CameraType>, connectType: camera.ConnectionType): void {
  try {
    let cameraDevs: Array<camera.CameraDevice> = [];
    cameraDevs = cameraManager.getCameraDevices(position, types, connectType);
  } catch (error) {
    // If the operation fails, an error code is returned and processed.
    let err = error as BusinessError;
    console.error(`The getCameraDevices call failed. error code: ${err.code}`);
  }
}
```

## getSupportedCameras

```TypeScript
getSupportedCameras(): Array<CameraDevice>
```

Obtains the supported cameras (such as the default camera whose **CameraType** is **CAMERA_TYPE_DEFAULT**). This API returns the result synchronously.

Other cameras (such as the telephoto camera whose **CameraType** is **CAMERA_TYPE_TELEPHOTO**) can be obtained using [getCameraDevices](#getcameradevices) API.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[CameraDevice](arkts-camera-camera-cameradevice-i.md)&gt; | Array of camera devices supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getSupportedCameras(cameraManager: camera.CameraManager): Array<camera.CameraDevice> {
  let cameras: Array<camera.CameraDevice> = [];
  try {
    cameras = cameraManager.getSupportedCameras();
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The getSupportedCameras call failed. error code: ${err.code}`);
  }
  return cameras;
}
```

## getSupportedFullOutputCapability

```TypeScript
getSupportedFullOutputCapability(camera: CameraDevice, mode: SceneMode): CameraOutputCapability
```

Obtains the complete output capabilities supported by a specified camera in a specified mode, including YUV, HEIF, and HDR.

> **NOTE:** 
> 
> Before using YUV, HEIF, or HDR, you need to explicitly call this method to ensure that the complete output
> capabilities are obtained.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| camera | [CameraDevice](arkts-camera-camera-cameradevice-i.md) | Yes | Camera device. |
| mode | [SceneMode](arkts-camera-camera-scenemode-e.md) | Yes | Scene mode. |

**Return value:**

| Type | Description |
| --- | --- |
| [CameraOutputCapability](arkts-camera-camera-cameraoutputcapability-i.md) | Camera output capability obtained. |

**Examples**

```TypeScript
import { camera } from '@kit.CameraKit';

function getSupportedFullOutputCapability(camera: camera.CameraDevice, cameraManager: camera.CameraManager, sceneMode: camera.SceneMode): camera.CameraOutputCapability {
  let cameraOutputCapability: camera.CameraOutputCapability = cameraManager.getSupportedFullOutputCapability(camera, sceneMode);
  return cameraOutputCapability;
}
```

## getSupportedOutputCapability

```TypeScript
getSupportedOutputCapability(camera: CameraDevice): CameraOutputCapability
```

Obtains the output capability supported by a camera device. This API returns the result synchronously.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [getSupportedOutputCapability](#getsupportedoutputcapability-1)(camera: CameraDevice, mode: SceneMode)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| camera | [CameraDevice](arkts-camera-camera-cameradevice-i.md) | Yes | Camera device. |

**Return value:**

| Type | Description |
| --- | --- |
| [CameraOutputCapability](arkts-camera-camera-cameraoutputcapability-i.md) | Camera output capability obtained. |

**Examples**

```TypeScript
function getSupportedOutputCapability(camera: camera.CameraDevice, cameraManager: camera.CameraManager): camera.CameraOutputCapability {
  let cameraOutputCapability: camera.CameraOutputCapability = cameraManager.getSupportedOutputCapability(camera);
  return cameraOutputCapability;
}
```

<a id="getsupportedoutputcapability-1"></a>

## getSupportedOutputCapability

```TypeScript
getSupportedOutputCapability(camera: CameraDevice, mode: SceneMode): CameraOutputCapability
```

Obtains the output capability supported by a camera device in a given scene mode. This API returns the result synchronously.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| camera | [CameraDevice](arkts-camera-camera-cameradevice-i.md) | Yes | Camera device. |
| mode | [SceneMode](arkts-camera-camera-scenemode-e.md) | Yes | Scene mode. |

**Return value:**

| Type | Description |
| --- | --- |
| [CameraOutputCapability](arkts-camera-camera-cameraoutputcapability-i.md) | Camera output capability obtained. |

**Examples**

```TypeScript
function getSupportedOutputCapability(camera: camera.CameraDevice, cameraManager: camera.CameraManager, sceneMode: camera.SceneMode): camera.CameraOutputCapability {
  let cameraOutputCapability: camera.CameraOutputCapability = cameraManager.getSupportedOutputCapability(camera, sceneMode);
  return cameraOutputCapability;
}
```

## getSupportedSceneModes

```TypeScript
getSupportedSceneModes(camera: CameraDevice): Array<SceneMode>
```

Obtains the scene modes supported by a camera device. This API returns the result synchronously.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| camera | [CameraDevice](arkts-camera-camera-cameradevice-i.md) | Yes | Camera device. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[SceneMode](arkts-camera-camera-scenemode-e.md)&gt; | Array of scene modes supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getSupportedSceneModes(cameraManager: camera.CameraManager, camera: camera.CameraDevice): Array<camera.SceneMode> {
  let modes: Array<camera.SceneMode> = [];
  try {
    modes = cameraManager.getSupportedSceneModes(camera);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The getSupportedSceneModes call failed. error code: ${err.code}`);
  }
  return modes;
}
```

## getTorchMode

```TypeScript
getTorchMode(): TorchMode
```

Obtains the flashlight mode of this camera device.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| [TorchMode](arkts-camera-camera-torchmode-e.md) | Flashlight mode. |

**Examples**

```TypeScript
function getTorchMode(cameraManager: camera.CameraManager): camera.TorchMode | undefined {
  let torchMode: camera.TorchMode | undefined = undefined;
  torchMode = cameraManager.getTorchMode();
  return torchMode;
}
```

## isCameraMuted

```TypeScript
isCameraMuted(): boolean
```

Checks whether this camera is muted.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the camera is muted. **true** if muted, **false** otherwise. |

**Examples**

```TypeScript
function isCameraMuted(cameraManager: camera.CameraManager): boolean {
  let isMuted: boolean = cameraManager.isCameraMuted();
  return isMuted;
}
```

## isTorchLevelControlSupported

```TypeScript
isTorchLevelControlSupported(): boolean
```

Checks whether the device supports flashlight brightness control.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the device supports flashlight brightness control. Returns **true** if supported, **false** if not. If the API call fails, undefined is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application.<br>**Applicable version:** 23 - 24 |

**Examples**

```TypeScript
function isTorchLevelControlSupported(cameraManager: camera.CameraManager): boolean {
  let isSupported = cameraManager.isTorchLevelControlSupported();
  return isSupported;
}
```

## isTorchModeSupported

```TypeScript
isTorchModeSupported(mode: TorchMode): boolean
```

Checks whether a flashlight mode is supported.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [TorchMode](arkts-camera-camera-torchmode-e.md) | Yes | Flashlight mode. If the input parameter is null or undefined, it is treated as 0 and the flashlight is turned off. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of the flashlight mode. **true** if supported, **false** otherwise. If the API call fails, undefined is returned. |

**Examples**

```TypeScript
function isTorchModeSupported(cameraManager: camera.CameraManager, torchMode: camera.TorchMode): boolean {
  let isSupported = cameraManager.isTorchModeSupported(torchMode);
  return isSupported;
}
```

## isTorchSupported

```TypeScript
isTorchSupported(): boolean
```

Checks whether the camera device supports the flashlight.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the device supports the flashlight. **true** if supported, **false** otherwise. <br>If **false** is returned, [isTorchModeSupported](#istorchmodesupported), [getTorchMode](#gettorchmode), [setTorchMode](#settorchmode), [isTorchLevelControlSupported](#istorchlevelcontrolsupported), and [setTorchModeOnWithLevel](../../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#settorchmodeonwithlevel) do not take effect. <br>If the API call fails, undefined is returned. |

**Examples**

```TypeScript
function isTorchSupported(cameraManager: camera.CameraManager): boolean {
  let isSupported = cameraManager.isTorchSupported();
  return isSupported;
}
```

## off('cameraStatus')

```TypeScript
off(type: 'cameraStatus', callback?: AsyncCallback<CameraStatusInfo>): void
```

Unsubscribes from camera status events. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'cameraStatus' | Yes | Event type. The value is fixed at **'cameraStatus'**. The event can be listened for when a **CameraManager** instance is obtained. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CameraStatusInfo](arkts-camera-camera-camerastatusinfo-i.md)&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

**Examples**

```TypeScript
function unregisterCameraStatus(cameraManager: camera.CameraManager): void {
  cameraManager.off('cameraStatus');
}
```

## off('foldStatusChange')

```TypeScript
off(type: 'foldStatusChange', callback?: AsyncCallback<FoldStatusInfo>): void
```

Unsubscribes from fold state change events of the foldable device.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'foldStatusChange' | Yes | Event type. The value is fixed at **'foldStatusChange'**. The event is triggered when the fold state of the foldable device changes. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FoldStatusInfo](arkts-camera-camera-foldstatusinfo-i.md)&gt; | No | Callback used to return the fold state information about the foldable device. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

**Examples**

```TypeScript
function unregisterFoldStatusChange(cameraManager: camera.CameraManager): void {
  cameraManager.off('foldStatusChange');
}
```

## off('torchStatusChange')

```TypeScript
off(type: 'torchStatusChange', callback?: AsyncCallback<TorchStatusInfo>): void
```

Unsubscribes from flashlight status change events. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'torchStatusChange' | Yes | Event type. The value is fixed at **'torchStatusChange'**. The event can be listened for when a **CameraManager** instance is obtained. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[TorchStatusInfo](arkts-camera-camera-torchstatusinfo-i.md)&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

**Examples**

```TypeScript
function unregisterTorchStatusChange(cameraManager: camera.CameraManager): void {
  cameraManager.off('torchStatusChange');
}
```

## on('cameraStatus')

```TypeScript
on(type: 'cameraStatus', callback: AsyncCallback<CameraStatusInfo>): void
```

Subscribes to camera status events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'cameraStatus' | Yes | Event type. The value is fixed at **'cameraStatus'**. The event can be listened for when a **CameraManager** instance is obtained. This event is triggered and the corresponding information is returned only when the camera device is enabled or disabled. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CameraStatusInfo](arkts-camera-camera-camerastatusinfo-i.md)&gt; | Yes | Callback used to return the camera status change. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, cameraStatusInfo: camera.CameraStatusInfo): void {
  if (err !== undefined && err.code !== 0) {
    console.error('cameraStatus with errorCode = ' + err.code);
    return;
  }
  console.info(`camera : ${cameraStatusInfo.camera.cameraId}`);
  console.info(`status: ${cameraStatusInfo.status}`);
}

function registerCameraStatus(cameraManager: camera.CameraManager): void {
  cameraManager.on('cameraStatus', callback);
}
```

## on('foldStatusChange')

```TypeScript
on(type: 'foldStatusChange', callback: AsyncCallback<FoldStatusInfo>): void
```

Subscribes to fold status change events of the foldable device. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'foldStatusChange' | Yes | Event type. The value is fixed at **'foldStatusChange'**. The event is triggered when the fold state of the foldable device changes. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FoldStatusInfo](arkts-camera-camera-foldstatusinfo-i.md)&gt; | Yes | Callback used to return the fold state information about the foldable device. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, foldStatusInfo: camera.FoldStatusInfo): void {
  if (err !== undefined && err.code !== 0) {
    console.error('foldStatusChange with errorCode = ' + err.code);
    return;
  }
  console.info(`camera length: ${foldStatusInfo.supportedCameras.length}`);
  console.info(`foldStatus: ${foldStatusInfo.foldStatus}`);
}

function registerFoldStatusChange(cameraManager: camera.CameraManager): void {
  cameraManager.on('foldStatusChange', callback);
}
```

## on('torchStatusChange')

```TypeScript
on(type: 'torchStatusChange', callback: AsyncCallback<TorchStatusInfo>): void
```

Subscribes to flashlight status change events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'torchStatusChange' | Yes | Event type. The value is fixed at **'torchStatusChange'**. The event can be listened for when a **CameraManager** instance is obtained. Currently, this event is triggered only in the following scenarios: The flashlight is turned on or turned off, or becomes unavailable or available. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[TorchStatusInfo](arkts-camera-camera-torchstatusinfo-i.md)&gt; | Yes | Callback used to return the flashlight status. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, torchStatusInfo: camera.TorchStatusInfo): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`onTorchStatusChange, isTorchAvailable: ${torchStatusInfo.isTorchAvailable}, isTorchActive: ${torchStatusInfo.isTorchActive}, level: ${torchStatusInfo.torchLevel}`);
}

function registerTorchStatusChange(cameraManager: camera.CameraManager): void {
  cameraManager.on('torchStatusChange', callback);
}
```

## setTorchMode

```TypeScript
setTorchMode(mode: TorchMode): void
```

Sets the flashlight mode.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [TorchMode](arkts-camera-camera-torchmode-e.md) | Yes | Flashlight mode. If the input parameter is null or undefined, it is treated as 0 and the flashlight is turned off. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect.<br>**Applicable version:** 11 - 17 |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed.<br>**Applicable version:** 12 and later |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setTorchMode(cameraManager: camera.CameraManager, torchMode: camera.TorchMode): void {
  try {
    cameraManager.setTorchMode(torchMode);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The setTorchMode call failed. error code: ${err.code}`);
  }
}
```

## setTorchModeOnWithLevel

```TypeScript
setTorchModeOnWithLevel(torchLevel: number): void
```

Sets the torch mode to [ON](arkts-camera-camera-torchmode-e.md#on) with the specified torch level.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| torchLevel | number | Yes | the specified torch level, the value range is [0.0, 1.0] |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application.<br>**Applicable version:** 23 - 24 |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
function SetTorchModeOnWithLevel(cameraManager: camera.CameraManager, torchLevel: number): void {
  cameraManager.setTorchModeOnWithLevel(torchLevel);
  return ;
}
```
