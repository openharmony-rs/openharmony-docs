# ManualFocusQuery

```TypeScript
interface ManualFocusQuery
```

Manual Focus Query object.

**Since:** 24

<!--Device-camera-interface ManualFocusQuery--><!--Device-camera-interface ManualFocusQuery-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## isFocusDistanceSupported

```TypeScript
isFocusDistanceSupported(): boolean
```

Checks whether a focus distance is supported.

**Since:** 24

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-ManualFocusQuery-isFocusDistanceSupported(): boolean--><!--Device-ManualFocusQuery-isFocusDistanceSupported(): boolean-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Is focus distance supported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |
