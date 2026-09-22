# begin (System API)

## Modules to Import

```TypeScript
import { performanceMonitor } from '@kit.ArkUI';
```

## begin

```TypeScript
function begin(scene: string, startInputType: ActionType, note?: string): void
```

Marks the start of a user scene. Call this API when the scene begins.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scene | string | Yes | User scene ID. The string length is unlimited, but it is recommended that you keep it within 255 characters. The format is recommended to use uppercase letters connected by underscores, for example, **LAUNCHER_APP_LAUNCH_FROM_ICON**. |
| startInputType | [ActionType](arkts-arkui-performancemonitor-actiontype-e-sys.md) | Yes | Trigger mode of the user scene. |
| note | string | No | Remarks for the user scene. The string length is unlimited, but it is recommended that you keep it within 255 characters. This field is optional. If provided, the performance metrics report will include the remark information; if not provided, there is no impact. |

**Examples**

Start point of the user scene where the user taps an icon to launch an application, triggered by a release event (LAST_UP).

```TypeScript
performanceMonitor.begin("LAUNCHER_APP_LAUNCH_FROM_ICON", performanceMonitor.ActionType.LAST_UP, "APP_START_BEGIN");
```
