# sendPrivateCommand (System API)

## Modules to Import

```TypeScript
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## sendPrivateCommand

```TypeScript
function sendPrivateCommand(commandData: Record<string, CommandDataType>): Promise<void>
```

Sends a private command to the system-default input method application.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| commandData | Record&lt;string, [CommandDataType](arkts-ime-inputmethodengine-commanddatatype-t.md)&gt; | Yes | Command data to be sent. The maximum size is 32 KB, and a maximum of five commands are allowed. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12800026](../errorcode-inputmethod-framework.md#12800026-input-method-system-panel-error) | input method system panel error. Possible causes: 1. the system panel not connected. 2. ipc failed due to the large amount of data transferred or other reasons. 3. the caller is not system panel. |
