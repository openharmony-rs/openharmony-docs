# @ohos.arkui.performanceMonitor

The **performanceMonitor** module provides APIs for monitoring performance metrics related to user scenes. By calling the **begin** and **end** APIs at the start and end of a scene respectively, you can obtain relevant performance metrics such as response latency, completion latency, and frame drops.

> **NOTE:** 
> 
> The APIs of this module are supported since API version 10. Updates will be marked with a superscript to indicate
> their
> 
> The APIs provided by this module are system APIs.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { performanceMonitor } from '@kit.ArkUI';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [begin](arkts-arkui-performancemonitor-begin-f-sys.md) | Marks the start of a user scene. Call this API when the scene begins. |
| [end](arkts-arkui-performancemonitor-end-f-sys.md) | Marks the end of a user scene. Call this API when the scene ends. |
| [recordInputEventTime](arkts-arkui-performancemonitor-recordinputeventtime-f-sys.md) | Records the trigger event type and time before the start of the animation scene. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ActionType](arkts-arkui-performancemonitor-actiontype-e-sys.md) | Enumerates the trigger modes for user scenes (typically scenes involving animations). |
| [SourceType](arkts-arkui-performancemonitor-sourcetype-e-sys.md) | Enumerates the trigger source types of user scenes. |
<!--DelEnd-->
