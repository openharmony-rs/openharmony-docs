# ColorSpaceManager

Implements management of color space objects. ColorSpaceManager is a core class used to manage and operate color space objects. It provides functions such as obtaining the color space type, white point value, and gamma value, and supports transfer between concurrent ArkTS instances.

Before calling any of the following APIs, you must use [create()](arkts-arkgraphics2d-sendablecolorspacemanager-create-f.md) to create a color space manager.

**Inheritance/Implementation:** ColorSpaceManager extends [ISendable](arkts-arkgraphics2d-sendablecolorspacemanager-isendable-t.md)

**Since:** 12

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## Modules to Import

```TypeScript
import { sendableColorSpaceManager } from '@kit.ArkGraphics2D';
```

## getColorSpaceName

```TypeScript
getColorSpaceName(): colorSpaceManager.ColorSpace
```

Obtains the color space type.

**Since:** 12

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| [colorSpaceManager.ColorSpace](arkts-arkgraphics2d-colorspacemanager-colorspace-e.md) | Color space type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [18600001](../errorcode-colorspace-manager.md#18600001-abnormal-parameter-value) | The parameter value is abnormal.<br>**Applicable version:** 12 - 22 |

**Examples**

```TypeScript
// Obtain the color space type.
let spaceName: colorSpaceManager.ColorSpace = colorSpace.getColorSpaceName();
```

## getGamma

```TypeScript
getGamma(): number
```

Obtains the gamma of the color space.

**Since:** 12

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Gamma of the color space. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [18600001](../errorcode-colorspace-manager.md#18600001-abnormal-parameter-value) | The parameter value is abnormal.<br>**Applicable version:** 12 - 22 |

**Examples**

```TypeScript
// Obtain the gamma value of the color space.
let gamma: number = colorSpace.getGamma();
```

## getWhitePoint

```TypeScript
getWhitePoint(): collections.Array<number>
```

Obtains the white point value of the color space. The chromaticity coordinates [x, y] are returned, indicating the coordinates of the white point in the color space.

**Since:** 12

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| [collections.Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)&lt;number&gt; | Coordinates [x, y] of the white point. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [18600001](../errorcode-colorspace-manager.md#18600001-abnormal-parameter-value) | The parameter value is abnormal.<br>**Applicable version:** 12 - 22 |

**Examples**

```TypeScript
import { collections } from '@kit.ArkTS';
// Obtain the white point value [x, y] of the color space.
let point: collections.Array<number> = colorSpace.getWhitePoint();
```
