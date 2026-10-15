# @ohos.arkui.inspector(Layout Callback)

Provides APIs for registering the component layout and drawing completion callbacks. By registering callbacks, you can receive notifications in a timely manner after component layout or drawing is complete. It is suitable for scenarios where custom logic needs to be executed after component layout or drawing is complete, helping you precisely control the component rendering timing.

**Since:** 10

<!--Device-unnamed-declare namespace inspector--><!--Device-unnamed-declare namespace inspector-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { inspector } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createComponentObserver](arkts-arkui-inspector-createcomponentobserver-f.md#createcomponentobserver) | Binds to the specified component and returns the corresponding observation handle. |

### Interfaces

| Name | Description |
| --- | --- |
| [ComponentObserver](arkts-arkui-inspector-componentobserver-i.md) | Defines the handle for component layout and drawing completion callbacks. You can call the following APIs through this handle: |
