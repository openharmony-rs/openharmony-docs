# create

## Modules to Import

```TypeScript
import { sendableColorSpaceManager } from '@kit.ArkGraphics2D';
```

## create

```TypeScript
function create(colorSpaceName: colorSpaceManager.ColorSpace): ColorSpaceManager
```

Creates a criterion color space management instance that is sendable.

**Since:** 12

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colorSpaceName | [colorSpaceManager.ColorSpace](arkts-arkgraphics2d-colorspacemanager-colorspace-e.md) | Yes | Type of the color space.<br>**UNKNOWN** and **CUSTOM** cannot be used when creating standard color space objects. |

**Return value:**

| Type | Description |
| --- | --- |
| [ColorSpaceManager](arkts-arkgraphics2d-sendablecolorspacemanager-colorspacemanager-i.md) | Sendable color space object created. <br>This instance inherits from **ISendable** and can be passed by reference between concurrent ArkTS instances (including the main thread and the worker threads of TaskPool or Worker). For details, see [Using Sendable Objects](../../../arkts-utils/sendable-guide.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1.Incorrect parameter type. 2.Parameter verification failed. |
| [18600001](../errorcode-colorspace-manager.md#18600001-abnormal-parameter-value) | The parameter value is abnormal. |

**Examples**

```TypeScript
import { colorSpaceManager, sendableColorSpaceManager } from '@kit.ArkGraphics2D';
let colorSpace: sendableColorSpaceManager.ColorSpaceManager;
// Create a color management instance for the criterion sRGB color space.
colorSpace = sendableColorSpaceManager.create(colorSpaceManager.ColorSpace.SRGB);
```

```TypeScript
import { colorSpaceManager, sendableColorSpaceManager } from '@kit.ArkGraphics2D';
let colorSpace: sendableColorSpaceManager.ColorSpaceManager;
// Define the color space criterion primary colors parameter.
let primaries: colorSpaceManager.ColorSpacePrimaries = {
  redX: 0.1,
  redY: 0.1,
  greenX: 0.2,
  greenY: 0.2,
  blueX: 0.3,
  blueY: 0.3,
  whitePointX: 0.4,
  whitePointY: 0.4
};
// Define the color space gamma value.
let gamma: number = 2.2;
// Create a custom color space management instance that is sendable.
colorSpace = sendableColorSpaceManager.create(primaries, gamma);
```


## create

```TypeScript
function create(primaries: colorSpaceManager.ColorSpacePrimaries, gamma: number): ColorSpaceManager
```

Creates a custom color space object that is sendable.

**Since:** 12

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| primaries | [colorSpaceManager.ColorSpacePrimaries](arkts-arkgraphics2d-colorspacemanager-colorspaceprimaries-i.md) | Yes | Primaries of the color space. |
| gamma | number | Yes | Gamma value of the color space, which is a floating point number greater than 0. |

**Return value:**

| Type | Description |
| --- | --- |
| [ColorSpaceManager](arkts-arkgraphics2d-sendablecolorspacemanager-colorspacemanager-i.md) | Sendable color space object created. <br>The color space type is **CUSTOM**, which is one of the enumerated values of [colorSpaceManager.ColorSpace](arkts-arkgraphics2d-colorspacemanager-colorspace-e.md). <br>This instance inherits from **ISendable** and can be passed by reference between concurrent ArkTS instances (including the main thread and the worker threads of TaskPool or Worker). For details, see [Using Sendable Objects](../../../arkts-utils/sendable-guide.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1.Incorrect parameter type. 2.Parameter verification failed. |
| [18600001](../errorcode-colorspace-manager.md#18600001-abnormal-parameter-value) | The parameter value is abnormal. |

**Examples**

See [create](#create)
