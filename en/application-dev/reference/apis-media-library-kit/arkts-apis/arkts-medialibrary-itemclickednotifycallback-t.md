# ItemClickedNotifyCallback

```TypeScript
export type ItemClickedNotifyCallback = (itemInfo: ItemInfo, clickType: ClickType) => void
```

Callback to be invoked when an item in a **PhotoPickerComponent** is clicked.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| itemInfo | [ItemInfo](arkts-medialibrary-file-photopickercomponent-iteminfo-c.md) | Yes | Type of the clicked item, which can be a thumbnail item or a camera item. |
| clickType | [ClickType](arkts-medialibrary-file-photopickercomponent-clicktype-e.md) | Yes | Enumerates the click operation types. |
