# DragSpringLoadingConfiguration

Defines the configuration parameters for drag hover detection. The default settings typically suffice. These settings can be customized through [onDragSpringLoading](../arkts-components/arkts-arkui-commonmethod-c.md#ondragspringloading) binding or dynamically updated during BEGIN state using [updateConfiguration](arkts-arkui-dragcontroller-springloadingcontext-c.md#updateconfiguration).

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## stillTimeLimit

```TypeScript
stillTimeLimit?: number
```

Time (in ms) required to remain stationary to enter the BEGIN state of hover detection. Value range: integer in the [0, 2&lt;sup&gt;31&lt;/sup&gt;-1] range. Floating-point number inputs will be truncated to integers. Invalid values (negative numbers, **null**, **undefined**, **NaN**) are treated as the default value **500**.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## updateInterval

```TypeScript
updateInterval?: number
```

Time interval (in ms) at which update notifications are sent after hover detection enters the UPDATE state. Value range: integer in the [0, 2&lt;sup&gt;31&lt;/sup&gt;-1] range. Floating-point number inputs will be truncated to integers. Invalid values (negative numbers, **null**, **undefined**, **NaN**) are treated as the default value **100**.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## updateNotifyCount

```TypeScript
updateNotifyCount?: number
```

Maximum number of update notifications after hover detection enters the UPDATE state. Value range: integer in the [0, 2&lt;sup&gt;31&lt;/sup&gt;-1] range. Floating-point number inputs will be truncated to integers. Invalid values (negative numbers, **null**, **undefined**, **NaN**) are treated as the default value **3**.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## updateToFinishInterval

```TypeScript
updateToFinishInterval?: number
```

Maximum waiting time (in ms) from the UPDATE state to the END state. Value range: integer in the [0, 2&lt;sup&gt;31&lt;/sup&gt;-1] range. Floating-point number inputs will be truncated to integers. Invalid values (negative numbers, **null**, **undefined**, **NaN**) are treated as the default value **100**.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
