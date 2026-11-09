# unsetGlobalPriorityCursor (System API)

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## unsetGlobalPriorityCursor

```TypeScript
function unsetGlobalPriorityCursor(): Promise<void>
```

Clear the global high-priority cursor. Only the global high-priority cursor set by the caller can be cleared.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_CURSOR_STYLE

**Model restriction:** This API can be used only in the stage model.

<!--Device-pointer-function unsetGlobalPriorityCursor(): Promise<void>--><!--Device-pointer-function unsetGlobalPriorityCursor(): Promise<void>-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes:         1. The hardware does not support the capability; 2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [3800001](../errorcode-infraredemitter.md#3800001-multimodal-input-service-internal-error) | Input service exception. Possible causes: 1. Memory allocation failure.         2. Thread busy. 3. Service terminated abnormally. 4. Other unexpected errors. Try again later. |
| 26500002 | The global high-priority cursor was not set by the caller and cannot be cleared. |
