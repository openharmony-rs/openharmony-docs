# end (System API)

## Modules to Import

```TypeScript
import { performanceMonitor } from '@kit.ArkUI';
```

## end

```TypeScript
function end(scene: string): void
```

Marks the end of a user scene. Call this API when the scene ends.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scene | string | Yes | User scene ID, which must be strictly consistent with that in **begin**; otherwise, the monitoring will be invalid. |

**Examples**

End point of the user scene where the user taps an icon to launch an application.

```TypeScript
performanceMonitor.end("LAUNCHER_APP_LAUNCH_FROM_ICON");
```
