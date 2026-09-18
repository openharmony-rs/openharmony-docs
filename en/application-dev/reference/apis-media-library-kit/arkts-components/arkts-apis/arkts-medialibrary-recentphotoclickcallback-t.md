# RecentPhotoClickCallback

```TypeScript
export type RecentPhotoClickCallback = (recentPhotoInfo: BaseItemInfo) => boolean
```

Called when the recent image or video is selected. No special processing is performed on the return value.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| recentPhotoInfo | [BaseItemInfo](arkts-medialibrary-file-photopickercomponent-baseiteminfo-c.md) | Yes | Information about the recent image or video. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Processing result of the recent image or video. The value **true** means that the processing is complete. |
