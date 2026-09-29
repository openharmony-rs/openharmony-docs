# FoldCreaseRegion

```TypeScript
interface FoldCreaseRegion
```

Describes the crease region of a foldable device.

**Since:** 10

<!--Device-display-interface FoldCreaseRegion--><!--Device-display-interface FoldCreaseRegion-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## creaseRects

```TypeScript
readonly creaseRects: Array<Rect>
```

Crease region.

**Type:** Array&lt;[Rect](arkts-arkui-display-rect-i.md)&gt;

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-FoldCreaseRegion-readonly creaseRects: Array<Rect>--><!--Device-FoldCreaseRegion-readonly creaseRects: Array<Rect>-End-->

**System capability:** SystemCapability.Window.SessionManager

## displayId

```TypeScript
readonly displayId: number
```

ID of the display where the crease is located.

**Type:** number

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-FoldCreaseRegion-readonly displayId: long--><!--Device-FoldCreaseRegion-readonly displayId: long-End-->

**System capability:** SystemCapability.Window.SessionManager
