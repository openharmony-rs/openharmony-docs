# init

## Modules to Import

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## init

```TypeScript
function init(
    options: [
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number,
      number
    ]
  ): Matrix4Transit
```

Matrix constructor, which is used to create a 4 x 4 matrix with the input parameters. Column-major order is used.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number     ] | Yes | A number array whose length is 16 (4 x 4). For details, see **4 x 4 matrix description**.<br>Value range of each number: (-∞, +∞)<br>Default value:<br>[1, 0, 0, 0,<br>0, 1, 0, 0,<br>0, 0, 1, 0,<br>0, 0, 0, 1] |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | 4 x 4 matrix object created based on the input parameters. |

**Examples**

```TypeScript
import { matrix4 } from '@kit.ArkUI';

// Create a 4 x 4 matrix.
let matrix = matrix4.init(
  [1.0, 0.0, 0.0, 0.0,
    0.0, 1.0, 0.0, 0.0,
    0.0, 0.0, 1.0, 0.0,
    0.0, 0.0, 0.0, 1.0]);

@Entry
@Component
struct Tests {
  build() {
    Column() {
      // Replace $r("app.media.zh") with the image resource file you use.
      Image($r("app.media.zh"))
        .width('40%')
        .height(100)
        .transform(matrix)
    }
  }
}
```
