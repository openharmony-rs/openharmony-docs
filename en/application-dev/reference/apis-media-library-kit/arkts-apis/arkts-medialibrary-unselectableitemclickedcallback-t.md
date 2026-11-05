# UnselectableItemClickedCallback

```TypeScript
export type UnselectableItemClickedCallback = (unselectableItemInfo: UnselectableItemInfo) => void
```

Describes the callback invoked when an unselectable image is tapped on the picker grid or large image preview screen.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-unnamed-export type UnselectableItemClickedCallback = (unselectableItemInfo: UnselectableItemInfo) => void--><!--Device-unnamed-export type UnselectableItemClickedCallback = (unselectableItemInfo: UnselectableItemInfo) => void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| unselectableItemInfo | [UnselectableItemInfo](arkts-medialibrary-file-photopickercomponent-unselectableiteminfo-c.md) | Yes | Details about the image that is tapped but cannot be selected. |
