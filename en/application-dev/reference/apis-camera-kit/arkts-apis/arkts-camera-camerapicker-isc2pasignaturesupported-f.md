# isC2PASignatureSupported

## Modules to Import

```TypeScript
import { cameraPicker } from '@kit.CameraKit';
```

## isC2PASignatureSupported

```TypeScript
function isC2PASignatureSupported(): boolean
```

Checks whether C2PA signature is supported.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-cameraPicker-function isC2PASignatureSupported(): boolean--><!--Device-cameraPicker-function isC2PASignatureSupported(): boolean-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of C2PA signature. **true** if supported, **false** otherwise. If the API call fails, undefined is returned. |
