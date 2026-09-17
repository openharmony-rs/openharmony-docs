# isArkChildProcessSupported

## Modules to Import

```TypeScript
import { childProcessManager } from '@kit.AbilityKit';
```

## isArkChildProcessSupported

```TypeScript
function isArkChildProcessSupported(): boolean
```

Checks whether the caller is allowed to create ark child processes on this device. Some devices may not support creating ark child processes, so it is recommended to use this interface to verify support beforehand.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | `true`: The caller is allowed to create ark child processes.   - `false`: The caller is not allowed to create ark child processes. |

**Examples**

```TypeScript
import { childProcessManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('Click')
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            try {
              let isSupport: boolean = childProcessManager.isArkChildProcessSupported();
              console.info(`isArkChildProcessSupported: ${isSupport}`);
            } catch (err: BusinessError) {
              console.error(`isArkChildProcessSupported error, errorCode: ${err.code}, errorMsg: ${err.message}`);
            }
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
