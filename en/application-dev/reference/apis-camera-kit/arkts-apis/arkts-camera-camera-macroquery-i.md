# MacroQuery

```TypeScript
interface MacroQuery
```

MacroQuery provides the API to check the support for macro photography.

**Since:** 19

<!--Device-camera-interface MacroQuery--><!--Device-camera-interface MacroQuery-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## isMacroSupported

```TypeScript
isMacroSupported(): boolean
```

Checks whether macro photography is supported in the current state. This API must be called after [commitConfig](arkts-camera-camera-session-i.md#commitconfig).

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-MacroQuery-isMacroSupported(): boolean--><!--Device-MacroQuery-isMacroSupported(): boolean-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of macro photography. **true** if supported, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |

**Examples**

```TypeScript
function isMacroSupported(photoSession: camera.PhotoSession): boolean {
  let isSupported: boolean = photoSession.isMacroSupported();
  return isSupported;
}
```
