# @ohos.bundle.bundleMonitor(bundleMonitor Module)

The module provides APIs for listening for bundle installation, uninstall, and updates.

@namespace bundleMonitor

**Since:** 9

<!--Device-unnamed-declare namespace bundleMonitor--><!--Device-unnamed-declare namespace bundleMonitor-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { bundleMonitor } from '@kit.AbilityKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [off](arkts-ability-bundlemonitor-off-f-sys.md) | Unsubscribes from bundle installation, uninstall, and update events. This API uses an asynchronous callback to return the result. |
| [on](arkts-ability-bundlemonitor-on-f-sys.md) | Subscribes to bundle installation, uninstall, and update events. This API uses an asynchronous callback to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [BundleChangedInfo](arkts-ability-bundlemonitor-bundlechangedinfo-i-sys.md) | Application Change Information. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [BundleChangedEvent](arkts-ability-bundlemonitor-bundlechangedevent-t-sys.md) | Enumerates the types of events to listen for. |
<!--DelEnd-->
