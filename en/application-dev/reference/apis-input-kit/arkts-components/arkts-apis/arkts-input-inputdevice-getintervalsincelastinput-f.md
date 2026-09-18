# getIntervalSinceLastInput

## Modules to Import

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## getIntervalSinceLastInput

```TypeScript
function getIntervalSinceLastInput(): Promise<number>
```

Obtains the interval (including the device sleep time) elapsed since the last system input event. This API uses a promise to return the result.

**Since:** 14

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the time elapsed since the last system input event, in microseconds (μs). |

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
            // Obtain the time interval since the last input
            inputDevice.getIntervalSinceLastInput().then((timeInterval: number) => {
              console.info(`Succeeded in getting interval since last input: ${JSON.stringify(timeInterval)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get interval since last input, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get interval since last input, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
