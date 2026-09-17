# ItemsDeletedCallback

```TypeScript
export type ItemsDeletedCallback = (baseItemInfos: Array<BaseItemInfo>) => void
```

Called when the selected items are deleted.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| baseItemInfos | Array&lt;[BaseItemInfo](arkts-medialibrary-file-photopickercomponent-baseiteminfo-c.md)&gt; | Yes | Basic information about the selected items. |
