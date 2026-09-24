# PathShape

```TypeScript
export declare class PathShape extends CommonShapeMethod<PathShape>
```

Represents a path used in the **clipShape** and **maskShape** APIs.

This API inherits from [CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md).

**Inheritance/Implementation:** PathShape extends CommonShapeMethod<PathShape>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## commands

```TypeScript
commands(commands: string): PathShape
```

Sets the path drawing commands.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| commands | string | Yes | Path drawing commands. |

**Return value:**

| Type | Description |
| --- | --- |
| [PathShape](arkts-arkui-arkui-shape-pathshape-c.md) | **PathShape** object. |

## constructor

```TypeScript
constructor(options?: PathShapeOptions)
```

A constructor used to create a **PathShape** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PathShapeOptions](arkts-arkui-arkui-shape-pathshapeoptions-i.md) | No | Path parameters. |
