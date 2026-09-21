# Session

```TypeScript
interface Session
```

**Session** implements a session, which saves all [CameraInput](arkts-camera-camera-camerainput-i.md) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md) instances required to run the camera and requests the camera to take a photo or record a video.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## addInput

```TypeScript
addInput(cameraInput: CameraInput): void
```

Adds a [CameraInput](arkts-camera-camera-camerainput-i.md) instance to this session.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cameraInput | [CameraInput](arkts-camera-camera-camerainput-i.md) | Yes | **CameraInput** instance to add. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config.<br>**Applicable version:** 11 - 17 |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function addInput(session: camera.Session, cameraInput: camera.CameraInput): void {
  try {
    session.addInput(cameraInput);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The addInput call failed. error code: ${err.code}`);
  }
}
```

## addOutput

```TypeScript
addOutput(cameraOutput: CameraOutput): void
```

Adds a [CameraOutput](arkts-camera-camera-cameraoutput-i.md) instance to this session.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cameraOutput | [CameraOutput](arkts-camera-camera-cameraoutput-i.md) | Yes | **CameraOutput** instance to add. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config.<br>**Applicable version:** 11 - 17 |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function addOutput(session: camera.Session, cameraOutput: camera.CameraOutput): void {
  try {
    session.addOutput(cameraOutput);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The addOutput call failed. error code: ${err.code}`);
  }
}
```

## beginConfig

```TypeScript
beginConfig(): void
```

Starts configuration for the session.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400105](../errorcode-camera.md#7400105-session-configuration-locked) | Session config locked. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function beginConfig(session: camera.Session): void {
  try {
    session.beginConfig();
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The beginConfig call failed. error code: ${err.code}`);
  }
}
```

## canAddInput

```TypeScript
canAddInput(cameraInput: CameraInput): boolean
```

Checks whether a **CameraInput** instance can be added to this session. This API must be called after [beginConfig](#beginconfig) and before [commitConfig](#commitconfig).

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cameraInput | [CameraInput](arkts-camera-camera-camerainput-i.md) | Yes | **CameraInput** instance to add. The API does not take effect if the input parameter is invalid (for example, the value is out of range, null, or undefined). |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for adding the **CameraInput** instance. **true** if it can be added, **false** otherwise. |

**Examples**

```TypeScript
function canAddInput(session: camera.Session, cameraInput: camera.CameraInput): void {
  let canAdd: boolean = session.canAddInput(cameraInput);
  console.info(`The input canAddInput: ${canAdd}`);
}
```

## canAddOutput

```TypeScript
canAddOutput(cameraOutput: CameraOutput): boolean
```

Determines whether a CameraOutput instance can be added to this session. This API must be called after [addInput](#addinput) and before [commitConfig](#commitconfig).

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cameraOutput | [CameraOutput](arkts-camera-camera-cameraoutput-i.md) | Yes | **CameraOutput** instance to add. The API does not take effect if the input parameter is invalid (for example, the value is out of range, null, or undefined). |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for adding the **CameraOutput** instance. **true** if it can be added, **false** otherwise. |

**Examples**

```TypeScript
function canAddOutput(session: camera.Session, cameraOutput: camera.CameraOutput): void {
  let canAdd: boolean = session.canAddOutput(cameraOutput);
  console.info(`This addOutput can add: ${canAdd}`);
}
```

## commitConfig

```TypeScript
commitConfig(callback: AsyncCallback<void>): void
```

Commits the configuration for this session. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the configuration is successfully committed, **err** is **undefined**; otherwise, **err** is an error object with an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md). For example, if the aspect ratio of the preview stream is different from that of the video output stream, error code 7400201 is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function commitConfig(session: camera.Session): void {
  session.commitConfig((err: BusinessError) => {
    if (err) {
      console.error(`The commitConfig call failed. error code: ${err.code}`);
      return;
    }
    console.info('Callback invoked to indicate the commit config success.');
  });
}
```

<a id="commitconfig-1"></a>

## commitConfig

```TypeScript
commitConfig(): Promise<void>
```

Commits the configuration for this session. This API uses a promise to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function commitConfig(session: camera.Session): void {
  session.commitConfig().then(() => {
    console.info('Promise returned to indicate the commit config success.');
  }).catch((error: BusinessError) => {
    // If the operation fails, error.code is returned and processed.
    console.error(`The commitConfig call failed. error code: ${error.code}`);
  });
}
```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases this session. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the session is released successfully, **err** is **undefined**; otherwise, **err** is an error object with an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function releaseCaptureSession(session: camera.Session): void {
  session.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release the session instance, error code: ${err.code}.`);
      return;
    }
    console.info('Callback invoked to indicate that the session instance is released successfully.');
  });
}
```

<a id="release-1"></a>

## release

```TypeScript
release(): Promise<void>
```

Releases this session. This API uses a promise to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function releaseCaptureSession(session: camera.Session): void {
  session.release().then(() => {
    console.info('Promise returned to indicate that the session instance is released successfully.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release the session instance, error code: ${error.code}.`);
  });
}
```

## removeInput

```TypeScript
removeInput(cameraInput: CameraInput): void
```

Removes a [CameraInput](arkts-camera-camera-camerainput-i.md) instance from this session. This API must be called after [beginConfig](#beginconfig) and before [commitConfig](#commitconfig).

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cameraInput | [CameraInput](arkts-camera-camera-camerainput-i.md) | Yes | **CameraInput** instance to remove. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config.<br>**Applicable version:** 11 - 17 |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function removeInput(session: camera.Session, cameraInput: camera.CameraInput): void {
  try {
    session.removeInput(cameraInput);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The removeInput call failed. error code: ${err.code}`);
  }
}
```

## removeOutput

```TypeScript
removeOutput(cameraOutput: CameraOutput): void
```

Removes a [CameraOutput](arkts-camera-camera-cameraoutput-i.md) instance from this session.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cameraOutput | [CameraOutput](arkts-camera-camera-cameraoutput-i.md) | Yes | **CameraOutput** instance to remove. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config.<br>**Applicable version:** 11 - 17 |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function removeOutput(session: camera.Session, previewOutput: camera.PreviewOutput): void {
  try {
    session.removeOutput(previewOutput);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The removeOutput call failed. error code: ${err.code}`);
  }
}
```

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

Starts this session. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the session starts successfully, **err** is **undefined**; otherwise, **err** is an error object with an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function startCaptureSession(session: camera.Session): void {
  session.start((err: BusinessError) => {
    if (err) {
      console.error(`Failed to start the session, error code: ${err.code}.`);
      return;
    }
    console.info('Callback invoked to indicate the session start success.');
  });
}
```

<a id="start-1"></a>

## start

```TypeScript
start(): Promise<void>
```

Starts this session. This API uses a promise to return the result.

**Since:** 11

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
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function startCaptureSession(session: camera.Session): void {
  session.start().then(() => {
    console.info('Promise returned to indicate the session start success.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to start the session, error code: ${error.code}.`);
  });
}
```

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

Stops this session. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the session stops successfully, **err** is **undefined**; otherwise, **err** is an error object with an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function stopCaptureSession(session: camera.Session): void {
  session.stop((err: BusinessError) => {
    if (err) {
      console.error(`Failed to stop the session, error code: ${err.code}.`);
      return;
    }
    console.info('Callback invoked to indicate the session stop success.');
  });
}
```

<a id="stop-1"></a>

## stop

```TypeScript
stop(): Promise<void>
```

Stops this session. This API uses a promise to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function stopCaptureSession(session: camera.Session): void {
  session.stop().then(() => {
    console.info('Promise returned to indicate the session stop success.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to stop the session, error code: ${error.code}.`);
  });
}
```
