# onKey (System API)

## Modules to Import

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## onKey

```TypeScript
function onKey(keyOptions: KeyOptions, callback:KeyCommandCallback): void
```

Subscribe system keys.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyOptions | [KeyOptions](arkts-input-inputconsumer-keyoptions-i-sys.md) | Yes | the key events about input which is to be subscribed. |
| callback | [KeyCommandCallback](arkts-input-inputconsumer-keycommandcallback-t-sys.md) | Yes | callback function, receive reported data. |

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
let keyOptions: inputConsumer.KeyOptions = {
  preKeys: [leftCtrlKey],
  finalKey: cKey,
  isFinalKeyDown: true,
  finalKeyDownDuration: 0,
  triggerType: inputConsumer.KeyCommandTriggerType.PRESSED
};
let callback: inputConsumer.KeyCommandCallback = (keyOptions, keyEvents): void => {
  console.info(`keyOptions: ${keyOptions} keyEvents: ${keyEvents}`);
};
try {
  inputConsumer.onKey(keyOptions, callback);
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to subscribe. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

let keyOptions: inputConsumer.KeyOptions = {
  preKeys: [],
  finalKey: 2049,
  isFinalKeyDown: true,
  finalKeyDownDuration: 0,
  triggerType: inputConsumer.KeyCommandTriggerType.REPEAT_PRESSED
};
let callback: inputConsumer.KeyCommandCallback = (keyOptions, keyEvents): void => {
  console.info(`Repeat key event`);
}
try {
  inputConsumer.onKey(keyOptions, callback);
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to subscribe. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

let leftAltKey = 2045;
let tabKey = 2049;
let keyOptions: inputConsumer.KeyOptions = {
  preKeys: [leftAltKey],
  finalKey: tabKey,
  isFinalKeyDown: true,
  finalKeyDownDuration: 0,
  triggerType: inputConsumer.KeyCommandTriggerType.ALL_RELEASED
};
let callback: inputConsumer.KeyCommandCallback = (keyOptions, keyEvents): void => {
  console.info(`All released event`);
}
try {
  inputConsumer.onKey(keyOptions, callback);
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to subscribe. Code: ${err.code}, message: ${err.message}`);
}
```
