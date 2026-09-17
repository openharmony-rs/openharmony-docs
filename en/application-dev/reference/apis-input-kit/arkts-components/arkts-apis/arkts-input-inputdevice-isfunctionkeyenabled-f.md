# isFunctionKeyEnabled

## Modules to Import

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## isFunctionKeyEnabled

```TypeScript
function isFunctionKeyEnabled(functionKey: FunctionKey): Promise<boolean>
```

Checks whether the specified function key (for example, **CapsLock**) is enabled. This API uses a promise to return the result.

**Since:** 15

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| functionKey | [FunctionKey](arkts-input-inputdevice-functionkey-e.md) | Yes | Type of the function key. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the function key is enabled, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [3900002](../errorcode-inputdevice.md#3900002-keyboard-not-connected) | There is currently no keyboard device connected. |

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
            // Query Whether a Function Key Is Enabled
            inputDevice.isFunctionKeyEnabled(inputDevice.FunctionKey.CAPS_LOCK).then((state: boolean) => {
              console.info(`Succeeded in getting capslock state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get capslock state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get capslock state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
