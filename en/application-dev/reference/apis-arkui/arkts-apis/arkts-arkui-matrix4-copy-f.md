# copy

## Modules to Import

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## copy

```TypeScript
function copy(): Matrix4Transit
```

Copies this matrix object.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [copy](arkts-arkui-matrix4-matrix4transit-i.md#copy)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Copy object of the current matrix. |

**Examples**

```TypeScript
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

let matrix1 = matrix4.identity().translate({ x: 100 });
// Perform a scale operation on the copy of matrix1 without affecting matrix1.
let matrix2 = matrix1.copy().scale({ x: 2 });

@Entry
@Component
struct Test {

  build() {
    Column() {
      // Replace $r("app.media.bg1") with the image resource file you use.
      Image($r("app.media.bg1"))
        .width('40%')
        .height(100)
        .transform(matrix1)
      // Replace $r("app.media.bg2") with the image resource file you use.
      Image($r("app.media.bg2"))
        .width("40%")
        .height(100)
        .margin({ top: 50 })
        .transform(matrix2)
    }
  }
}
```
