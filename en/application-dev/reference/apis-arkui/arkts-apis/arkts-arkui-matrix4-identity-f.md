# identity

## Modules to Import

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## identity

```TypeScript
function identity(): Matrix4Transit
```

Constructs an identity matrix.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Identity matrix object. |

**Examples**

```TypeScript
// The effect of matrix 1 is the same as that of matrix 2.
import { matrix4 } from '@kit.ArkUI';

let matrix1 = matrix4.init(
  [1.0, 0.0, 0.0, 0.0,
    0.0, 1.0, 0.0, 0.0,
    0.0, 0.0, 1.0, 0.0,
    0.0, 0.0, 0.0, 1.0]);
let matrix2 = matrix4.identity();

@Entry
@Component
struct Tests {
  build() {
    Column() {
      // Replace $r("app.media.zh") with the image resource file you use.
      Image($r("app.media.zh"))
        .width('40%')
        .height(100)
        .transform(matrix1)
      // Replace $r("app.media.zh") with the image resource file you use.
      Image($r("app.media.zh"))
        .width("40%")
        .height(100)
        .margin({ top: 150 })
        .transform(matrix2)
    }
  }
}
```
