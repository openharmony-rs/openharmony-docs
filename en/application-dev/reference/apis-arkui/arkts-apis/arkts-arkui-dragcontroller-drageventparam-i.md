# DragEventParam

Callback used to return the result.

**Since:** 12

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

**Type:** [DragEvent](../arkts-components/arkts-arkui-dragevent-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## extraParams

```TypeScript
extraParams: string
```

Additional information about the drag action. Not supported currently.

The default value is null.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
