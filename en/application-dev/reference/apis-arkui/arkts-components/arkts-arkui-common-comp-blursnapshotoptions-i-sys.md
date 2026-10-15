# BlurSnapshotOptions (System API)

```TypeScript
declare interface BlurSnapshotOptions
```

Defines the options for blur snapshot optimization. Setting this object enables blur optimization.

**Since:** 26.0.0

<!--Device-unnamed-declare interface BlurSnapshotOptions--><!--Device-unnamed-declare interface BlurSnapshotOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## enableFreeze

```TypeScript
enableFreeze?: boolean
```

Sets whether to enable freeze optimization for the blur snapshot. When enabled, freeze optimization is applied during blur snapshot to reduce rendering overhead. When not set or set to false, freeze optimization is disabled and the conventional rendering method is used.

After the sheet is pulled up, this parameter value can be switched dynamically.

Default value: false

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BlurSnapshotOptions-enableFreeze?: boolean--><!--Device-BlurSnapshotOptions-enableFreeze?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
