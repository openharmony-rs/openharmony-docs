# transmitInfrared

## Modules to Import

```TypeScript
import { infraredEmitter } from '@kit.InputKit';
```

## transmitInfrared

```TypeScript
function transmitInfrared(infraredFrequency: number, pattern: Array<number>): void
```

Generates IR signals at the specified frequency and level.

**Since:** 15

**Required permissions:** ohos.permission.MANAGE_INPUT_INFRARED_EMITTER

**System capability:** SystemCapability.MultimodalInput.Input.InfraredEmitter

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| infraredFrequency | number | Yes | IR frequency, in Hz. |
| pattern | Array&lt;number&gt; | Yes | Infrared level signal, in microseconds (μs). The number of infrared level signals ranges from 0 to 1024. The value of this parameter must be greater than 0. If this parameter is set to **0**, the API does not take effect.<br>For example, in the level signal array [100,200,300,400], **100** indicates a high-level signal, **200** indicates a low-level signal, **300** is a high-level signal, and **400** is a low -level signal. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application.<br>**Applicable version:** 12 - 14 |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { infraredEmitter } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the infrared frequency and infrared level signal mode.
            infraredEmitter.transmitInfrared(38000, [100, 200, 300, 400]);
          } catch (error) {
            console.error(`Failed to transmit infrared signal, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
