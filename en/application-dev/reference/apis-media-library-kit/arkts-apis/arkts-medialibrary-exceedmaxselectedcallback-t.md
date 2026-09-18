# ExceedMaxSelectedCallback

```TypeScript
export type ExceedMaxSelectedCallback = (exceedMaxCountType: MaxCountType) => void
```

Called when items are selected after the maximum count has been reached.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| exceedMaxCountType | [MaxCountType](arkts-medialibrary-file-photopickercomponent-maxcounttype-e.md) | Yes | Type of the maximum count that has been reached. It can be the maximum count of selected images, maximum count of selected videos, or maximum count of selected images and videos. |
