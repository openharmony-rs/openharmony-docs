# PhotoBrowserZoomCallback

```TypeScript
export type PhotoBrowserZoomCallback = (scale: number) => void
```

Callback to be invoked when the large image is zoomed in or out after the large image is entered through the **PhotoPickerComponent**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | number | Yes | Scale of the image compared with the original image. |
