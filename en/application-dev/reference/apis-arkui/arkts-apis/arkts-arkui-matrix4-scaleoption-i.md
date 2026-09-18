# ScaleOption

Describes the scale parameters.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## centerX

```TypeScript
centerX?: number
```

X-coordinate of the center point.

Unit: px

Default value: X-coordinate of the component center

Value range: (-∞, +∞)

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## centerY

```TypeScript
centerY?: number
```

Y-coordinate of the center point.

Unit: px

Default value: Y-coordinate of the component center

Value range: (-∞, +∞)

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: number
```

Scaling multiple along the x-axis. x &gt; 1: The image is scaled up along the x-axis.

0 &lt; x &lt; 1: The image is scaled down along the x-axis.

x &lt; 0: The image is scaled in the reverse direction along the x-axis.

Default value: **1**

Value range: (-∞, +∞)

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: number
```

Scaling multiple along the y-axis. y &gt; 1: The image is scaled up along the y-axis.

0 &lt; y &lt; 1: The image is scaled down along the y-axis.

y &lt; 0: The image is scaled in the reverse direction along the y-axis.

Default value: **1**

Value range: (-∞, +∞)

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## z

```TypeScript
z?: number
```

Scaling multiple along the z-axis. z &gt; 1: The image is scaled up along the z-axis.

0 &lt; z &lt; 1: The image is scaled down along the z-axis.

z &lt; 0: The image is scaled in the reverse direction along the z-axis.

Default value: **1**

Value range: (-∞, +∞)

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
