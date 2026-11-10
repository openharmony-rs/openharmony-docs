# setGlobalPriorityCursor (System API)

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## setGlobalPriorityCursor

```TypeScript
function setGlobalPriorityCursor(cursor: CustomCursor): Promise<void>
```

Set a global high-priority cursor. Once set successfully, the cursor style will be locked and restricted when the cursor is visible, unaffected by other styles, until it is cleared or overridden by a new global high-priority cursor.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_CURSOR_STYLE

**Model restriction:** This API can be used only in the stage model.

<!--Device-pointer-function setGlobalPriorityCursor(cursor: CustomCursor): Promise<void>--><!--Device-pointer-function setGlobalPriorityCursor(cursor: CustomCursor): Promise<void>-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cursor | [CustomCursor](arkts-input-pointer-customcursor-i.md) | Yes | cursor resource info. |

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
