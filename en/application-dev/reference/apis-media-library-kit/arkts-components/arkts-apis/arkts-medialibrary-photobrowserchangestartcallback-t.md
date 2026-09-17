# PhotoBrowserChangeStartCallback

```TypeScript
export type PhotoBrowserChangeStartCallback = (targetPhotoInfo: BaseItemInfo) => void
```

Callback to be invoked when a grid view switches to the photo browser page or the photo browser page is switched.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetPhotoInfo | [BaseItemInfo](arkts-medialibrary-file-photopickercomponent-baseiteminfo-c.md) | Yes | Basic information about the selected items. |
