# setFunctionKeyEnabled

## Modules to Import

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## setFunctionKeyEnabled

```TypeScript
function setFunctionKeyEnabled(functionKey: FunctionKey, enabled: boolean): Promise<void>
```

Specifies whether to enable a function key (for example, **CapsLock**). This API uses a promise to return the result.

**Since:** 15

**Required permissions:** ohos.permission.INPUT_KEYBOARD_CONTROLLER

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| functionKey | [FunctionKey](arkts-input-inputdevice-functionkey-e.md) | Yes | Type of the function key. |
| enabled | boolean | Yes | Status of the function key. The value **true** indicates that the function key is enabled, and the value **false** indicates the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [3900002](../errorcode-inputdevice.md#3900002-keyboard-not-connected) | There is currently no keyboard device connected. |
| [3900003](../errorcode-inputdevice.md#3900003-api-call-failed-for-a-non-input-application) | It is prohibited for non-input applications. |

**Examples**

```TypeScript
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set Function Key Enabled Status
            inputDevice.setFunctionKeyEnabled(inputDevice.FunctionKey.CAPS_LOCK, true).then(() => {
              console.info(`Succeeded in setting capslock state.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set capslock state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            });
          } catch (error) {
            console.error(`Failed to set capslock enable, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
