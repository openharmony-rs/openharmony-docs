# DepthFusion (System API)

Depth fusion class. It inherits from [DepthFusionQuery](arkts-camera-camera-depthfusionquery-i-sys.md).

**Inheritance/Implementation:** DepthFusion extends [DepthFusionQuery](arkts-camera-camera-depthfusionquery-i-sys.md)

**Since:** 14

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## enableDepthFusion

```TypeScript
enableDepthFusion(enabled: boolean): void
```

Enables depth fusion.

**Since:** 14

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable depth fusion. **true** to enable, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function enableDepthFusion(DepthFusion: camera.DepthFusion): void {
  try {
    let enabled: boolean = true;
    DepthFusion.enableDepthFusion(enabled);
    console.info('Promise returned to indicate that enableDepthFusion method execution success.');
  } catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to depth fusion enableDepthFusion, error code: ${err.code}.`);
  };
}
```

## isDepthFusionEnabled

```TypeScript
isDepthFusionEnabled(): boolean
```

Checks whether depth fusion is enabled.

**Since:** 14

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether depth fusion is enabled. **true** if enabled, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isDepthFusionEnabled(DepthFusion: camera.DepthFusion): boolean {
  let isEnable: boolean = false;
  try {
    isEnable = DepthFusion.isDepthFusionEnabled();
    console.info('Promise returned to indicate that isDepthFusionEnabled method execution success.');
  } catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to depth fusion isDepthFusionEnabled, error code: ${err.code}.`);
  };
  return isEnable;
}
```
