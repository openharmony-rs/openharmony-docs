# setShieldStatus (System API)

## Modules to Import

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## setShieldStatus

```TypeScript
function setShieldStatus(shieldMode: ShieldMode, isShield: boolean): void
```

Sets the system hotkey shield status.

**Since:** 11

**Required permissions:** ohos.permission.INPUT_CONTROL_DISPATCHING

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shieldMode | [ShieldMode](arkts-input-inputconsumer-shieldmode-e-sys.md) | Yes | System hotkey shield mode. Currently, only **FACTORY_MODE** is supported, which means to shield all system hotkeys. |
| isShield | boolean | Yes | Whether to enable shortcut key shielding. The value **true** means to enable shortcut key shielding, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | SystemAPI permission error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let FACTORY_MODE = 0;
          try {
            // Set the shield status.
            inputConsumer.setShieldStatus(FACTORY_MODE, true);
            console.info(`Succeeded in setting shield status.`);
          } catch (error) {
            console.error(`Failed to set shield status, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
