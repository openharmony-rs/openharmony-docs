# getInfraredFrequencies

## Modules to Import

```TypeScript
import { infraredEmitter } from '@kit.InputKit';
```

## getInfraredFrequencies

```TypeScript
function getInfraredFrequencies(): Array<InfraredFrequency>
```

Queries the frequency range of the infrared signals supported by the device. It is recommended that you first use [hasIrEmitter](arkts-input-infraredemitter-hasiremitter-f.md) to check whether the device supports an infrared emitter.

**Since:** 15

**Required permissions:** ohos.permission.MANAGE_INPUT_INFRARED_EMITTER

<!--Device-infraredEmitter-function getInfraredFrequencies(): Array<InfraredFrequency>--><!--Device-infraredEmitter-function getInfraredFrequencies(): Array<InfraredFrequency>-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InfraredEmitter

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[InfraredFrequency](arkts-input-infraredemitter-infraredfrequency-i.md)&gt; | Frequency range of the infrared signal, containing multiple sets of maximum and minimum frequencies.<br>Since API version 23, when the device does not have an infrared emitter, a set of maximum and minimum frequencies is returned, both 0 Hz. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 - 14 |

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
            let frequencies = infraredEmitter.getInfraredFrequencies();
            console.info(`Succeeded in getting infrared frequencies, frequencies: ${JSON.stringify(frequencies)}.`);
          } catch (error) {
            console.error(`Failed to get infrared frequencies, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
