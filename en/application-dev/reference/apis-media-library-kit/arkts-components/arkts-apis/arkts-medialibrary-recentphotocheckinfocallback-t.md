# RecentPhotoCheckInfoCallback

```TypeScript
export type RecentPhotoCheckInfoCallback = (recentPhotoExists: boolean, info: RecentPhotoInfo) => void
```

Called to return whether the recent image or video exists and the information about it.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| recentPhotoExists | boolean | Yes | Whether the recent image or video exists. **true** if it exists, **false** otherwise. The default value is **true**. |
| info | [RecentPhotoInfo](arkts-medialibrary-file-recentphotocomponent-recentphotoinfo-c.md) | Yes | Information about the recent image or video. |
