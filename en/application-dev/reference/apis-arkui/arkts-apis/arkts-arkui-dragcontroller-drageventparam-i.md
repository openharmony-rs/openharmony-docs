# DragEventParam

```TypeScript
interface DragEventParam
```

Callback used to return the result.

**Since:** 12

<!--Device-dragController-interface DragEventParam--><!--Device-dragController-interface DragEventParam-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## event

```TypeScript
event: DragEvent
```

Drag event information that includes only the drag result.

**Type:** [DragEvent](../arkts-components/arkts-arkui-common-comp-dragevent-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DragEventParam-event: DragEvent--><!--Device-DragEventParam-event: DragEvent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## extraParams

```TypeScript
extraParams: string
```

Additional information about the drag event.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DragEventParam-extraParams: string--><!--Device-DragEventParam-extraParams: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
