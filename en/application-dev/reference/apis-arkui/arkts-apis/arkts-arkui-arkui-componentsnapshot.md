# @ohos.arkui.componentSnapshot(ComponentSnapshot)

The **componentSnapshot** module provides APIs for obtaining component snapshots, including snapshots of components that have been loaded and snapshots of components that have not been loaded yet. Snapshots are strictly limited to the component's layout bounds. Content drawn outside the area of the owning component or the parent component is not visible in the snapshots. In addition, sibling components stacked in the component's area are not displayed in the snapshot.

Transformation attributes such as scaling, translation, and rotation only apply to the child components of the target component. Applying these transformation attributes directly to the target component itself has no effect; the snapshot will still display the component as it appears before any transformations are applied.

For typical use cases (for example, long screenshots) and best practices of component snapshots, see [Using Component Snapshot (ComponentSnapshot)](../../../ui/arkts-uicontext-component-snapshot.md).

> **NOTE:** 
> 
> - In scenarios where XComponent is used to, for example, display video or camera streams,obtain images through [createPixelMapFromSurface](../../apis-image-kit/arkts-apis/arkts-image-image-createpixelmapfromsurface-f.md),instead of through an API in this module.
> 
> - If the content of a component does not fill the entire area allocated for it, any remaining space in the snapshot will be rendered as transparent pixels. In addition, if the component uses image effects or other effect-related attributes, the resulting snapshot may not be as expected. To address these potential issues, check whether the component's transparent content area needs to be filled, or use the window screenshot API [snapshot](arkts-arkui-window-window-i.md#snapshot) instead.
> 
> - You can preview how this component looks on a real device, but not in DevEco Studio Previewer.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { componentSnapshot } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createFromBuilder](arkts-arkui-componentsnapshot-createfrombuilder-f.md#createfrombuilder) | Renders a custom component in the application background and outputs its snapshot. This API uses an asynchronous callback to return the result. The coordinates and size of the offscreen component's drawing area can be obtained through the callback. |
| [createFromBuilder](arkts-arkui-componentsnapshot-createfrombuilder-f.md#createfrombuilder-1) | Renders a custom component in the application background and outputs its snapshot. This API uses a promise to return the result. The coordinates and size of the offscreen component's drawing area can be obtained through the callback. |
| [get](arkts-arkui-componentsnapshot-get-f.md#get) | Obtains the snapshot of a component that has been loaded based on the provided component ID. This API uses an asynchronous callback to return the result. |
| [get](arkts-arkui-componentsnapshot-get-f.md#get-1) | Obtains the snapshot of a component that has been loaded based on the provided component ID. This API uses a promise to return the result. |
| [getSync](arkts-arkui-componentsnapshot-getsync-f.md) | Obtains the snapshot of a component that has been loaded based on the provided component ID. This API synchronously waits for the snapshot to complete and returns a [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) object. |

### Interfaces

| Name | Description |
| --- | --- |
| [ColorModeOptions](arkts-arkui-componentsnapshot-colormodeoptions-i.md) | Defines the color space used for the snapshot. |
| [DynamicRangeModeOptions](arkts-arkui-componentsnapshot-dynamicrangemodeoptions-i.md) | Defines the dynamic range mode used for the snapshot. |
| [LocalizedSnapshotRegion](arkts-arkui-componentsnapshot-localizedsnapshotregion-i.md) | Defines the rectangular region for capturing the component snapshot, with coordinates adjusted based on the layout direction (LTR or RTL). |
| [SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md) | Defines the extra options for snapshot taking. |
| [SnapshotRegion](arkts-arkui-componentsnapshot-snapshotregion-i.md) | Defines the rectangular region for capturing the component snapshot. |
| [SnapshotSizeLimitation](arkts-arkui-componentsnapshot-snapshotsizelimitation-i.md) | Defines the size limit of a component screenshot. |

### Types

| Name | Description |
| --- | --- |
| [SnapshotRegionType](arkts-arkui-componentsnapshot-snapshotregiontype-t.md) | Defines the snapshot region rect type. |
