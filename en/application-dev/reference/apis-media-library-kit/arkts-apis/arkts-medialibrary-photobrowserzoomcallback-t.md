# PhotoBrowserZoomCallback

```TypeScript
export type PhotoBrowserZoomCallback = (scale: number) => void
```

Called when the user zooms in or out on a full image after entering the full image view through **PhotoPickerComponent**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-unnamed-export type PhotoBrowserZoomCallback = (scale: double) => void--><!--Device-unnamed-export type PhotoBrowserZoomCallback = (scale: double) => void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | number | Yes | Scale of the image compared with the original image. |
