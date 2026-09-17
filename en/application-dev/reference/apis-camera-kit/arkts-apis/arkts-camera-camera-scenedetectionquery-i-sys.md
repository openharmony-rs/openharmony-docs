# SceneDetectionQuery (System API)

Provides the scene detection and query capabilities.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## isSceneFeatureSupported

```TypeScript
isSceneFeatureSupported(type: SceneFeatureType): boolean
```

Checks whether a scene feature is supported.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SceneFeatureType](arkts-camera-camera-scenefeaturetype-e-sys.md) | Yes | Scene feature. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of the scene feature. **true** if supported, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application, only throw in session usage. |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |

**Examples**

```TypeScript
function isSceneFeatureSupported(photoSessionForSys: camera.PhotoSessionForSys, featureType: camera.SceneFeatureType): boolean {
  let isSupported: boolean = photoSessionForSys.isSceneFeatureSupported(featureType);
  return isSupported;
}
```
