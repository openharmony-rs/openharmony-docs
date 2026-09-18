# DepthFusionQuery (System API)

A class for querying depth fusion capabilities.

**Since:** 14

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getDepthFusionThreshold

```TypeScript
getDepthFusionThreshold(): Array<number>
```

Obtains the depth fusion threshold.

**Since:** 14

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;number&gt; | Depth fusion threshold. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getDepthFusionThreshold(DepthFusionQuery: camera.DepthFusionQuery): void {
  try {
    let threshold: Array<number> = DepthFusionQuery.getDepthFusionThreshold();
    console.info('Promise returned to indicate that getDepthFusionThreshold method execution success.');
  } catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to depth fusion query  getDepthFusionThreshold, error code: ${err.code}.`);
  }
}
```

## isDepthFusionSupported

```TypeScript
isDepthFusionSupported(): boolean
```

Checks whether depth fusion is supported.

**Since:** 14

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of depth fusion. **true** if supported, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isDepthFusionSupported(DepthFusionQuery: camera.DepthFusionQuery): void {
  try {
    let isSupported: boolean = DepthFusionQuery.isDepthFusionSupported();
    console.info('Indicate that isDepthFusionSupported method execution success.');
  } catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to depth fusion query  isDepthFusionSupported, error code: ${err.code}.`);
  }
}
```
