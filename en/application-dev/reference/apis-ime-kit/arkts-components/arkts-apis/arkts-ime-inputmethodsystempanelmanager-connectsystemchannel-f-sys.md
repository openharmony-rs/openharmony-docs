# connectSystemChannel (System API)

## Modules to Import

```TypeScript
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## connectSystemChannel

```TypeScript
function connectSystemChannel(): Promise<void>
```

Connects to the system channel for communication between the input method system panel and the system-default input method application. This API can be called only by the input method system panel.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CONNECT_IME_ABILITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

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
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible causes: a system error, such as null pointer, IPC exception. |
| [12800026](../errorcode-inputmethod-framework.md#12800026-input-method-system-panel-error) | input method system panel error. Possible causes: 1. the system panel not connected. 2. ipc failed due to the large amount of data transferred or other reasons. 3. the caller is not system panel. |
