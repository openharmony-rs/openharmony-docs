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

## createCameraInputWithTokenId

```TypeScript
createCameraInputWithTokenId(camera: CameraDevice, tokenId: number): CameraInput
```

Creates a CameraInput instance by camera and calling token.

Before using this interface, first through the getSupportedCameras interface to query the current list of camera devices supported by the device, the developer needs to be based on specific scenarios to choose the camera device that meets the needs of the developer, and then use this interface to create a CameraInput instance.

**Since:** 24

**Required permissions:** ohos.permission.CAMERA

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| camera | [CameraDevice](arkts-camera-camera-cameradevice-i.md) | Yes | Camera device used to create the instance. |
| tokenId | number | Yes | The calling token id. |

**Return value:**

| Type | Description |
| --- | --- |
| [CameraInput](arkts-camera-camera-camerainput-i.md) | Returns a CameraInput instance. Failure of an interface call returns the corresponding error code, which is of type CameraErrorCode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

## createControlCenterSession

```TypeScript
createControlCenterSession(): ControlCenterSession
```

Create a ControlCenterSession instance.

**Since:** 20

**Required permissions:** ohos.permission.CAMERA_CONTROL

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [ControlCenterSession](arkts-camera-camera-controlcentersession-i-sys.md) | the ControlCenterSession instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

## createDepthDataOutput

```TypeScript
createDepthDataOutput(profile: DepthProfile): DepthDataOutput
```

Creates a DepthDataOutput instance. This API returns the result synchronously.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| profile | [DepthProfile](arkts-camera-camera-depthprofile-i-sys.md) | Yes | Supported preview profile, which is obtained through  [getSupportedOutputCapability](arkts-camera-camera-cameramanager-i.md#getsupportedoutputcapability-1). |

**Return value:**

| Type | Description |
| --- | --- |
| [DepthDataOutput](arkts-camera-camera-depthdataoutput-i-sys.md) | DepthDataOutput instance. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createDepthDataOutput(cameraOutputCapability: camera.CameraOutputCapability, cameraManager: camera.CameraManager): camera.DepthDataOutput | undefined {
  let profile: camera.DepthProfile = cameraOutputCapability.depthProfiles[0];
  let depthDataOutput: camera.DepthDataOutput | undefined = undefined;
  try {
    depthDataOutput = cameraManager.createDepthDataOutput(profile);
  } catch (error) {
    // Return the error code error.code on failure and handle it.
    let err = error as BusinessError;
    console.error(`The createDepthDataOutput call failed. error code: ${err.code}`);
  }
  return depthDataOutput;
}
```

## isCameraMuteSupported

```TypeScript
isCameraMuteSupported(): boolean
```

Checks whether the camera device can be muted.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the camera device can be muted. **true** if it can be muted, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 13 and later |

**Examples**

```TypeScript
function isCameraMuteSupported(cameraManager: camera.CameraManager): boolean {
  let isMuteSupported: boolean = cameraManager.isCameraMuteSupported();
  return isMuteSupported;
}
```

## isControlCenterActive

```TypeScript
isControlCenterActive(): boolean
```

Check if the control center active.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | this value that specifies whether the control center active. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

## isPrelaunchSupported

```TypeScript
isPrelaunchSupported(camera: CameraDevice): boolean
```

Checks whether a camera device supports prelaunch.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| camera | [CameraDevice](arkts-camera-camera-cameradevice-i.md) | Yes | Camera device. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of prelaunch. **true** if supported, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { common } from '@kit.AbilityKit';

function isPreLaunchSupported(context: common.BaseContext): boolean {
  let cameraManager: camera.CameraManager = camera.getCameraManager(context);
  let cameras: Array<camera.CameraDevice> = cameraManager.getSupportedCameras();
  let isSupported: boolean = false;
  if (cameras && cameras.length >= 1) {
    isSupported = cameraManager.isPrelaunchSupported(cameras[0]);
    console.info(`PreLaunch supported states: ${isSupported}`);
    return isSupported;
  }
  return isSupported;
}
```

## muteCamera

```TypeScript
muteCamera(mute: boolean): void
```

Mutes or unmutes the camera device.

**Since:** 10

**Deprecated since:** 12

**Substitutes:** [muteCameraPersistent](#mutecamerapersistent)

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mute | boolean | Yes | Mutes or unmutes the camera device. **true** to mute, **false** otherwise. |

**Examples**

```TypeScript
function muteCamera(cameraManager: camera.CameraManager): void {
  let mute: boolean = true;
  cameraManager.muteCamera(mute);
}
```

## muteCameraPersistent

```TypeScript
muteCameraPersistent(mute: boolean, type: PolicyType): void
```

Mutes the camera device permanently.

**Since:** 12

**Required permissions:** ohos.permission.CAMERA_CONTROL

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mute | boolean | Yes | Mutes or unmutes the camera device. **true** to mute, **false** otherwise. |
| type | [PolicyType](arkts-camera-camera-policytype-e-sys.md) | Yes | Policy type. For details about the available options, see [PolicyType](arkts-camera-camera-policytype-e-sys.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |

**Examples**

```TypeScript
function muteCameraPersistent(cameraManager: camera.CameraManager): void {
  let mute: boolean = true;
  cameraManager.muteCameraPersistent(mute, camera.PolicyType.PRIVACY);
}
```

## off('cameraMute')

```TypeScript
off(type: 'cameraMute', callback?: AsyncCallback<boolean>): void
```

Unsubscribes from camera mute status events.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'cameraMute' | Yes | Event type. The value is fixed at **'cameraMute'**, indicating the camera mute status. The event can be listened for when a CameraManager instance is obtained. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | No | Callback used to return the camera mute status. **true** if muted, **false** otherwise. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('cameraMute')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 13 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, curMuted: boolean): void {
  let isMuted: boolean = curMuted;
}

function unregisterCameraMute(cameraManager: camera.CameraManager): void {
  cameraManager.off('cameraMute', callback);
}
```

## off('controlCenterStatusChange')

```TypeScript
off(type: 'controlCenterStatusChange', callback?: AsyncCallback<boolean>): void
```

Unsubscribes control center status change event callback.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'controlCenterStatusChange' | Yes | Event type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | No | Callback used to get the control center status change. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

## offCameraSharedStatus

```TypeScript
offCameraSharedStatus(callback?: Callback<CameraSharedStatusInfo>): void
```

Unsubscribes from camera shared status change event callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CameraSharedStatusInfo](arkts-camera-camera-camerasharedstatusinfo-i-sys.md)&gt; | No | Callback used to get the camera shared status change. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

## on('cameraMute')

```TypeScript
on(type: 'cameraMute', callback: AsyncCallback<boolean>): void
```

Subscribes to camera mute status events. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'cameraMute' | Yes | Event type. The value is fixed at **'cameraMute'**, indicating the camera mute status. The event can be listened for when a CameraManager instance is obtained. This event is triggered and the status is returned when the camera device is muted or unmuted. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the camera mute status. **true** if muted, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 13 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, curMuted: boolean): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  let isMuted: boolean = curMuted;
  console.info(`cameraMute status: ${isMuted}`);
}

function registerCameraMute(cameraManager: camera.CameraManager): void {
  cameraManager.on('cameraMute', callback);
}
```

## on('controlCenterStatusChange')

```TypeScript
on(type: 'controlCenterStatusChange', callback: AsyncCallback<boolean>): void
```

Subscribes control center status change event callback.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'controlCenterStatusChange' | Yes | Event type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to get the control center status change. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

## onCameraSharedStatus

```TypeScript
onCameraSharedStatus(callback: Callback<CameraSharedStatusInfo>): void
```

Subscribes camera shared status change event callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CameraSharedStatusInfo](arkts-camera-camera-camerasharedstatusinfo-i-sys.md)&gt; | Yes | Callback used to get the camera shared status change. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

## prelaunch

```TypeScript
prelaunch(): void
```

Prelaunches the camera device. This API is called when a user clicks the system camera icon to start the camera application.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application.<br>**Applicable version:** 13 and later |

**Examples**

```TypeScript
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { camera } from '@kit.CameraKit';

function preLaunch(context: common.BaseContext): void {
  let cameraManager: camera.CameraManager = camera.getCameraManager(context);
  try {
    cameraManager.prelaunch();
  } catch (error) {
    let err = error as BusinessError;
    console.error(`prelaunch error. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## preSwitchCamera

```TypeScript
preSwitchCamera(cameraId: string): void
```

Pre-switches a camera device to speed up its startup.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cameraId | string | Yes | Camera ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function preSwitch(cameraDevice: camera.CameraDevice, context: common.BaseContext): void {
  let cameraManager: camera.CameraManager = camera.getCameraManager(context);
  try {
    cameraManager.preSwitchCamera(cameraDevice.cameraId);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`prelaunch error. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## setPrelaunchConfig

```TypeScript
setPrelaunchConfig(prelaunchConfig: PrelaunchConfig): void
```

Sets prelaunch configuration. Before the setting, call [isPrelaunchSupported](#isprelaunchsupported) to check whether the camera device supports prelaunch.

**Since:** 10

**Required permissions:** ohos.permission.CAMERA

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| prelaunchConfig | [PrelaunchConfig](arkts-camera-camera-prelaunchconfig-i-sys.md) | Yes | Prelaunch configuration. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application.<br>**Applicable version:** 12 and later |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function setPrelaunchConfig(context: common.BaseContext): void {
  let cameraManager: camera.CameraManager = camera.getCameraManager(context);
  let cameras: Array<camera.CameraDevice> = cameraManager.getSupportedCameras();
  if (cameras && cameras.length >= 1) {
    let cameraDevice: camera.CameraDevice = cameras[0];
    if(cameraManager.isPrelaunchSupported(cameraDevice)) {
      try {
        cameraManager.setPrelaunchConfig({cameraDevice: cameraDevice});
      } catch (error) {
        let err = error as BusinessError;
        console.error(`setPrelaunchConfig error. Code: ${err.code}, message: ${err.message}`);
      }
    }
  }
}
```
