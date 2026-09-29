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

Constructor of **Matrix4**. It is used to create a 4 x 4 matrix based on the input parameters. The matrix is column -major, that is, the 16 values in the input array are filled into the matrix column by column: array[0] to array[3] form the first column, array[4] to array[7] form the second column, array[8] to array[11] form the third column, and array[12] to array[15] form the fourth column. When only an identity matrix is required, you are advised to use **matrix4.identity()**.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-matrix4-function init(    options: [      number,      number,      number,      number,      number,      number,      number,      number,      number,      number,      number,      number,      number,      number,      number,      number    ]  ): Matrix4Transit--><!--Device-matrix4-function init(    options: [      number,      number,      number,      number,      number,      number,      number,      number,      number,      number,      number,      number,      number,      number,      number,      number    ]  ): Matrix4Transit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number,       number     ] | Yes | Number array whose length is 16 (4 x 4). For details, see **4 x 4 matrix description**.<br>Value range of each number: (-∞, +∞) <br>Default value: <br>[1, 0, 0, 0, <br>0, 1, 0, 0, <br>0, 0, 1, 0, <br>0, 0, 0, 1] |

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
