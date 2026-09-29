# PathShapeOptions

```TypeScript
interface PathShapeOptions
```

Represents the parameter of the constructor used to create a **PathShape** object.

**Since:** 12

<!--Device-unnamed-interface PathShapeOptions--><!--Device-unnamed-interface PathShapeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## commands

```TypeScript
commands?: string
```

Commands for drawing the path. The default value is an empty string, and no path is drawn when this parameter is not set.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-PathShapeOptions-commands?: string--><!--Device-PathShapeOptions-commands?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
