# SecureSession

```TypeScript
interface SecureSession extends Session, Flash, AutoExposure, WhiteBalance, Focus, Zoom
```

**SecureSession** inherits from [Session](arkts-camera-camera-session-i.md), [Flash](arkts-camera-camera-flash-i.md), [AutoExposure](arkts-camera-camera-autoexposure-i.md), [WhiteBalance](arkts-camera-camera-whitebalance-i.md), [Focus](arkts-camera-camera-focus-i.md), and [Zoom](arkts-camera-camera-zoom-i.md).

It implements a secure session, which provides operations on the flash, exposure, white balance, focus, and zoom.

You can call [createSession](arkts-camera-camera-cameramanager-i.md#createsession) with [SceneMode](arkts-camera-camera-scenemode-e.md) set to **SECURE_PHOTO** to create a session in secure mode. The secure mode is designed for applications with high security requirements, such as facial recognition systems and banking services. It must be used together with the &lt;!--RP1--&gt;security TA&lt;!--RP1End--&gt; to support service scenarios where both standard preview streams and security streams are output.&lt;!--RP2--&gt;

The security TA can verify the signature of data delivered by the server, sign images, parse and assemble TLV logic, and read, create, and operate keys. It applies to image processing.&lt;!--RP2End--&gt;

@extends Session, Flash, AutoExposure, Focus, Zoom [since 12 - 19] @extends Session, Flash, AutoExposure, WhiteBalance, Focus, Zoom [since 20]

**Inheritance/Implementation:** SecureSession extends [Session](arkts-camera-camera-session-i.md), [Flash](arkts-camera-camera-flash-i.md), [AutoExposure](arkts-camera-camera-autoexposure-i.md), [WhiteBalance](arkts-camera-camera-whitebalance-i.md), [Focus](arkts-camera-camera-focus-i.md), [Zoom](arkts-camera-camera-zoom-i.md)

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## addSecureOutput

```TypeScript
addSecureOutput(previewOutput: PreviewOutput): void
```

Marks a [PreviewOutput](arkts-camera-camera-previewoutput-i.md) stream as secure output.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| previewOutput | [PreviewOutput](arkts-camera-camera-previewoutput-i.md) | Yes | Preview output stream. An error code is returned if the input parameter is invalid. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config.<br>**Applicable version:** 12 - 17 |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function addSecureOutput(session: camera.SecureSession, previewOutput: camera.PreviewOutput): void {
  try {
    session.addSecureOutput(previewOutput);
  } catch (error) {
    // If the operation fails, error.code is returned and processed.
    let err = error as BusinessError;
    console.error(`The addOutput call failed. error code: ${err.code}`);
  }
}
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from SecureSession error events.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. The value is fixed at **'error'**. The event can be listened for when a session is created. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

**Examples**

```TypeScript
function unregisterSessionError(secureSession: camera.SecureSession): void {
  secureSession.off('error');
}
```

## off('focusStateChange')

```TypeScript
off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void
```

Unsubscribes from focus state change events.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'focusStateChange' | Yes | Event type. The value is fixed at **'focusStateChange'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

**Examples**

```TypeScript
function unregisterFocusStateChange(secureSession: camera.SecureSession): void {
  secureSession.off('focusStateChange');
}
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to SecureSession error events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. The value is fixed at **'error'**. The event can be listened for when a session is created. This event is triggered and the error message is returned when an error occurs during the calling of a session-related API such as [beginConfig](arkts-camera-camera-session-i.md#beginconfig), [commitConfig](arkts-camera-camera-session-i.md#commitconfig), and [addInput](arkts-camera-camera-session-i.md#addinput). |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to return an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md). |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError): void {
  console.error(`Video session error code: ${err.code}`);
}

function registerSessionError(secureSession: camera.SecureSession): void {
  secureSession.on('error', callback);
}
```

## on('focusStateChange')

```TypeScript
on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void
```

Subscribes to focus state change events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'focusStateChange' | Yes | Event type. The value is fixed at **'focusStateChange'**. The event can be listened for when a session is created. This event is triggered only when the camera focus state changes in auto focus mode. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | Yes | Callback used to return the focus state change. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, focusState: camera.FocusState): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`Focus state: ${focusState}`);
}

function registerFocusStateChange(secureSession: camera.SecureSession): void {
  secureSession.on('focusStateChange', callback);
}
```
