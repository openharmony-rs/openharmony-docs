# offSystemPrivateCommand (System API)

## Modules to Import

```TypeScript
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## offSystemPrivateCommand

```TypeScript
function offSystemPrivateCommand(callback?: Callback<Record<string, CommandDataType>>): void
```

Unsubscribes from events that the system-default input method application sends a private data command.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Record&lt;string, [CommandDataType](arkts-ime-inputmethodengine-commanddatatype-t.md)&gt;&gt; | No | Callback function. If this parameter is left empty, all callbacks will be unsubscribed from. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
