# ColorModeOptions

```TypeScript
interface ColorModeOptions
```

Defines the color space used for the snapshot.

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { componentSnapshot } from '@kit.ArkUI';
```

## colorSpace

```TypeScript
colorSpace?: colorSpaceManager.ColorSpace
```

Color space used for the snapshot.

If the target component's color space is known, specify it through **colorSpace** and set **isAuto** to **false** to achieve optimal snapshot quality.

The value can be **DISPLAY_P3**, **SRGB**, or **DISPLAY_BT2020_SRGB** in [colorSpaceManager.ColorSpace](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspace-e.md).

Default value: **SRGB**

If the value is **undefined**, **null**, or not set, the default value is used. If an abnormal value is used, snapshot capture fails and the error code 160003 is returned.

**Type:** [colorSpaceManager.ColorSpace](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspace-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isAuto

```TypeScript
isAuto?: boolean
```

Whether the system automatically determines the color space to be used.

The value **true** means to allow the system to automatically determine the color space to be used, and **false** means to manually set the color space through **colorSpace**. If an invalid value is used, the default value **false** is used.

Default value: **false**

For offscreen snapshots, this parameter can only be set to **false**. Otherwise, the error code 160004 will be returned.

If `isAuto` is set to **true**, you are advised to set `waitUntilRenderFinished` in [SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md) to **true** to ensure that the system can properly detect the used color space.

If the color space used by the component is uncertain, you are advised to set **isAuto** to **true** so that the system can automatically determine the color space to be used.

When **isAuto** is set to true, the value of **colorSpace** is ignored. In this case, if the target component contains child components in different color spaces, the color space with the highest priority is used for the snapshot. The priority order of the color space is as follows: **DISPLAY_BT2020_SRGB**  
> **DISPLAY_P3**
> **SRGB**.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
