# offKey (System API)

## Modules to Import

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## offKey

```TypeScript
function offKey(keyOptions: KeyOptions, callback?: KeyCommandCallback): void
```

Unsubscribe system keys.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyOptions | [KeyOptions](arkts-input-inputconsumer-keyoptions-i-sys.md) | Yes | the key events about input which is to be subscribed. |
| callback | [KeyCommandCallback](arkts-input-inputconsumer-keycommandcallback-t-sys.md) | No | Callback function that receives reported data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |

**Examples**

```TypeScript
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

let leftCtrlKey = 2072;
let cKey = 2049;
let callback: inputConsumer.KeyCommandCallback = (keyOptions, keyEvents): void => {
  console.info(`KeyEvent received`);
}
let keyOptions: inputConsumer.KeyOptions = {
  preKeys: [leftCtrlKey],
  finalKey: cKey,
  isFinalKeyDown: true,
  finalKeyDownDuration: 0,
  triggerType: inputConsumer.KeyCommandTriggerType.PRESSED
};
try {
  inputConsumer.onKey(keyOptions, callback);
  inputConsumer.offKey(keyOptions, callback);
  console.info(`Unsubscribe success`);
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to execute operation. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

let leftCtrlKey = 2072;
let cKey = 2049;
let keyOptions: inputConsumer.KeyOptions = {
  preKeys: [leftCtrlKey],
  finalKey: cKey,
  isFinalKeyDown: true,
  finalKeyDownDuration: 0,
  triggerType: inputConsumer.KeyCommandTriggerType.PRESSED
};
try {
  inputConsumer.offKey(keyOptions);
  console.info(`Unsubscribe all success`);
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to execute operation. Code: ${err.code}, message: ${err.message}`);
}
```
