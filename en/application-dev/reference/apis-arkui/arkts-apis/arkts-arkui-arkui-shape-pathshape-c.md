# PathShape

```TypeScript
export declare class PathShape extends CommonShapeMethod<PathShape>
```

Represents a path shape used for the **clipShape** and **maskShape** APIs. It inherits from [CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md).

**Inheritance/Implementation:** PathShape extends CommonShapeMethod<PathShape>

**Since:** 12

<!--Device-unnamed-export declare class PathShape extends CommonShapeMethod<PathShape>--><!--Device-unnamed-export declare class PathShape extends CommonShapeMethod<PathShape>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## commands

```TypeScript
commands(commands: string): PathShape
```

Sets the path drawing commands, used to define the drawing path of **PathShape**. The commands follow the SVG path data format. For details about the supported drawing commands, see [commands](../arkts-components/arkts-arkui-path-comp-attribute.md#commands).

> **NOTE:** 
> 
> - The commands must be set (either through the **PathShapeOptions.commands** constructor parameter or through this API) for **PathShape** to produce a visible clipping or mask effect in the **clipShape** or **maskShape**API.
> 
> - The **PathShape** without commands set is an empty path and produces no clipping or mask effect.
> 
> - This API sets the same attribute as the **PathShapeOptions.commands** constructor. The setting called later overrides the earlier one.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-PathShape-commands(commands: string): PathShape--><!--Device-PathShape-commands(commands: string): PathShape-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| commands | string | Yes | Path drawing commands. For the format requirements, see the drawing commands supported by [commands](../arkts-components/arkts-arkui-path-comp-attribute.md#commands). If invalid commands are passed in, no visible path is generated. |

**Return value:**

| Type | Description |
| --- | --- |
| [PathShape](arkts-arkui-arkui-shape-pathshape-c.md) | **PathShape** object with path drawing commands configured, which can be used for chained calls to further configure the path shape. |

## constructor

```TypeScript
constructor(options?: PathShapeOptions)
```

A constructor used to create a **PathShape** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-PathShape-constructor(options?: PathShapeOptions)--><!--Device-PathShape-constructor(options?: PathShapeOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PathShapeOptions](arkts-arkui-arkui-shape-pathshapeoptions-i.md) | No | Path parameters. If not passed in, the path drawing commands default to an empty string, and no path is drawn. |
