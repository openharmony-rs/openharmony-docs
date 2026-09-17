# isNativeChildProcessSupported

## Modules to Import

```TypeScript
import { childProcessManager } from '@kit.AbilityKit';
```

## isNativeChildProcessSupported

```TypeScript
function isNativeChildProcessSupported(): boolean
```

Checks whether the caller is allowed to create native child processes on this device. Some devices may not support creating native child processes, so it is recommended to use this interface to verify support beforehand.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | `true`: The caller is allowed to create native child processes.   - `false`: The caller is not allowed to create native child processes. |

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
              let isSupport: boolean = childProcessManager.isNativeChildProcessSupported();
              console.info(`isNativeChildProcessSupported: ${isSupport}`);
            } catch (err: BusinessError) {
              console.error(`isNativeChildProcessSupported error, errorCode: ${err.code}, errorMsg: ${err.message}`);
            }
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
