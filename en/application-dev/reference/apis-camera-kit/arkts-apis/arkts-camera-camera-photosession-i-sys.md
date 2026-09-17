# PhotoSession

**PhotoSession** inherits from [Session](arkts-camera-camera-session-i.md), [Flash](arkts-camera-camera-flash-i.md), [AutoExposure](arkts-camera-camera-autoexposure-i.md), [WhiteBalance](arkts-camera-camera-whitebalance-i.md), [Focus](arkts-camera-camera-focus-i.md), [Zoom](arkts-camera-camera-zoom-i.md), [ColorManagement](arkts-camera-camera-colormanagement-i.md), [AutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md), [Macro](arkts-camera-camera-macro-i.md), [ManualExposure](arkts-camera-camera-manualexposure-i.md), [ManualFocus](arkts-camera-camera-manualfocus-i.md), [ManualIso](arkts-camera-camera-manualiso-i.md), [OIS](arkts-camera-camera-ois-i.md), and [Aperture](arkts-camera-camera-aperture-i.md).

It implements a photo session, which provides operations on the flash, exposure, white balance, focus, zoom, color space, macro mode, manual exposure, manual focus, manual ISO setting, optical image stabilization (OIS), and aperture.

**PhotoSession** is provided for the default photo mode. It is used to take standard photos. It supports multiple photo formats and resolutions, which are suitable for most daily photo capture scenarios.

@extends Session, Flash, AutoExposure, Focus, Zoom, ColorManagement [since 11 - 12] @extends Session, Flash, AutoExposure, Focus, Zoom, ColorManagement, AutoDeviceSwitch [since 13 - 18] @extends Session, Flash, AutoExposure, Focus, Zoom, ColorManagement, AutoDeviceSwitch, Macro [since 19 - 19] @extends Session, Flash, AutoExposure, WhiteBalance, Focus, Zoom, ColorManagement, AutoDeviceSwitch, Macro [since 20 - 23] @extends Session, Flash, AutoExposure, WhiteBalance, Focus, Zoom, ColorManagement, AutoDeviceSwitch, Macro, ManualExposure, ManualFocus, ManualIso, OIS, Aperture [since 24]

**Inheritance/Implementation:** PhotoSession extends [Session](arkts-camera-camera-session-i.md), [Flash](arkts-camera-camera-flash-i.md), [AutoExposure](arkts-camera-camera-autoexposure-i.md), [WhiteBalance](arkts-camera-camera-whitebalance-i.md), [Focus](arkts-camera-camera-focus-i.md), [Zoom](arkts-camera-camera-zoom-i.md), [ColorManagement](arkts-camera-camera-colormanagement-i.md), [AutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md), [Macro](arkts-camera-camera-macro-i.md), [ManualExposure](arkts-camera-camera-manualexposure-i.md), [ManualFocus](arkts-camera-camera-manualfocus-i.md), [ManualIso](arkts-camera-camera-manualiso-i.md), [OIS](arkts-camera-camera-ois-i.md), [Aperture](arkts-camera-camera-aperture-i.md)

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getSessionConflictFunctions

```TypeScript
getSessionConflictFunctions(): Array<PhotoConflictFunctions>
```

Gets session conflict functions.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[PhotoConflictFunctions](arkts-camera-camera-photoconflictfunctions-i-sys.md)&gt; | List of session conflict functions. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

## getSessionFunctions

```TypeScript
getSessionFunctions(outputCapability: CameraOutputCapability): Array<PhotoFunctions>
```

Gets session functions.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| outputCapability | [CameraOutputCapability](arkts-camera-camera-cameraoutputcapability-i.md) | Yes | CameraOutputCapability to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[PhotoFunctions](arkts-camera-camera-photofunctions-i-sys.md)&gt; | List of session functions. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

## off('featureDetection')

```TypeScript
off(type: 'featureDetection', featureType: SceneFeatureType, callback?: AsyncCallback<SceneFeatureDetectionResult>): void
```

Unsubscribe from camera feature detection status change events.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'featureDetection' | Yes | Event type. The value is fixed at **'featureDetection'**. The event can be listened for when a session is created. |
| featureType | [SceneFeatureType](arkts-camera-camera-scenefeaturetype-e-sys.md) | Yes | Scene feature type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SceneFeatureDetectionResult](arkts-camera-camera-scenefeaturedetectionresult-i-sys.md)&gt; | No | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('featureDetection')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

## off('effectSuggestionChange')

```TypeScript
off(type: 'effectSuggestionChange', callback?: AsyncCallback<EffectSuggestionType>): void
```

Unsubscribes from effect suggestion event callback.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'effectSuggestionChange' | Yes | Event type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[EffectSuggestionType](arkts-camera-camera-effectsuggestiontype-e-sys.md)&gt; | No | Callback used to return the result. |

## off('lcdFlashStatus')

```TypeScript
off(type: 'lcdFlashStatus', callback?: AsyncCallback<LcdFlashStatus>): void
```

Unsubscribes from LCD flash status change events.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'lcdFlashStatus' | Yes | Event type. The value is fixed at **'lcdFlashStatus'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[LcdFlashStatus](arkts-camera-camera-lcdflashstatus-i-sys.md)&gt; | No | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('lcdFlashStatus')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

## on('featureDetection')

```TypeScript
on(type: 'featureDetection', featureType: SceneFeatureType, callback: AsyncCallback<SceneFeatureDetectionResult>): void
```

Subscribe to scene feature detection status change events. This API uses an asynchronous callback to return the result.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'featureDetection' | Yes | Event type. The value is fixed at **'featureDetection'**. The event can be listened for when a photo session is created. |
| featureType | [SceneFeatureType](arkts-camera-camera-scenefeaturetype-e-sys.md) | Yes | Scene feature type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SceneFeatureDetectionResult](arkts-camera-camera-scenefeaturedetectionresult-i-sys.md)&gt; | Yes | Callback used to return the status of the scene feature detection. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

## on('effectSuggestionChange')

```TypeScript
on(type: 'effectSuggestionChange', callback: AsyncCallback<EffectSuggestionType>): void
```

Subscribes to effect suggestion event callback.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'effectSuggestionChange' | Yes | Event type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[EffectSuggestionType](arkts-camera-camera-effectsuggestiontype-e-sys.md)&gt; | Yes | Callback used to return the result. |

## on('lcdFlashStatus')

```TypeScript
on(type: 'lcdFlashStatus', callback: AsyncCallback<LcdFlashStatus>): void
```

Subscribes to LCD flash status change events. This API uses an asynchronous callback to return the result.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'lcdFlashStatus' | Yes | Event type. The value is fixed at **'lcdFlashStatus'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[LcdFlashStatus](arkts-camera-camera-lcdflashstatus-i-sys.md)&gt; | Yes | Callback used to return the LCD flash status change. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
