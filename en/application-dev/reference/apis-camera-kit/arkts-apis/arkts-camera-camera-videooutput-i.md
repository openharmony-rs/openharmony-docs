# VideoOutput

```TypeScript
interface VideoOutput extends CameraOutput
```

VideoOutput implements output information used in a video session. It inherits from [CameraOutput](arkts-camera-camera-cameraoutput-i.md).

**Inheritance/Implementation:** VideoOutput extends [CameraOutput](arkts-camera-camera-cameraoutput-i.md)

**Since:** 10

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## enableMirror

```TypeScript
enableMirror(enabled: boolean): void
```

Enables or disables mirror recording.

- Before calling this API, check whether mirror recording is supported by using [isMirrorSupported](#ismirrorsupported).  
- After enabling or disabling mirror recording, call [getVideoRotation](#getvideorotation) to obtain the rotation angle and [updateRotation](../../apis-media-kit/arkts-apis/arkts-media-media-avrecorder-i.md#updaterotation) to update the rotation angle.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable mirror recording. **true** to enable, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application.<br>**Applicable version:** 12 - 14 |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

**Examples**

```TypeScript
import { camera } from '@kit.CameraKit';
import { media } from '@kit.MediaKit';
import { BusinessError } from '@kit.BasicServicesKit';

function enableMirror(videoOutput: camera.VideoOutput, mirrorMode: boolean, aVRecorder: media.AVRecorder, deviceDegree : number): void {
    try {
        videoOutput.enableMirror(mirrorMode);
        aVRecorder.updateRotation(videoOutput.getVideoRotation(deviceDegree));
    } catch (error) {
        let err = error as BusinessError;
    }
}
```

## getActiveFrameRate

```TypeScript
getActiveFrameRate(): FrameRateRange
```

Obtains the configured frame rate range.

This API is valid only after [setFrameRate](#setframerate) is called to set a frame rate range for video streams.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| [FrameRateRange](arkts-camera-camera-frameraterange-i.md) | Frame rate range. |

**Examples**

```TypeScript
function getActiveFrameRate(videoOutput: camera.VideoOutput): camera.FrameRateRange {
  let activeFrameRate: camera.FrameRateRange = videoOutput.getActiveFrameRate();
  return activeFrameRate;
}
```

## getActiveProfile

```TypeScript
getActiveProfile(): VideoProfile
```

Obtains the profile that takes effect currently.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| [VideoProfile](arkts-camera-camera-videoprofile-i.md) | Profile obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function testGetActiveProfile(videoOutput: camera.VideoOutput): camera.Profile | undefined {
  let activeProfile: camera.VideoProfile | undefined = undefined;
  try {
    activeProfile = videoOutput.getActiveProfile();
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The videoOutput.getActiveProfile call failed. error code: ${err.code}`);
  }
  return activeProfile;
}
```

## getSupportedFrameRates

```TypeScript
getSupportedFrameRates(): Array<FrameRateRange>
```

Obtains the supported frame rates.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[FrameRateRange](arkts-camera-camera-frameraterange-i.md)&gt; | Array of supported frame rates. If the API call fails, undefined is returned. |

**Examples**

```TypeScript
function getSupportedFrameRates(videoOutput: camera.VideoOutput): Array<camera.FrameRateRange> {
  let supportedFrameRatesArray: Array<camera.FrameRateRange> = videoOutput.getSupportedFrameRates();
  return supportedFrameRatesArray;
}
```

## getVideoRotation

```TypeScript
getVideoRotation(deviceDegree?: number): ImageRotation
```

Obtains the video rotation angle.

- Device' natural orientation: the default orientation for using a device. For example, the default orientation  
of the bar-type phone is in portrait mode, with the charging port facing downward.  
- Camera lens angle: equivalent to the angle at which the camera is rotated clockwise to match the device's  
natural orientation. For example, the rear camera sensor of a bar-type phone is installed in landscape mode. Therefore, it needs to be rotated by 90 degrees clockwise to match the device's natural orientation.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceDegree | number | No | Device rotation angle, measured in degrees, within the range of [0, 360].<br> Since API version 23, the input parameter **deviceDegree** is optional. If no parameter is passed, the system obtains the **deviceDegree** value to calculate the video rotation angle.<br>**Since:** 23 |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageRotation](arkts-camera-camera-imagerotation-e.md) | Returns the rotation angle of a video. If the API call fails, undefined is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect.<br>**Applicable version:** 12 - 22 |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { camera } from '@kit.CameraKit';
import { Decimal } from '@kit.ArkTS';
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function getVideoRotation(videoOutput: camera.VideoOutput): Promise<camera.ImageRotation> {
  let deviceDegree = await getDeviceDegree();
  let videoRotation: camera.ImageRotation = camera.ImageRotation.ROTATION_0;
  try {
    videoRotation = videoOutput.getVideoRotation(deviceDegree);
  } catch (error) {
    let err = error as BusinessError;
    console.error('Failed to get video rotation: ' + JSON.stringify(err));
  }
  return videoRotation;
}

function testGetVideoRotationWithOutParam(videoOutput: camera.VideoOutput): camera.ImageRotation {
  let videoRotation: camera.ImageRotation = camera.ImageRotation.ROTATION_0;
  try {
    videoRotation = videoOutput.getVideoRotation();
    console.info(`Video rotation is: ${videoRotation}`);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The videoOutput.testGetVideoRotationWithOutParam call failed. error code: ${err.code}`);
  }
  return videoRotation;
}

// Obtain the device rotation degree.
function getDeviceDegree(): Promise<number> {
  return new Promise<number>((resolve) => {
    try {
      sensor.once(sensor.SensorId.GRAVITY, (data: sensor.GravityResponse) => {
        console.info('Succeeded in invoking once. X-coordinate component: ' + data.x);
        console.info('Succeeded in invoking once. Y-coordinate component: ' + data.y);
        console.info('Succeeded in invoking once. Z-coordinate component: ' + data.z);
        let x = data.x;
        let y = data.y;
        let z = data.z;
        let deviceDegree: number;
        if ((x * x + y * y) * 3 < z * z) {
          deviceDegree = -1;
        } else {
          let sd: Decimal = Decimal.atan2(y, -x);
          let sc: Decimal = Decimal.round(Number(sd) / 3.141592653589 * 180)
          deviceDegree = 90 - Number(sc);
          deviceDegree = deviceDegree >= 0 ? deviceDegree% 360 : deviceDegree% 360 + 360;
        }
        resolve(deviceDegree);
      });
    } catch (error) {
      let err = error as BusinessError;
      console.error('Failed to register gravity sensor: ' + JSON.stringify(err));
      resolve(-1); // Return the default value when an exception occurs.
    }
  });
}
```

## isMirrorSupported

```TypeScript
isMirrorSupported(): boolean
```

Checks whether mirror recording is supported.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of mirror recording. **true** if supported, **false** otherwise. If the API call fails, undefined is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application.<br>**Applicable version:** 12 - 14 |

**Examples**

```TypeScript
function testIsMirrorSupported(videoOutput: camera.VideoOutput): boolean {
  let isSupported: boolean = videoOutput.isMirrorSupported();
  return isSupported;
}
```

## off('frameStart')

```TypeScript
off(type: 'frameStart', callback?: AsyncCallback<void>): void
```

Unsubscribes from video recording start events.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'frameStart' | Yes | Event type. The value is fixed at **'frameStart'**. The event can be listened for when a videoOutput instance is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

**Examples**

```TypeScript
function unregisterVideoOutputFrameStart(videoOutput: camera.VideoOutput): void {
  videoOutput.off('frameStart');
}
```

## off('frameEnd')

```TypeScript
off(type: 'frameEnd', callback?: AsyncCallback<void>): void
```

Unsubscribes from video recording stop events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'frameEnd' | Yes | Event type. The value is fixed at **'frameEnd'**. The event can be listened for when a videoOutput instance is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

**Examples**

```TypeScript
function unregisterVideoOutputFrameEnd(videoOutput: camera.VideoOutput): void {
  videoOutput.off('frameEnd');
}
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from VideoOutput error events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. The value is fixed at **'error'**. The event can be listened for when a photoOutput instance is created. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

**Examples**

```TypeScript
function unregisterVideoOutputError(videoOutput: camera.VideoOutput): void {
  videoOutput.off('error');
}
```

## on('frameStart')

```TypeScript
on(type: 'frameStart', callback: AsyncCallback<void>): void
```

Subscribes to video recording start events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'frameStart' | Yes | Event type. The value is fixed at **'frameStart'**. The event can be listened for when a videoOutput instance is created. The event is triggered and the corresponding information is returned when the bottom layer starts exposure for the first time. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. The recording starts as long as this event is returned. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError): void {
  if (err.code) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info('Video frame started');
}

function registerVideoOutputFrameStart(videoOutput: camera.VideoOutput): void {
  videoOutput.on('frameStart', callback);
}
```

## on('frameEnd')

```TypeScript
on(type: 'frameEnd', callback: AsyncCallback<void>): void
```

Subscribes to video recording stop events. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'frameEnd' | Yes | Event type. The value is fixed at **'frameEnd'**. The event can be listened for when a videoOutput instance is created. This event is triggered and returned when the last frame of recording is complete. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. The recording ends as long as this event is returned. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError): void {
  if (err.code) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info('Video frame ended');
}

function registerVideoOutputFrameEnd(videoOutput: camera.VideoOutput): void {
  videoOutput.on('frameEnd', callback);
}
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to VideoOutput error events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. The value is fixed at **'error'**. The event can be listened for when a videoOutput instance is created. This event is triggered and the corresponding error message is returned when an error occurs during the use of a recording-related API such as [start](#start) or [CameraOutput.release](arkts-camera-camera-cameraoutput-i.md#release). |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to return an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md). |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError): void {
  console.error(`Video output error code: ${err.code}`);
}

function registerVideoOutputError(videoOutput: camera.VideoOutput): void {
  videoOutput.on('error', callback);
}
```

## setFrameRate

```TypeScript
setFrameRate(minFps: number, maxFps: number): void
```

Sets a frame rate range for video streams. The range must be within the supported frame rate range,

which can be obtained by calling [getSupportedFrameRates](#getsupportedframerates).

> **NOTE:** 
> 
> This API is valid only in [PhotoSession](arkts-camera-camera-photosession-i.md) or
> [VideoSession](arkts-camera-camera-videosession-i.md) mode.
> 
> Before calling this API, call [getActiveFrameRate](#getactiveframerate) to obtain the
> current frame rate of the video session. If the delivered frame rate matches the current frame rate, the
> delivered frame rate is not applied.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| minFps | number | Yes | Minimum frame rate, in fps. When the maximum value is less than the minimum value, the API does not take effect. |
| maxFps | number | Yes | Maximum frame rate, in fps. When the minimum value is greater than the maximum value, the API does not take effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400110](../errorcode-camera.md#7400110-configuration-conflicts) | Unresolved conflicts with current configurations. |

**Examples**

```TypeScript
function setFrameRateRange(videoOutput: camera.VideoOutput, frameRateRange: Array<number>): void {
  videoOutput.setFrameRate(frameRateRange[0], frameRateRange[1]);
}
```

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

Starts video recording. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If video recording starts successfully, **err** is **undefined**; otherwise, **err** is an error object with an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function startVideoOutput(videoOutput: camera.VideoOutput): void {
  videoOutput.start((err: BusinessError) => {
    if (err.code) {
      console.error(`Failed to start the video output, error code: ${err.code}.`);
      return;
    }
    console.info('Callback invoked to indicate the video output start success.');
  });
}
```

<a id="start-1"></a>

## start

```TypeScript
start(): Promise<void>
```

Starts video recording. This API uses a promise to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function startVideoOutput(videoOutput: camera.VideoOutput): void {
  videoOutput.start().then(() => {
    console.info('Promise returned to indicate that start method execution success.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to video output start, error code: ${error.code}.`);
  });
}
```

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

Stops video recording. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If video recording stops successfully, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
function stopVideoOutput(videoOutput: camera.VideoOutput): void {
  videoOutput.stop(() => {
    console.info('Callback invoked to indicate the video output stop success.');
  });
}
```

<a id="stop-1"></a>

## stop

```TypeScript
stop(): Promise<void>
```

Stops video recording. This API uses a promise to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function stopVideoOutput(videoOutput: camera.VideoOutput): void {
  videoOutput.stop().then(() => {
    console.info('Promise returned to indicate that stop method execution success.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to video output stop, error code: ${error.code}.`);
  });
}
```
