# SpringLoadingContext

Defines callback context information passed to applications during hover detection. It enables access to drag states, dynamic UI effect updates, and drag data for operation handling decisions.

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## abort

```TypeScript
abort(): void
```

Terminates subsequent hover detection. This API does not trigger CANCEL state notifications, and the application needs to perform state cleanup when executing this API.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## updateConfiguration

```TypeScript
updateConfiguration(config: DragSpringLoadingConfiguration): void
```

Updates the hover detection configuration. This API is effective only when the hover detection state is BEGIN. Applications typically set the hover detection configuration when binding [onDragSpringLoading](../arkts-components/arkts-arkui-commonmethod-c.md#ondragspringloading) or use the default configuration. This API does not modify the original configuration set during binding, but updates dynamic configuration information for subsequent hover detection. Use this API with caution, as different drag data types may require different UX timing.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [DragSpringLoadingConfiguration](arkts-arkui-dragcontroller-dragspringloadingconfiguration-i.md) | Yes | New configuration for hover detection. |

## currentConfig

```TypeScript
currentConfig?: DragSpringLoadingConfiguration
```

Configuration information in the current callback. Omitted in CANCEL state; uses the [DragSpringLoadingConfiguration](arkts-arkui-dragcontroller-dragspringloadingconfiguration-i.md) default value when **undefined**.

**Type:** [DragSpringLoadingConfiguration](arkts-arkui-dragcontroller-dragspringloadingconfiguration-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## currentNotifySequence

```TypeScript
currentNotifySequence: number
```

Callback notification sequence number in the current hover detection cycle. The value is zero-based.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dragInfos

```TypeScript
dragInfos?: SpringLoadingDragInfos
```

Drag information. Omitted in CANCEL state; uses the [SpringLoadingDragInfos](arkts-arkui-dragcontroller-springloadingdraginfos-i.md) default value when **undefined**.

**Type:** [SpringLoadingDragInfos](arkts-arkui-dragcontroller-springloadingdraginfos-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state: DragSpringLoadingState
```

Current state of hover detection.

**Type:** [DragSpringLoadingState](arkts-arkui-dragcontroller-dragspringloadingstate-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
