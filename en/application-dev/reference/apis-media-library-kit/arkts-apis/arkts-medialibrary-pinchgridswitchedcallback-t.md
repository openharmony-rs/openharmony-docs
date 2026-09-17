# PinchGridSwitchedCallback

```TypeScript
export type PinchGridSwitchedCallback = (gridLevel: photoAccessHelper.GridLevel) => void
```

Callback to be invoked when a user pinches a grid component.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| gridLevel | [photoAccessHelper.GridLevel](arkts-medialibrary-photoaccesshelper-gridlevel-e.md) | Yes | Number of columns in the grid. |
